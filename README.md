# Final Task: Designing a Data Warehouse and Implementing Stored Procedures

## Klien ID/X Partners

Salah satu klien dari perusahaan ID/X Partners yang bergerak di industri perbankan memiliki kebutuhan untuk membangun sebuah Data Warehouse dari beberapa sumber data yang berbeda yang tersimpan di dalam sistem mereka. Beberapa sumber data tersebut antara lain:
- **transaction_excel** (file Excel)
- **transaction_csv** (file CSV)
- **transaction_db** (Database SQL Server)
- **account** (Database SQL Server)
- **customer** (Database SQL Server)
- **branch** (Database SQL Server)
- **city** (Database SQL Server)
- **state** (Database SQL Server)

Permasalahan yang mereka hadapi saat ini adalah kesulitan untuk mengekstrak data dari berbagai sumber (Excel, CSV, database) secara bersamaan, sehingga pelaporan dan analisis data mereka selalu mengalami keterlambatan.

## Tugas Anda sebagai Data Engineer

Sebagai seorang Data Engineer, ada beberapa tugas yang perlu Anda lakukan untuk mengoptimalkan proses ETL di perusahaan tersebut:

### 1. Membangun Data Warehouse
- Membangun sebuah database baru yang akan menjadi Data Warehouse bernama **DWH**.
- Buatlah tiga tabel dimensi: **DimAccount**, **DimCustomer**, **DimBranch**.
- Buat satu tabel fakta: **FactTransaction**.
- Pastikan untuk memberikan **primary key** dan **foreign key** pada setiap tabel.

### 2. Membuat Job ETL di Talend
- Buat job ETL di aplikasi Talend untuk memindahkan data dari sumber ke seluruh tabel Dimensi.
- Untuk tabel **DimCustomer**, format kolom yang disimpan adalah:
  - **CustomerID**
  - **CustomerName**
  - **Address**
  - **CityName**
  - **StateName**
  - **Age**
  - **Gender**
  - **Email**

  Semua data dari kolom tersebut diubah menjadi huruf kapital, kecuali untuk kolom **CustomerID**, **Age**, dan **Email**. Pastikan untuk mengikuti kaidah PascalCase dalam penamaan kolom (contoh: account_id = AccountID).

### 3. Menggabungkan Data Transaksi
- Buat job ETL untuk menggabungkan data transaksi (**transaction_excel**, **transaction_csv**, **transaction_db**) menjadi satu di tabel **FactTransaction**.
- Pastikan tidak ada baris yang duplikat di dalam tabel **FactTransaction**.

### 4. Membuat Stored Procedure
Buat dua Stored Procedure (SP) dengan parameter untuk membantu mendapatkan ringkasan data dengan cepat:

#### a. DailyTransaction
- Untuk menghitung banyaknya transaksi beserta total nominalnya setiap harinya.
- Kolom yang ditampilkan adalah:
  - **Date**
  - **TotalTransactions**
  - **TotalAmount**

  Kolom **TotalAmount** didapat dengan menjumlahkan **Amount** setiap harinya.
- Buat dua parameter, yaitu **start_date** dan **end_date**, sehingga ketika menjalankan SP ini dengan memasukkan parameter tersebut, maka akan menampilkan data sesuai rentang tanggal yang kita masukkan.

#### b. BalancePerCustomer
- Untuk mengetahui sisa balance per customer.
- Kolom yang ditampilkan adalah:
  - **CustomerName**
  - **AccountType**
  - **Balance**
  - **CurrentBalance**

  Kolom **CurrentBalance** didapat dari kolom **Balance** di tabel **account** dikurang total amount yang ditransaksikan di tabel **transaction** untuk setiap **account_id**. Untuk setiap **transaction_type = Deposit**, maka balance akan bertambah, selain itu, maka Balance akan berkurang.
- Buat parameter bernama **name** sehingga ketika menjalankan SP ini dengan memasukkan nama salah satu customer tersebut, maka akan menampilkan data sesuai dengan yang kita input.
- Pastikan untuk memfilter account yang berstatus active.

Dengan menyelesaikan tugas-tugas ini, Anda akan membantu klien dalam mengoptimalkan proses ETL dan memperoleh ringkasan data yang dibutuhkan dengan cepat dan efisien.

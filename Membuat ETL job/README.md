## Proses ETL dengan Talend untuk Tabel Dimensi Data Warehouse

### 1. Konfigurasi Aplikasi Talend
Pada gambar pertama, Anda dapat melihat antarmuka aplikasi Talend, yang mencakup beberapa pekerjaan atau komponen seperti:
- **Job DimAccount**
- **Job DimBranch**
- **Job DimCustomer**
- **Job FactTransaction**

Komponen-komponen ini akan digunakan untuk melakukan berbagai tugas dalam proses ETL.

### 2. Koneksi ke Sumber Data
Gambar kedua menunjukkan komponen **Job DimBranch**, yang terhubung ke sumber data yang diwakili oleh ikon "branch" di sebelah kiri. Detail yang ditampilkan menunjukkan bahwa ada 5 baris yang diproses dengan kecepatan 7,23 baris/detik.

### 3. Penyiapan Tabel Dimensi
Gambar ketiga menggambarkan komponen **Job DimCustomer**, yang bertanggung jawab untuk menyiapkan tabel dimensi **DimCustomer**. Ini melibatkan transformasi dan pemuatan data dari berbagai sumber, seperti:
- **city**
- **customer**
- **state**

Aliran data dan detail pemrosesan, seperti jumlah baris dan kecepatan pemrosesan, ditampilkan.

### 4. Penyiapan Tabel Fakta
Gambar keempat mewakili komponen **Job FactTransaction**, yang bertanggung jawab untuk menyiapkan tabel **FactTransaction**. Ini melibatkan penggabungan data dari berbagai sumber, termasuk:
- **transaction_db**
- **Transaction.csv**
- **Transaction_Excel**

Data ditransformasi menggunakan berbagai operasi seperti penggabungan, penyatuan, dan penghapusan duplikat, sebelum dimuat ke dalam tabel **FactTransaction**.

---

Proses keseluruhan melibatkan:
1. **Konfigurasi aplikasi Talend**
2. **Koneksi ke sumber data** (dalam kasus ini, Microsoft SQL Server)
3. **Ekstraksi data** dari sumber
4. **Transformasi data** sesuai kebutuhan
5. **Pemuatan data** yang telah ditransformasi ke dalam tabel dimensi dan fakta yang sesuai di data warehouse.


![alt text](<1.png>) ![alt text](<2.png>) ![alt text](<3.png>) ![alt text](<4.png>)

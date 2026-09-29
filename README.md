# Analisis Data Supermarket Indonesia

## Penjelasan Pembersihan Data

Pada tahap ini dilakukan proses pembersihan data untuk memastikan data yang digunakan dalam analisis memiliki format yang konsisten dan tidak menyebabkan kesalahan dalam perhitungan.

### 1. Menangani Data Duplikat

Data duplikat ditangani menggunakan fitur **Remove duplicates** pada Google Sheets. Baris data yang identik dihapus agar data yang sama tidak terhitung lebih dari satu kali dalam proses analisis.

### 2. Membersihkan Kolom Tanggal Pengiriman

Kolom `tanggal_pengiriman` dibersihkan menggunakan kolom baru `clean_tanggal_pengiriman`.

Apabila terdapat nilai kosong pada `tanggal_pengiriman`, maka nilainya diisi menggunakan `tanggal_pemesanan`. Hal ini dilakukan agar tidak terdapat nilai kosong pada tanggal pengiriman dan informasi tanggal transaksi tetap dapat digunakan dalam analisis.

### 3. Membersihkan Kolom Kota

Kolom `kota` dibersihkan menggunakan kolom baru `clean_kota`.

Nilai kota yang tersedia dinormalisasi menggunakan fungsi `TRIM` dan `PROPER` agar penulisan nama kota menjadi lebih konsisten. Apabila terdapat nilai kota yang kosong, maka nilai tersebut dilengkapi berdasarkan informasi `provinsi` menggunakan sheet referensi `reference_province_to_city`.

### 4. Membersihkan Kolom Kode Pos

Kolom `kode_pos` dibersihkan menggunakan kolom baru `clean_kode_pos`.

Apabila terdapat nilai kode pos yang kosong, maka nilai tersebut dilengkapi berdasarkan `provinsi` menggunakan sheet referensi `reference_postal_code`. Nilai kode pos yang sudah tersedia tetap dipertahankan.

### 5. Mempertahankan Kolom Asli

Kolom asli tidak dihapus selama proses pembersihan data. Hasil pembersihan disimpan pada kolom baru dengan awalan `clean_`, seperti:

* `clean_tanggal_pengiriman`
* `clean_kota`
* `clean_kode_pos`

Dengan demikian, data asli tetap tersedia dan hasil pembersihan dapat digunakan untuk proses analisis selanjutnya.

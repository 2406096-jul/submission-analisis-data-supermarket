# Analisis Data Supermarket Indonesia

Submission akhir kelas analisis data dengan studi kasus perusahaan ritel/supermarket di Indonesia.

## Deskripsi

Proyek ini bertujuan untuk melakukan proses pembersihan, analisis, visualisasi, dan analisis prediktif menggunakan dataset transaksi supermarket Indonesia.

Tools yang digunakan dalam proyek ini:

* Google Sheets
* SQL menggunakan fungsi `QUERY()` pada Google Sheets
* Looker Studio
* Orange Data Mining

## Dataset

Dataset yang digunakan merupakan dataset sintetis yang disediakan untuk kebutuhan submission.

Dataset berisi informasi transaksi, pelanggan, produk, lokasi, penjualan, kuantitas, diskon, dan keuntungan.

## Proses Pembersihan Data

### 1. Menghapus Data Duplikat

Data duplikat ditemukan pada dataset dan ditangani menggunakan fitur **Remove duplicates** pada Google Sheets.

Data duplikat dihapus agar setiap transaksi tidak dihitung lebih dari satu kali sehingga hasil analisis penjualan, kuantitas, dan keuntungan tidak terdistorsi.

### 2. Membersihkan Tanggal Pengiriman

Pada kolom `tanggal_pengiriman` ditemukan beberapa nilai kosong.

Untuk menangani masalah tersebut, dibuat kolom baru:

`clean_tanggal_pengiriman`

Nilai yang kosong pada `tanggal_pengiriman` diisi menggunakan nilai dari `tanggal_pemesanan`.

Metode ini digunakan untuk menghindari nilai kosong pada data tanggal pengiriman dan mempertahankan informasi waktu transaksi yang tersedia.

### 3. Membersihkan Data Kota

Pada kolom `kota` terdapat dua masalah, yaitu nilai kosong dan ketidakkonsistenan penulisan, seperti perbedaan penggunaan huruf besar dan kecil.

Untuk menangani masalah tersebut, dibuat kolom:

`clean_kota`

Data kota dinormalisasi menggunakan fungsi `TRIM` dan `PROPER` agar format penulisan menjadi konsisten.

Apabila nilai kota kosong, informasi kota diambil berdasarkan provinsi menggunakan sheet:

`reference_province_to_city`

Dengan demikian, kolom `clean_kota` memiliki format yang lebih konsisten dan tidak memiliki nilai kosong.

### 4. Membersihkan Data Kode Pos

Pada kolom `kode_pos` terdapat beberapa nilai kosong.

Untuk menangani masalah tersebut, dibuat kolom:

`clean_kode_pos`

Apabila kode pos kosong, nilai kode pos diisi berdasarkan provinsi menggunakan sheet:

`reference_postal_code`.

Kode pos yang sudah tersedia tetap dipertahankan.

## Analisis Data

Analisis dilakukan menggunakan Google Sheets dan fungsi `QUERY()`.

Analisis yang dilakukan meliputi:

* Total penjualan tahun 2016.
* Total kuantitas produk tahun 2016.
* Jumlah pemesanan menggunakan metode First Class.
* Lima produk dengan total penjualan tertinggi.
* Jumlah pelanggan berdasarkan kota.
* Rata-rata penjualan berdasarkan kota.
* Jumlah transaksi berdasarkan hari.
* Total penjualan berdasarkan produk dan kota menggunakan pivot table.

## Visualisasi Data

Visualisasi data dibuat menggunakan Looker Studio.

Dashboard pertama menampilkan:

* Tren penjualan tahun 2014–2017.
* Proporsi jumlah pesanan berdasarkan wilayah.
* Proporsi penjualan berdasarkan kategori produk.

Dashboard kedua menampilkan:

* Kota dengan total penjualan tertinggi.
* Metode pengiriman yang paling sering digunakan.
* Bulan dengan total penjualan tertinggi.

## Analisis Prediktif

Analisis prediktif dilakukan menggunakan Orange Data Mining dengan target:

`keuntungan`

Model yang digunakan:

* Linear Regression
* Random Forest Regression

Tahapan analisis meliputi:

1. Import dataset.
2. Pemilihan fitur menggunakan Select Columns.
3. Preprocessing data.
4. Pemisahan/evaluasi data.
5. Pelatihan model regresi.
6. Evaluasi model menggunakan Test & Score.
7. Prediksi menggunakan Predictions.

Hasil evaluasi digunakan untuk mengetahui performa model dalam memperkirakan nilai keuntungan.

## Struktur File

Repository ini berisi hasil pekerjaan submission, antara lain:

* `syntethic_store_indonesia.xlsx` — dataset yang telah dibersihkan dan dianalisis.
* `informasi_penjualan_super_market_indonesia.pdf` — hasil export dashboard Looker Studio.
* `analisis-prediktif-supermarket.ows` — workflow analisis prediktif menggunakan Orange Data Mining.
* `url.txt` — berisi link Google Sheets dan Looker Studio.

## Tools

| Tools               | Kegunaan                                |
| ------------------- | --------------------------------------- |
| Google Sheets       | Cleaning dan analisis data              |
| Google Sheets QUERY | Analisis menggunakan sintaks SQL        |
| Looker Studio       | Visualisasi dan dashboard               |
| Orange Data Mining  | Analisis prediktif dan machine learning |
| GitHub              | Penyimpanan dan dokumentasi proyek      |

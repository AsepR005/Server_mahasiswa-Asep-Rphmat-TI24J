Analisis Proyek REST API Mahasiswa

1. Tujuan Proyek

Proyek ini dikembangkan untuk memberikan pemahaman mengenai cara
membangun REST API menggunakan Node.js, Express, dan MySQL. API ini
menyediakan fitur CRUD (Create, Read, Update, Delete) untuk data
mahasiswa.

2. Struktur Project

    serverkuliah
    │
    ├── controllers
    │   └── mahasiswaController.js
    │
    ├── models
    │   └── db.js
    │
    ├── index.js        (file untuk melakukan testing fetch PUT)
    ├── server.js       (file utama untuk menjalankan server)
    ├── package.json
    └── package-lock.json

Penjelasan:

-   server.js
    File utama untuk menjalankan Express server dan memetakan routing ke
    mahasiswaController.
-   mahasiswaController.js
    Mengandung semua logic REST API: GET, POST, PUT, DELETE.
-   db.js
    Mengelola koneksi MySQL.
-   index.js
    Digunakan untuk testing fetch PUT (mirip Postman manual).
-   package.json
    Mendefinisikan dependencies seperti Express dan MySQL.
-   package-lock.json
    Mengunci versi dependensi yang terinstal untuk memastikan proyek dapat dijalankan
    secara konsisten di berbagai lingkungan, serta membantu mencegah konflik versi
    atau bug akibat perbedaan versi paket.


3. Analisis Alur Kerja Program

a. Koneksi Database (db.js)

Program menggunakan `mysql.createConnection()` untuk menghubungkan
Node.js ke MySQL.
Jika koneksi gagal, sistem menampilkan error di console.

b. Routing dan Controller

Semua endpoint mahasiswa berada dalam `mahasiswaController.js` dan
terhubung melalui:

    app.use('/mahasiswa', mahasiswaController);

c. Endpoint CRUD

Berikut fungsi tiap endpoint:

1.  GET mahasiswa
    Mengambil seluruh data mahasiswa dari database.

2.  GET (/mahasiswa/:nim)
    Mengambil data spesifik berdasarkan NIM.

3.  POST (/mahasiswa)
    Menambah data mahasiswa baru ke database.

4.  PUT (/mahasiswa/:nim)
    Melakukan update data mahasiswa berdasarkan NIM.

5.  DELETE (/mahasiswa/:nim)
    Menghapus data mahasiswa dari database.

d. Pengujian API

Pengujian dilakukan melalui: - Postman (berhasil untuk POST, PUT,
DELETE) - index.js (fungsi fetch PUT)

Jika index.js digunakan, server harus dijalankan terlebih dahulu:

    nodemon server.js

4. Analisis Masalah dan Perbaikan

Masalah yang saya temukan:

1.  fetch error (ECONNREFUSED)
    Penyebab: server belum berjalan sebelum index.js dijalankan.
    Solusi: jalankan server dulu, kemudian jalankan index.js.

2.  Data berhasil di Database tetapi tidak tampil di index.js
    Karena index.js hanya menampilkan hasil respon PUT, bukan
    menampilkan semua data.


5. Kesimpulan

REST API mahasiswa berhasil dibangun dengan menerapkan konsep modular,
controller, dan koneksi database. Semua endpoint CRUD berfungsi baik.
Analisis menunjukkan bahwa arsitektur API sudah benar, dan program siap
dipublikasikan melalui GitHub.


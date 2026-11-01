# DEBUG_LOG — Latihan P10

## G1: Logo navbar tidak tampil

- **Reproduksi:** Membuka halaman `index.html`, kemudian memperhatikan logo pada navbar. Logo tidak tampil dan muncul ikon gambar rusak.
- **Hipotesis 1:** File logo tidak tersedia di dalam folder proyek. (Gugur, karena file `logo.svg` sebenarnya tersedia di folder `assets`).
- **Hipotesis 2:** Path gambar pada HTML tidak sesuai dengan lokasi file sebenarnya. (Terbukti).
- **Bukti DevTools:** Pada tab Network ditemukan permintaan gambar `img/logo.svg` yang menghasilkan status 404. File sebenarnya berada di `assets/logo.svg`.
- **Perbaikan (berkas:baris):** `index.html:13`, mengubah path gambar menjadi `assets/logo.svg`.
- **Commit:** `ab9ed80`
- **Uji ulang:** Logo berhasil tampil pada navbar dan permintaan gambar di Network tidak lagi menghasilkan 404.

## G2: Kartu karya tersusun satu kolom

- **Reproduksi:** Membuka halaman menggunakan laptop dengan lebar layar lebih dari 992 px. Kartu karya tetap tersusun satu kolom.
- **Hipotesis 1:** Ukuran layar tidak memenuhi breakpoint Bootstrap. (Gugur, karena lebar layar sudah lebih dari 992 px).
- **Hipotesis 2:** Elemen galeri belum menggunakan class `row` dari Bootstrap. (Terbukti).
- **Bukti DevTools:** Melalui tab Elements ditemukan bahwa elemen `#galeri` hanya memiliki class `g-3` dan belum memiliki class `row`.
- **Perbaikan (berkas:baris):** `index.html:34`, menambahkan class `row` sehingga menjadi `class="row g-3"`.
- **Commit:** `af20ff3`
- **Uji ulang:** Kartu karya berhasil tersusun menjadi beberapa kolom pada layar lebar.

## G3: Filter kategori tidak berfungsi

- **Reproduksi:** Memilih kategori Video pada dropdown filter. Daftar karya tidak dapat diperbarui dan muncul pesan error pada Console.
- **Hipotesis 1:** Data kategori pada `data.js` tidak sesuai dengan pilihan dropdown. (Gugur, karena data kategori Video tersedia).
- **Hipotesis 2:** Selector JavaScript tidak sesuai dengan ID elemen HTML. (Terbukti).
- **Bukti DevTools:** Console menampilkan TypeError karena JavaScript mencoba memasang event listener pada elemen yang tidak ditemukan. Selector menggunakan `#filter-kategori`, sedangkan ID HTML adalah `filterKategori`.
- **Perbaikan (berkas:baris):** `main.js:53` pada kode awal, mengganti selector menjadi `filterKategori` melalui variabel yang sudah dideklarasikan.
- **Commit:** `f18aea5`
- **Uji ulang:** Memilih kategori Video berhasil menampilkan karya dengan kategori Video tanpa error pada Console.

## G4: Jumlah karya tidak berubah

- **Reproduksi:** Mengetik kata Video pada kotak pencarian dan memperhatikan teks jumlah karya.
- **Hipotesis 1:** Data karya tidak mengalami perubahan. (Gugur, karena jumlah hasil pencarian berubah).
- **Hipotesis 2:** Teks jumlah karya menggunakan jumlah seluruh data, bukan jumlah hasil penyaringan. (Terbukti).
- **Bukti DevTools:** Melalui pemeriksaan kode pada fungsi `tampil()`, ditemukan bahwa teks jumlah menggunakan `KARYA.length` untuk kedua nilai, sehingga jumlah hasil pencarian tidak diperhitungkan.
- **Perbaikan (berkas:baris):** `main.js:38`, mengganti perhitungan jumlah hasil menjadi `hasil.length`.
- **Commit:** `f1eb084`
- **Uji ulang:** Ketika mencari Video, jumlah karya yang ditampilkan berubah menjadi 2 dari 6 karya.

## G5: Tombol Detail tidak berfungsi setelah pencarian

- **Reproduksi:** Membuka halaman, mengetik Animasi pada kotak pencarian, kemudian menekan tombol Detail pada salah satu kartu.
- **Hipotesis 1:** Data karya tidak memiliki ID yang sesuai. (Gugur, karena setiap karya memiliki ID).
- **Hipotesis 2:** Event listener tombol hilang ketika elemen galeri diperbarui. (Terbukti).
- **Bukti DevTools:** Pemeriksaan kode menunjukkan bahwa elemen galeri diperbarui menggunakan `replaceChildren()`. Tombol yang baru dibuat tidak memiliki event listener karena listener sebelumnya hanya dipasang satu kali saat halaman pertama dibuka.
- **Perbaikan (berkas:baris):** `main.js:41–47`, menerapkan event delegation dengan memasang event listener pada elemen galeri sehingga tombol Detail yang dibuat ulang tetap dapat digunakan.
- **Commit:** `520b527`
- **Uji ulang:** Tombol Detail tetap berfungsi setelah melakukan pencarian dan menampilkan informasi karya yang dipilih.

## G6: Pencarian tidak menemukan karya dengan huruf kecil

- **Reproduksi:** Mengetik animasi menggunakan huruf kecil pada kotak pencarian.
- **Hipotesis 1:** Data karya tidak memiliki kata Animasi. (Gugur, karena terdapat beberapa judul karya yang mengandung kata Animasi).
- **Hipotesis 2:** Pencarian menggunakan perbandingan huruf yang bersifat case-sensitive. (Terbukti).
- **Bukti DevTools:** Pemeriksaan kode fungsi `saring()` menunjukkan bahwa pencarian menggunakan `includes()` tanpa menyamakan huruf besar dan kecil terlebih dahulu.
- **Perbaikan (berkas:baris):** `main.js:10–14`, menggunakan `toLowerCase()` pada kata pencarian dan judul karya sebelum menjalankan `includes()`.
- **Commit:** `3ddb7b6`
- **Uji ulang:** Pencarian menggunakan kata animasi, Animasi, maupun ANIMASI berhasil menemukan karya yang sesuai.

---

## Kesimpulan

Berdasarkan proses debugging pada aplikasi Katalog Karya, ditemukan enam bug (G1–G6) yang berhasil diperbaiki. Proses pemeriksaan dilakukan menggunakan DevTools melalui tab Network, Console, Elements, serta pemeriksaan alur JavaScript. Setiap perbaikan dilakukan melalui commit terpisah agar perubahan mudah dilacak. Setelah seluruh perbaikan dilakukan, aplikasi dapat menampilkan logo, menyusun kartu dalam beberapa kolom, menjalankan filter dan pencarian, memperbarui jumlah karya, serta menjalankan tombol Detail dengan baik.
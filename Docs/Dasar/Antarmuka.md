---
    status: release
    title: "Antarmuka"
    description: 
    pageDecoration:
      tree:
        priority: 10
---
# Antarmuka

Sebelum memulai tahap ini pastikan anda sudah memenuhi [[Docs/Persyaratan|syaratnya]].

![[Docs/Dasar/antar-muka.png|Halaman Antarmuka Phoenix]]
Setelah anda berhasil masuk ke dalam satu Pro, anda bisa mengakses beberapa fitur dari Phoenix secara langsung. 

Berikut adalah beberapa bagian antarmuka ini:

1. [[#Bilah Navigasi]]
2. [[#Area Manajemen Folder]]
3. [[#Halaman Kerja]]

## Bilah Navigasi

![[Docs/Dasar/bilah-navigasi.png|Bilah Navigasi Halaman Kerja Phoenix]]
Bagian ini adalah berisi informasi dan kontrol utama untuk mengatur phoenix dengan rincian seperti berikut:

1. Logo Phoenix : informasi bentuk logo phoenix dan versi yang sedang berjalan
2. Pengenal Pro: informasi Pro yang sedang digunakan
3. Saklar Mode Gelap/Terang: tombol mengatur mode gelap atau terang tampilan Phoenix.
4. Saklar Mode Layar Penuh: tombol mengatur mode layar penuh tampilan Phoenix.
5. Tombol Dokumentasi: tombol navigasi untuk masuk ke halaman dokumentasi
6. Logo Ginalne: tombol navigasi untuk pergi ke halaman [Ginalne](https://ginalne.com).
7. Pengenal Akun: tinformasi Akun yang sedang digunakan serta tombol agar menampilkan rincian Akun serta navigasi tambahan

## Area Manajemen Folder

![[Docs/Dasar/area-manajemen-folder.png|Area Manajemen Folder dan Komponen Phoenix]]
Bagian ini merupakan tempat Anda mengatur daftar [[Docs/Dasar/Apa itu Folder|Folder]] dan [[Docs/Dasar/Apa itu Komponen|Komponen]] dalam Phoenix dengan rincian seperti berikut:

| Elemen | Nama | Penjelasan |
| ---------- | --------- | ---------------- |
| [[^field/workspace|Documentation]] | Pengenal Workspace | informasi [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] yang sedang dibuka saat ini serta tombol agar dapat mengganti ke Workspace lain. Selengkapnya lihat [[Docs/Dasar/Berpindah Workspace]]. |
| [[^button/nolabel/refresh]] | Tombol Penyegaran | tombol untuk menyegarkan (*refresh*) kembali daftar folder dan komponen. |
| [[^toggle/move]] | Saklar Pemindahan | tombol saklar untuk mengubah mode pemindahan komponen secara drag & drop. |
| [[^toggle/search]] | Saklar Pencarian | tombol saklar untuk menampilkan isian pencarian folder dan komponen |
| Kolom bagian bawah | Kolom Manajemen Komponen | kolom yang berisi daftar folder dan komponen |
   
## Halaman Kerja

![[Docs/Dasar/kolom-tab.png|Halaman Kerja Utama Phoenix]]
Bagian ini merupakan tempat Anda mengerjakan dan mengelola data Anda melalui komponen yang sedang aktif rincian seperti berikut:

1. Kolom Tab : bagian di bagian atas jendela yang menampilkan halaman kerja. Masing-masing tab dapat dipindahkan atau dihapus dengan konteks menu seperti berikut:
   * Close: agar menutup tab
   * Close All Except This: agar menutup semua tab selain dari tab yang dipilih
   * Close All: agar menutup semua tab
2. Kolom Kerja : bagian ini adalah bagian dimana komponen yang aktif dibuka muncul. Komponen yang dimaksud merupakan komponen dari [[Docs/Modul Data/Pengenalan|Modul Data]], [[Docs/Modul Interface/Pengenalan|Modul Interface]], [[Docs/Modul Logic/Pengenalan|Modul Logic]] atau [[Docs/Modul Developer/Pengenalan|Modul Developer]]


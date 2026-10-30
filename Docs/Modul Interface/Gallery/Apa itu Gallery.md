---
    status: release
    title: "Apa itu Gallery?"
    description: Pengenalan Gallery, komponen modul Interface untuk menyajikan setiap Row dari sebuah Table sebagai kartu visual.
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="0 0 16 16">
  <path d="M1 2.5A1.5 1.5 0 0 1 2.5 1h3A1.5 1.5 0 0 1 7 2.5v3A1.5 1.5 0 0 1 5.5 7h-3A1.5 1.5 0 0 1 1 5.5zM2.5 2a.5.5 0 0 0-.5.5v3a.5.5 0 0 0 .5.5h3a.5.5 0 0 0 .5-.5v-3a.5.5 0 0 0-.5-.5zm6.5.5A1.5 1.5 0 0 1 10.5 1h3A1.5 1.5 0 0 1 15 2.5v3A1.5 1.5 0 0 1 13.5 7h-3A1.5 1.5 0 0 1 9 5.5zm1.5-.5a.5.5 0 0 0-.5.5v3a.5.5 0 0 0 .5.5h3a.5.5 0 0 0 .5-.5v-3a.5.5 0 0 0-.5-.5zM1 10.5A1.5 1.5 0 0 1 2.5 9h3A1.5 1.5 0 0 1 7 10.5v3A1.5 1.5 0 0 1 5.5 15h-3A1.5 1.5 0 0 1 1 13.5zm1.5-.5a.5.5 0 0 0-.5.5v3a.5.5 0 0 0 .5.5h3a.5.5 0 0 0 .5-.5v-3a.5.5 0 0 0-.5-.5zm6.5.5A1.5 1.5 0 0 1 10.5 9h3a1.5 1.5 0 0 1 1.5 1.5v3a1.5 1.5 0 0 1-1.5 1.5h-3A1.5 1.5 0 0 1 9 13.5zm1.5-.5a.5.5 0 0 0-.5.5v3a.5.5 0 0 0 .5.5h3a.5.5 0 0 0 .5-.5v-3a.5.5 0 0 0-.5-.5z"/>
</svg>'
      tree:
        priority: 4
    icon: assets/icons/type/-0.svg
---
# Apa itu Gallery?

>**note** Gallery merupakan salah satu komponen dalam modul [[Docs/Modul Interface/Pengenalan|Interface]] di Phoenix.

Gallery adalah komponen yang dapat digunakan untuk menyajikan data dalam bentuk kartu visual yang menonjolkan konten dari setiap data.

Gallery ideal untuk koleksi yang bersifat visual, seperti katalog, portofolio, atau daftar aset, sehingga data lebih mudah dikenali sekilas. Setiap [[Docs/Tipe Data/Row]] dari [[Docs/Tipe Data/Table]] tampil sebagai satu kartu, dan isi kartu dapat Anda atur sendiri melalui template.

## Mengapa Menggunakan Gallery?

- **Data dikenali sekilas.** Setiap data tampil sebagai kartu visual, sehingga Anda tidak perlu membaca baris demi baris.
- **Cocok untuk koleksi visual.** Katalog, portofolio, dan daftar aset tampil lebih hidup dibandingkan tampilan tabel.
- **Format data tampil sebaik mungkin.** Semua format data ditampilkan di kartu, termasuk gambar.
- **Tampilan kartu dapat disesuaikan.** Anda menentukan [[Docs/Tipe Data/Column]] yang tampil, posisinya pada kartu, dan desainnya melalui [[Docs/Styling/Pengenalan|Styling]].
- **Data tetap terhubung ke sumbernya.** [[Docs/Tipe Data/Row]] dapat dilihat, diubah, ditambah, dan dihapus langsung dari Gallery sesuai hak akses Anda.

## Konsep Utama

| Istilah | Penjelasan |
| ------- | ---------- |
| [[Docs/Tipe Data/Table]] | Sumber data Gallery. Wajib dipilih saat membuat Gallery dan tidak dapat diubah setelahnya. |
| [[Docs/Tipe Data/Row]] | Satu baris pada Table. Setiap Row tampil sebagai satu kartu di Gallery. |
| [[#Cara Kerja Gallery|Kartu]] | Tampilan satu Row di Gallery. Isi dan tata letaknya ditentukan oleh template. |
| [[Docs/Modul Interface/Gallery/Mengatur Templat|Template Kartu]] | Pengaturan tata letak kartu yang terdiri dari [[^field|Header]], [[^field|Body]], dan [[^field|Footer]]. |
| [[Docs/Tipe Data/Column]] | Kolom Table yang ditambahkan ke template dan tampil pada kartu sesuai posisinya. |
| [[Docs/Styling/Pengenalan|Styling]] | Nama class yang menyesuaikan desain Column pada kartu. |
| [[Docs/Tipe Data/Query#Filter|Filter]] | Daftar kondisi (kolom, operator, dan operand) untuk menyaring Row yang tampil sebagai kartu. |
| [[Docs/Modul Data/Table/Apa itu Table#Membuat Table|Alias]] | Column Table yang menjadi isi kartu bila template masih kosong. |

## Cara Kerja

Penjelasan cara kerja Gallery lihat selengkap nya di [[Docs/Modul Interface/Gallery/Cara Kerja|Cara Kerja Gallery]].

## Mengelola Gallery

Berikut adalah halaman yang menjelaskan cara untuk mengelolanya:
1. [[Docs/Modul Interface/Gallery/Membuat Baru]] Gallery dalam halaman kerja.
2. [[Docs/Modul Interface/Gallery/Mengubah]] Atribut Gallery seperti [[^field|Name]], [[^field|Description]], atau [[^field|Filter]].
3. [[Docs/Modul Interface/Gallery/Menghapus]] Gallery.
4. [[Docs/Modul Interface/Gallery/Mengatur Templat]] Kartu dalam Gallery.

## Antarmuka

Penjelasan antarmuka Gallery lihat selengkap nya di [[Docs/Modul Interface/Gallery/Antarmuka|Antarmuka Gallery]].

## Mengatur Template Kartu

Kartu didalam Gallery bisa disesuaikan sesuai kebutuhan agar membuat interaksi menjadi lebih mudah, selengkapnya lihat [[Docs/Modul Interface/Gallery/Mengatur Templat]].

## Praktik Terbaik

- **Pilih Table sumber dengan tepat** karena [[^field|Table]] tidak dapat diubah setelah Gallery dibuat. Jika salah, buat Gallery baru.
- **Atur template sejak awal.** Template kosong hanya menampilkan [[Docs/Modul Data/Table/Apa itu Table#Membuat Table|Alias]], sehingga kartu belum memanfaatkan gambar atau konten lain.
- **Letakkan konten yang paling menonjol**, seperti gambar, pada [[^field|Header]] atau awal [[^field|Body]] agar mudah dikenali sekilas.
- **Gunakan [[^field|Styling]]** untuk menyeragamkan tampilan, misalnya rata kanan atau teks tebal pada Column tertentu.
- **Gunakan [[^field|Filter]]** agar hanya [[Docs/Tipe Data/Row]] yang relevan tampil sebagai kartu.

## Batasan dan Catatan

- Satu Gallery hanya menampilkan [[Docs/Tipe Data/Row]] dari satu [[Docs/Tipe Data/Table]], dan [[^field|Table]] tidak dapat diubah setelah Gallery dibuat.
- Mengubah [[Docs/Tipe Data/Row]] lewat Form Table hanya dapat dilakukan jika Data Access Table di [[Docs/Modul Developer/Workspace/Data Access|Workspace]] mengizinkan.
- Menghapus Row lewat [[^field|Delete]] menghapusnya dari Table sumber dan tidak dapat dikembalikan.
- Menghapus Gallery tidak menghapus [[Docs/Tipe Data/Row]] di Table sumber.
- Template kosong menampilkan [[Docs/Modul Data/Table/Apa itu Table#Membuat Table|Alias]], bukan seluruh Column.

## TL:DR

- Gallery adalah komponen modul [[Docs/Modul Interface/Pengenalan|Interface]] yang menyajikan setiap [[Docs/Tipe Data/Row]] dari [[Docs/Tipe Data/Table]] sebagai kartu visual.
- Halaman kerja terdiri dari bilah navigasi ([[^button/edit|Edit]], [[^button/setting|Column]], [[^button/refresh|Refresh]], dan pencarian) serta area kartu.
- Saat membuat Gallery, [[^field|Table]] wajib diisi dan [[^field|Filter]] diisi jika dibutuhkan. Table tidak dapat diubah setelahnya.
- Atur tampilan kartu lewat [[^button/setting|Column]] ➜ [[^field|Setup Gallery Template]] dengan bagian [[^field|Header]], [[^field|Body]], dan [[^field|Footer]].
- Klik kanan kartu untuk mengubah Row, klik kiri kartu untuk [[^field|Detail]], [[^field|Add Row]], dan [[^field|Delete]].
- Berhati-hatilah pada [[^field|Delete]] karena menghapus Row dari Table sumber.

## 

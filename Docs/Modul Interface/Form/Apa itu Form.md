---
    status: release
    title: "Apa itu Form?"
    description: "Form adalah komponen untuk menginput, melihat, dan mengubah data secara terstruktur, serta dapat dibagikan kepada publik untuk mengumpulkan data."
    pageDecoration: 
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="0 0 16 16">
  <path
    d="M7 2.5a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-7a.5.5 0 0 1-.5-.5zM2 1a2 2 0 0 0-2 2v2a2 2 0 0 0 2 2h2a2 2 0 0 0 2-2V3a2 2 0 0 0-2-2zm0 8a2 2 0 0 0-2 2v2a2 2 0 0 0 2 2h2a2 2 0 0 0 2-2v-2a2 2 0 0 0-2-2zm.854-3.646a.5.5 0 0 1-.708 0l-1-1a.5.5 0 1 1 .708-.708l.646.647 1.646-1.647a.5.5 0 1 1 .708.708zm0 8a.5.5 0 0 1-.708 0l-1-1a.5.5 0 0 1 .708-.708l.646.647 1.646-1.647a.5.5 0 0 1 .708.708zM7 10.5a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-7a.5.5 0 0 1-.5-.5zm0-5a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5m0 8a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5" />
</svg>'
      tree:
        priority: 10
    icon: assets/icons/type/-f.svg
---
# Apa itu Form?

>**note** Form merupakan salah satu komponen dalam modul [[Docs/Modul Interface/Pengenalan|Interface]] di Phoenix.

Form adalah komponen yang dapat digunakan untuk menginput, melihat, dan mengubah data secara terstruktur. Setiap kolom ditampilkan sebagai *field* yang jelas dan terarah, sehingga proses pengisian data menjadi lebih rapi, konsisten, dan minim kesalahan.

Anda dapat menyusun tampilan Form sendiri dari beberapa [[#Memahami Elemen|Elemen]], mengikatnya ke data di [[Docs/Modul Data/Table/Apa itu Table|Table]], lalu membagikannya kepada publik lewat [[#Mempublikasikan Form|Publish]] agar proses pengumpulan data menjadi lebih cepat dan efektif.

## Mengapa Menggunakan Form?

- **Pengisian data lebih rapi.** Setiap kolom tampil sebagai *field* yang jelas, sehingga pengisi tahu persis apa yang harus diisi.
- **Data konsisten dan minim kesalahan.** Setiap *field* terikat ke [[Docs/Tipe Data/Column]] pada [[Docs/Tipe Data/Row]] yang tepat lewat [[#Binding Form|Binding]], sehingga hasil isian masuk ke tempat yang benar.
- **Pengumpulan data lebih cepat.** Form dapat dibagikan kepada publik lewat tautan, tanpa pengisi perlu masuk ke Phoenix.
- **Tampilan dapat disesuaikan.** Anda menyusun Form dari [[#Memahami Elemen|Elemen]] dan mengatur gayanya sesuai kebutuhan.
- **Pengiriman mudah dipantau.** Setiap pengiriman tercatat sebagai Submission, lengkap dengan status dan grafiknya di [[#Mengelola Submission|Submission List]].

## Konsep Utama

| Istilah | Penjelasan |
| --- | --- |
| [[#Mengelola Page Form|Page]] | Satu halaman di dalam Form. Satu Form dapat memiliki beberapa Page. |
| [[#Mengelola Page Form|Form Flow]] | Alur Page pada Form. Page paling kiri tampil pertama, dan Form dapat disubmit setelah pengisi mencapai Page terakhir. |
| [[#Memahami Elemen|Elemen]] | Satu objek penyusun isi Form, misalnya teks, tabel, atau kolom isian. |
| [[#Elemen Layout|Layout]] | Kategori Elemen yang berfungsi sebagai templat tempat Elemen lain diletakkan. |
| [[#Elemen Display|Display]] | Kategori Elemen yang menampilkan informasi, baik statis maupun hasil dari nilai Binding. |
| [[#Elemen Input|Input]] | Kategori Elemen untuk mengisi atau menampilkan informasi yang berlaku pada Binding. |
| [[#Binding Form|Binding]] | Ikatan antara Elemen dan data di [[Docs/Modul Data/Table/Apa itu Table|Table]] agar isian dan hasil akhirnya sesuai. |
| [[#Mode View dan Edit Mode|Edit Mode]] | Mode untuk menyusun Form, termasuk melihat informasi Binding dan konfigurasi Elemen. |
| [[#Mempublikasikan Form|Publish]] | Konfigurasi untuk membagikan Form kepada publik. |
| [[#Mengelola Submission|Submission]] | Catatan setiap pengiriman Form, dengan status sukses, menunggu, atau gagal. |

## Cara Kerja

Penjelasan cara kerja Form lihat selengkap nya di [[Docs/Modul Interface/Form/Cara Kerja|Cara Kerja Form]].

## Mengelola Form

Berikut adalah halaman yang menjelaskan cara untuk mengelolanya:
1. [[Docs/Modul Interface/Form/Membuat Baru]] Form dalam halaman kerja.
2. [[Docs/Modul Interface/Form/Mengubah]] Atribut Form seperti [[^field|Name]], [[^field|Description]], atau [[^field|Filter]].
3. [[Docs/Modul Interface/Form/Menghapus]] Form.
4. [[Docs/Modul Interface/Form/Form Page|Mengelola Alur Halaman]] dalam Form.
5. [[Docs/Modul Interface/Form/Elemen Form/Binding|Memahami Binding]] dalam Form.
6. [[Docs/Modul Interface/Form/State|Memahami State]] dalam Form.
7. [[Docs/Modul Interface/Form/Validator|Memahami Validator]] dalam Form.
8. [[Docs/Modul Data/Table/Mempublikasi]]: mengatur publikasi Table.
9. [[Docs/Modul Data/Table/Otomasi]]: menghubungkan Table dengan [[Docs/Event/Apa itu Event|Event]].

## Antarmuka

Penjelasan antarmuka Form lihat selengkap nya di [[Docs/Modul Interface/Form/Antarmuka|Antarmuka Form]].

## Mengatur Template Kartu

Kartu didalam Form bisa disesuaikan sesuai kebutuhan agar membuat interaksi menjadi lebih mudah, selengkapnya lihat [[Docs/Modul Interface/Form/Mengatur Templat]].

Selengkapnya tentang penjelasan khusus setiap Elemen dapat dilihat pada halaman masing-masing di [[#Memahami Elemen]].

## Praktik Terbaik

- **Mulai dari Binding.** Tentukan [[Docs/Modul Data/Table/Apa itu Table|Table]] dan [[Docs/Tipe Data/Column]] tujuan sebelum menyusun [[#Memahami Elemen|Elemen]], agar setiap Elemen Input terikat ke kolom yang tepat.
- **Gunakan Layout untuk tata letak.** Letakkan Elemen Display dan Elemen Input di dalam [[#Elemen Layout|Layout]] agar susunan Form rapi dan mudah dikelola.
- **Gunakan Page untuk memecah isian panjang.** Bagi Form yang panjang ke beberapa [[#Mengelola Page Form|Page]] agar pengisi tidak kewalahan.
- **Uji sebelum dibagikan.** Periksa tampilan di [[#Mode View dan Edit Mode|View]], lalu aktifkan [[^field|Status]] dan salin [[^field|Link]] di [[#Mempublikasikan Form|Publish]] hanya setelah Form siap.
- **Pantau Submission secara berkala.** Gunakan [[#Mengelola Submission|Submission List]] untuk memeriksa Submission berstatus Failure.

## Batasan dan Catatan

- [[#Mode View dan Edit Mode|Edit Mode]] hanya dapat diaktifkan bila [[^field|Data Access]] di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] mengizinkan.
- Menghapus Form menghapus templat (Page, Elemen, dan Binding) beserta riwayat Submission, tetapi data yang sudah tersimpan di [[Docs/Modul Data/Table/Apa itu Table|Table]] tidak langsung terhapus.
- Tautan Publish menjadi tidak valid setelah Form dihapus, dan pengisi yang sedang mengisi Form publik akan mengalami *error* saat mengirim.
- Form hanya dapat disubmit setelah pengisi mencapai Page terakhir pada [[#Mengelola Page Form|Form Flow]].
- Menghapus Elemen Layout menghapus semua Elemen di dalamnya.
- Jika [[^field|Status]] berstatus Non-Active, Form publik hanya dapat dilihat dan tidak dapat dikirim.
- [[^field|Single Submission]] membatasi pengiriman per perangkat, bukan per orang.
- Tombol [[^button/edit|Edit]] hanya mengubah atribut Form, bukan isi Form.
- Start Building dan informasi Binding hanya tampil di [[#Mode View dan Edit Mode|Edit Mode]].

## TL:DR

- **Definisi.** [[#Apa itu Form?|Form]] adalah komponen untuk menginput, melihat, dan mengubah data secara terstruktur, serta dapat dibagikan kepada publik.
- **Antarmuka.** [[#Antarmuka Form|Bilah navigasi]] berisi [[^button/edit|Edit]], [[^button/publish|Publish]], toggle [[^field|mode]], [[^button/save|Save]], [[^button/refresh|Refresh]], dan [[^button/submission|Informasi Submission]].
- **Menyusun.** Tambahkan [[#Mengelola Page Form|Page]], lalu susun isinya dari [[#Memahami Elemen|Elemen]] Layout, Display, dan Input di [[#Mode View dan Edit Mode|Edit Mode]].
- **Menghubungkan data.** [[#Binding Form|Binding]] mengikat Elemen ke [[Docs/Modul Data/Table/Apa itu Table|Table]], [[Docs/Tipe Data/Column]], dan [[Docs/Tipe Data/Row]] agar isian tersimpan di tempat yang tepat.
- **Membagikan dan memantau.** [[#Mempublikasikan Form|Publish]] membagikan Form lewat tautan, dan [[#Mengelola Submission|Submission List]] memantau pengiriman.
- **Hati-hati.** Menghapus Form menghapus templat (Page, Elemen, dan Binding) beserta riwayat Submission, tautan Publish menjadi tidak valid, dan publik yang sedang mengisi akan *error* saat mengirim.

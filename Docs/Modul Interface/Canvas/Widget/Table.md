---
status: draft
title: Widget Table
description: Widget Table menampilkan data Table dalam bentuk tabel pada Canvas, lengkap dengan pagination dan toolbar search yang dapat diaktifkan.
---
# Widget Table

>**note** Widget Table merupakan salah satu widget pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Daftar widget lainnya ada di [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget Canvas]].

Widget Table adalah [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] dalam bentuk tabel di dalam [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Data diambil melalui [[Docs/Tipe Data/Query]], lalu dapat dilengkapi pagination dan toolbar search agar pembaca mudah menelusuri baris.

## Menambahkan Widget Table

Ketik `/table` dalam [[^field|Type something here to add...]] untuk menampilkan variasi tabel lalu pilih salah satunya. Langkah lengkapnya ada di [[Docs/Modul Interface/Canvas/Widget/Menambahkan|Menambahkan Widget]].

## Antarmuka Widget Table

![[Docs/Modul Interface/Form/Widget/Table/interface-widget-table.png]]
Pada [[^mode/edit|Edit]], klik kiri widget untuk menampilkan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar]] di atas widget, [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]] di bawah widget. Contoh gambar di atas menampilkan Widget Table dengan [[^field|pagination]] dan toolbar [[^field|search]] aktif.

### Header Toolbar

| Elemen                                    | Fungsi                                                                                                                         |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Ikon Table (paling kiri)                  | Menandai jenis widget.                                                                                                         |
| Ikon pegangan ⋮⋮                          | Memindahkan widget ke posisi atau Layout lain.                                                                                 |
| [[^toggle|123]]                          | Toggle pagination. Menampilkan atau menyembunyikan bilah pagination di bagian bawah widget.                                    |
| [[^toggle/search|Search]] (ikon kaca pembesar) | Toggle toolbar search. Memunculkan atau menyembunyikan toolbar search di bagian atas widget.                                   |
| [[^field|Data]]                      | [[Docs/Tipe Data/Query]] untuk data yang ditampilkan widget. Klik [[^button/q]] untuk membuka konfigurasi [[Docs/Tipe Data/Query]] yang mengikuti kaidah  [[Docs/Tipe Data/Query#Table Output]]|
| [[^button/delete|Remove]]                | Menghapus widget dari Canvas. Lihat [[#Menghapus Widget Table]].                                                               |

Tombol toggle yang aktif ditandai dengan latar berwarna.

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* pada widget dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]].

### Tampilan tabel

| Bagian                         | Isi                                                                                                                                                |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Kolom                          | Kolom ID dan kolom hasil [[Docs/Tipe Data/Query|Query]]. Ikon kecil di samping nama kolom menunjukkan tipe data kolom.                            |
| Baris                          | Baris hasil Query. Cell yang kosong menampilkan teks [[^field|Empty]].                                                                            |
| Toolbar search                 | Tombol [[^button/refresh|Refresh List]] dan kolom [[^field|Search Data...]]. Tampil bila toggle [[^toggle/search|Search]] aktif.               |
| Pagination                     | Informasi [[^field|Show 50 of 8 items, on page]] (50 adalah batas data per halaman), input nomor halaman dengan [[^button/empty|Go]], serta [[^button/empty|Prev]] dan [[^button/empty|Next]]. Tampil bila toggle [[^button/empty|123]] aktif. |

### Interaksi pada Widget Table

| Fungsi                              | Aksi                         |
| --------------------------------- | -------------------------- |
| Mencari data                        | Ketik kata kunci pada [[^field|Search Data...]].      |
| Menyegarkan daftar                  | Klik [[^button/refresh|Refresh List]].                      |
| Berpindah halaman                   | Klik [[^button/empty|Prev]] atau [[^button/empty|Next]], atau isi nomor halaman lalu klik [[^button/empty|Go]].                      |

## Menghapus Widget Table

Langkah menghapus Widget Table sama dengan menghapus widget lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan
> Menghapus widget akan menghapus semua konfigurasi yang ada termasuk Query yang sudah dibuat. Data sumber dan barisnya tetap aman. Setelah terhapus, aksi tidak bisa dikembalikan..

## Praktik Terbaik

- **Aktifkan [[^toggle|123]] untuk data yang banyak.** Pagination menjaga widget tetap ringkas dan mudah dibaca.
- **Aktifkan [[^toggle/search|Search]] bila pembaca perlu mencari.** Toolbar search memudahkan menemukan baris tanpa menggulir seluruh data.
- **Batasi data lewat [[Docs/Tipe Data/Query|Query]].** Tampilkan hanya kolom dan baris yang dibutuhkan pembaca agar tabel tetap ringkas.
- **Atur [[^field|min.]] tinggi dan lebar.** Beri ruang cukup agar tabel dan pagination tidak terpotong oleh widget lain pada Canvas.
- **Gunakan [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]] untuk mengelola data.** Widget Table hanya untuk menampilkan..

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Apa arti tombol 123 pada header toolbar?**
> [[^toggle|123]] adalah toggle pagination. Saat aktif, bilah pagination tampil di bagian bawah widget untuk berpindah halaman data.
> **Untuk apa tombol kaca pembesar?**
> [[^toggle/search|Search]] adalah toggle untuk memunculkan toolbar search di bagian atas widget, berisi [[^button/refresh|Refresh List]] dan [[^field|Search Data...]].
> **Mengapa saya tidak dapat mengubah isi tabel?**
> Data hasil [[Docs/Tipe Data/Query|Query]]tidak dapat dimanipulasi dari Canvas. Gunakan [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]] untuk mengelola baris.
> **Bagaimana mengatur kolom yang tampil?**
> Kolom dan baris yang tampil ditentukan oleh [[Docs/Tipe Data/Query|Query]]. Klik [[^button/q]] pada header toolbar untuk mengaturnya.
> **Berapa data yang tampil per halaman?**
> Batasnya 50 data per halaman, seperti tertulis pada informasi [[^field|Show 50 of 8 items, on page]].
> **Apakah menghapus widget menghapus data sumber?**
> Tidak. Menghapus widget hanya menghapus tampilan dan konfigurasinya, termasuk [[Docs/Tipe Data/Query|Query]]. Table sumber tetap aman.
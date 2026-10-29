---
status: draft
title: Widget Timeline
description: Widget Timeline menampilkan satu data Table dalam urutan waktu pada Canvas.
---
# Widget Timeline

>**note** Widget Timeline merupakan salah satu widget pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Daftar widget lainnya ada di [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget Canvas]].

Widget Timeline adalah [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] dalam urutan waktu di dalam [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Data diambil melalui [[Docs/Tipe Data/Query]], lalu setiap data hasil Query tampil sebagai blok pada sumbu waktu.

Berbeda dengan komponen [[Docs/Modul Interface/Timeline/Apa itu Timeline|Timeline]] yang memiliki Timeline Event dan banyak Timeline Data, Widget Timeline hanya menyajikan satu data.

## Menambahkan Widget Timeline

Ketik `/timeline` dalam [[^field|Type something here to add...]] untuk menampilkan variasi timeline lalu pilih salah satunya. Langkah lengkapnya ada di [[Docs/Modul Interface/Canvas/Widget/Menambahkan|Menambahkan Widget]].

## Antarmuka Widget Timeline

![[Docs/Modul Interface/Form/Widget/Timeline/interface-widget-timeline.png]]
Pada [[^mode/edit|Edit]], klik kiri widget untuk menampilkan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar]] di atas widget, [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]] di bawah widget.

### Header Toolbar

| Elemen                                    | Fungsi                                                                                                                         |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Ikon Timeline (paling kiri)                  | Menandai jenis widget.                                                                                                         |
| Ikon pegangan ⋮⋮                          | Memindahkan widget ke posisi atau Layout lain.                                                                                 |
| [[^field\|Data]]                          | [[Docs/Tipe Data/Query]] untuk data yang ditampilkan widget. Klik [[^button/q]] untuk membuka konfigurasi [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Timeline Output]] |
| [[^button/delete\|Remove]]                | Menghapus widget dari Canvas. Lihat [[#Menghapus Widget Timeline]].                                                               |

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* pada widget dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]].

### Tampilan timeline

| Bagian                         | Isi                                                                                                                                                |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[^field\|Item List]] | Kolom di sisi kiri yang memuat nama setiap Row hasil [[Docs/Tipe Data/Query\|Query]]. |
| Header waktu | Skala waktu di bagian atas widget. |
| Garis now | Garis dan penanda yang menunjukkan waktu saat ini. |
| Blok data | Satu blok untuk setiap Row, dari waktu Start sampai End. |

### Interaksi pada Widget Timeline

| Fungsi                              | Aksi                         |
| --------------------------------- | -------------------------- |
| Berpindah waktu | Gulir horizontal pada widget. Berlaku bila rentang waktu melebihi lebar widget. |
| Mengubah skala waktu | Gulir *wheel* pada widget. |

## Menghapus Widget Timeline

Langkah menghapus Widget Timeline sama dengan menghapus widget lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan
> Menghapus widget akan menghapus semua konfigurasi yang ada termasuk Query yang sudah dibuat. Data sumber dan barisnya tetap aman. Setelah terhapus, aksi tidak bisa dikembalikan.

## Praktik Terbaik

- **Batasi data lewat [[Docs/Tipe Data/Query|Query]].** Tampilkan hanya data yang dibutuhkan pembaca agar widget tetap ringkas dan mudah dibaca.
- **Atur [[^field|min.]] tinggi dan lebar.** Beri ruang cukup agar isi widget tidak terpotong oleh widget lain pada Canvas.
- **Pastikan kolom Start dan End berformat waktu.** Gunakan format [[Docs/Tipe Data/DateTime]], [[Docs/Tipe Data/Date]], atau [[Docs/Tipe Data/DateTimeZone]] sesuai kaidah [[Docs/Tipe Data/Query#Timeline Output]].

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Query seperti apa yang dipakai Widget Timeline?**
> Query harus mengikuti kaidah [[Docs/Tipe Data/Query#Timeline Output|Timeline Output]]. Atur melalui [[^button/q]] pada [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar|Header Toolbar]].
> **Mengapa widget hanya menampilkan satu data?**
> Widget Timeline hanya menyajikan satu data. Untuk banyak Timeline Data dan Timeline Event, gunakan komponen [[Docs/Modul Interface/Timeline/Apa itu Timeline|Timeline]].
> **Mengapa saya tidak dapat menggeser blok?**
> Data hasil [[Docs/Tipe Data/Query|Query]] tidak dapat dimanipulasi dari Canvas. Gunakan [[Docs/Modul Interface/Timeline/Apa itu Timeline|Timeline]] untuk mengatur waktu Start dan End.
> **Bagaimana mengatur ukuran dan jarak widget?**
> Gunakan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel|Layout Panel]] untuk mengatur [[^field|min.]], [[^field|padding]], dan [[^field|margin]].
> **Apakah menghapus widget menghapus data sumber?**
> Tidak. Menghapus widget hanya menghapus tampilan dan konfigurasinya, termasuk [[Docs/Tipe Data/Query|Query]]. Data sumber tetap aman.


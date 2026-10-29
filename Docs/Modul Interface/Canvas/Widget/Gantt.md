---
status: draft
title: Widget Gantt
description: Widget Gantt menampilkan data Table sebagai bilah jadwal pada sumbu waktu di Canvas.
---
# Widget Gantt

>**note** Widget Gantt merupakan salah satu widget pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Daftar widget lainnya ada di [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget Canvas]].

Widget Gantt adalah [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai bilah jadwal pada sumbu waktu di dalam [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Data diambil melalui [[Docs/Tipe Data/Query]], lalu setiap data hasil Query tampil sebagai satu bilah sesuai waktu mulai dan waktu selesainya, sehingga rencana dan durasi mudah dipantau.

## Menambahkan Widget Gantt

Ketik `/gantt` dalam [[^field|Type something here to add...]] untuk menampilkan variasi gantt lalu pilih salah satunya. Langkah lengkapnya ada di [[Docs/Modul Interface/Canvas/Widget/Menambahkan|Menambahkan Widget]].

## Antarmuka Widget Gantt

![[Docs/Modul Interface/Form/Widget/Gantt/interface-widget-gantt.png]]
Pada [[^mode/edit|Edit]], klik kiri widget untuk menampilkan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar]] di atas widget, [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]] di bawah widget.

### Header Toolbar

| Elemen                                    | Fungsi                                                                                                                         |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Ikon Gantt (paling kiri)                  | Menandai jenis widget.                                                                                                         |
| Ikon pegangan ⋮⋮                          | Memindahkan widget ke posisi atau Layout lain.                                                                                 |
| [[^field\|Data]]                          | [[Docs/Tipe Data/Query]] untuk data yang ditampilkan widget. Klik [[^button/q]] untuk membuka konfigurasi [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Gantt Output]] |
| [[^button/delete\|Remove]]                | Menghapus widget dari Canvas. Lihat [[#Menghapus Widget Gantt]].                                                               |

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* pada widget dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]].

### Tampilan gantt

| Bagian                         | Isi                                                                                                                                                |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Header waktu | Skala waktu di bagian atas widget sebagai acuan posisi bilah. |
| Bilah | Satu bilah untuk setiap data hasil [[Docs/Tipe Data/Query\|Query]]. Posisi dan panjang bilah mengikuti waktu mulai dan waktu selesai data. |

### Interaksi pada Widget Gantt

| Fungsi                              | Aksi                         |
| --------------------------------- | -------------------------- |
| Berpindah waktu | Gulir horizontal pada widget. Berlaku bila rentang waktu melebihi lebar widget. |

## Menghapus Widget Gantt

Langkah menghapus Widget Gantt sama dengan menghapus widget lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan
> Menghapus widget akan menghapus semua konfigurasi yang ada termasuk Query yang sudah dibuat. Data sumber dan barisnya tetap aman. Setelah terhapus, aksi tidak bisa dikembalikan.

## Praktik Terbaik

- **Batasi data lewat [[Docs/Tipe Data/Query|Query]].** Tampilkan hanya data yang dibutuhkan pembaca agar widget tetap ringkas dan mudah dibaca.
- **Atur [[^field|min.]] tinggi dan lebar.** Beri ruang cukup agar isi widget tidak terpotong oleh widget lain pada Canvas.
- **Pastikan kolom waktu berformat waktu.** Kolom waktu mulai dan waktu selesai pada Query harus berformat waktu agar bilah dapat digambar.
- **Kelola data jadwal di [[Docs/Modul Data/Table/Apa itu Table|Table]].** Perubahan jadwal dilakukan pada data sumber, lalu widget mengikuti.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Query seperti apa yang dipakai Widget Gantt?**
> Query harus mengikuti kaidah [[Docs/Tipe Data/Query#Gantt Output|Gantt Output]]. Atur melalui [[^button/q]] pada [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar|Header Toolbar]].
> **Mengapa saya tidak dapat menggeser bilah?**
> Data hasil [[Docs/Tipe Data/Query|Query]] tidak dapat dimanipulasi dari Canvas. Ubah waktu mulai dan selesai pada data sumber, lalu widget menampilkan perubahannya.
> **Bagaimana mengatur ukuran dan jarak widget?**
> Gunakan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel|Layout Panel]] untuk mengatur [[^field|min.]], [[^field|padding]], dan [[^field|margin]].
> **Apakah menghapus widget menghapus data sumber?**
> Tidak. Menghapus widget hanya menghapus tampilan dan konfigurasinya, termasuk [[Docs/Tipe Data/Query|Query]]. Data sumber tetap aman.


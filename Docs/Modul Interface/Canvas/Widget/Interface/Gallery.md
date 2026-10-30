---
status: draft
title: Widget Gallery
description: Widget Gallery menampilkan data Table sebagai kartu visual yang menonjolkan gambar atau konten pada Canvas.
---
# Widget Gallery

>**note** Widget Gallery merupakan salah satu widget pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Daftar widget lainnya ada di [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget Canvas]].

Widget Gallery adalah [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] dalam bentuk kartu visual di dalam [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Data diambil melalui [[Docs/Tipe Data/Query]], lalu setiap data hasil Query tampil sebagai satu kartu yang menonjolkan gambar atau konten data, sehingga mudah dikenali sekilas.

## Menambahkan Widget Gallery

Ketik `/gallery` dalam [[^field|Type something here to add...]] untuk menampilkan variasi gallery lalu pilih salah satunya. Langkah lengkapnya ada di [[Docs/Modul Interface/Canvas/Widget/Menambahkan|Menambahkan Widget]].

## Antarmuka Widget Gallery

![[Docs/Modul Interface/Form/Widget/Gallery/interface-widget-gallery.png]]
Pada [[^mode/edit|Edit]], klik kiri widget untuk menampilkan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar]] di atas widget, [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]] di bawah widget.

### Header Toolbar

| Elemen                                    | Fungsi                                                                                                                         |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Ikon Gallery (paling kiri)                  | Menandai jenis widget.                                                                                                         |
| Ikon pegangan ⋮⋮                          | Memindahkan widget ke posisi atau Layout lain.                                                                                 |
| [[^field|Data]]                          | [[Docs/Tipe Data/Query]] untuk data yang ditampilkan widget. Klik [[^button/q]] untuk membuka konfigurasi [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Gallery Output]] |
| [[^button/delete|Remove]]                | Menghapus widget dari Canvas. Lihat [[#Menghapus Widget Gallery]].                                                               |

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* pada widget dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]].

### Tampilan gallery

| Bagian                         | Isi                                                                                                                                                |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Kartu | Satu kartu visual untuk setiap data hasil [[Docs/Tipe Data/Query|Query]], menonjolkan gambar atau konten data. |

### Interaksi pada Widget Gallery

| Fungsi                              | Aksi                         |
| --------------------------------- | -------------------------- |
| Menggulir daftar kartu | Gulir pada widget. Berlaku bila jumlah atau tinggi kartu melebihi widget. |

## Menghapus Widget Gallery

Langkah menghapus Widget Gallery sama dengan menghapus widget lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan
> Menghapus widget akan menghapus semua konfigurasi yang ada termasuk Query yang sudah dibuat. Data sumber dan barisnya tetap aman. Setelah terhapus, aksi tidak bisa dikembalikan.

## Praktik Terbaik

- **Batasi data lewat [[Docs/Tipe Data/Query|Query]].** Tampilkan hanya data yang dibutuhkan pembaca agar widget tetap ringkas dan mudah dibaca.
- **Atur [[^field|min.]] tinggi dan lebar.** Beri ruang cukup agar isi widget tidak terpotong oleh widget lain pada Canvas.
- **Gunakan [[Docs/Modul Interface/Gallery/Apa itu Gallery|Gallery]] untuk mengelola data.** Pengelolaan kartu dan data dilakukan di komponen Gallery, sedangkan widget hanya menampilkan.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Query seperti apa yang dipakai Widget Gallery?**
> Query harus mengikuti kaidah [[Docs/Tipe Data/Query#Gallery Output|Gallery Output]]. Atur melalui [[^button/q]] pada [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar|Header Toolbar]].
> **Mengapa saya tidak dapat mengubah isi kartu?**
> Data hasil [[Docs/Tipe Data/Query|Query]] tidak dapat dimanipulasi dari Canvas. Gunakan [[Docs/Modul Interface/Gallery/Apa itu Gallery|Gallery]] untuk mengelola kartu dan data.
> **Bagaimana mengatur ukuran dan jarak widget?**
> Gunakan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel|Layout Panel]] untuk mengatur [[^field|min.]], [[^field|padding]], dan [[^field|margin]].
> **Apakah menghapus widget menghapus data sumber?**
> Tidak. Menghapus widget hanya menghapus tampilan dan konfigurasinya, termasuk [[Docs/Tipe Data/Query|Query]]. Data sumber tetap aman.


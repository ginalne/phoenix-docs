---
status: draft
title: Widget Kanban
description: Widget Kanban menampilkan data Table sebagai kolom dan kartu berdasarkan status atau kategori pada Canvas.
---
# Widget Kanban

>**note** Widget Kanban merupakan salah satu widget pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Daftar widget lainnya ada di [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget Canvas]].

Widget Kanban adalah [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] dalam bentuk kolom dan kartu berdasarkan status atau kategori di dalam [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Data diambil melalui [[Docs/Tipe Data/Query]], lalu setiap data hasil Query tampil sebagai satu kartu pada kolom yang sesuai.

## Menambahkan Widget Kanban

Ketik `/kanban` dalam [[^field|Type something here to add...]] untuk menampilkan variasi kanban lalu pilih salah satunya. Langkah lengkapnya ada di [[Docs/Modul Interface/Canvas/Widget/Menambahkan|Menambahkan Widget]].

## Antarmuka Widget Kanban

![[Docs/Modul Interface/Form/Widget/Kanban/interface-widget-kanban.png]]
Pada [[^mode/edit|Edit]], klik kiri widget untuk menampilkan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar]] di atas widget, [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]] di bawah widget.

### Header Toolbar

| Elemen                                    | Fungsi                                                                                                                         |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Ikon Kanban (paling kiri)                  | Menandai jenis widget.                                                                                                         |
| Ikon pegangan ⋮⋮                          | Memindahkan widget ke posisi atau Layout lain.                                                                                 |
| [[^field|Data]]                          | [[Docs/Tipe Data/Query]] untuk data yang ditampilkan widget. Klik [[^button/q]] untuk membuka konfigurasi [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Kanban Output]] |
| [[^button/delete|Remove]]                | Menghapus widget dari Canvas. Lihat [[#Menghapus Widget Kanban]].                                                               |

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* pada widget dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]].

### Tampilan kanban

| Bagian                         | Isi                                                                                                                                                |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Kolom | Satu kolom untuk setiap status atau kategori. Header kolom menampilkan jumlah kartu dan nama kolom. |
| Kartu | Setiap data hasil [[Docs/Tipe Data/Query|Query]] tampil sebagai satu kartu pada kolom yang sesuai. |

### Interaksi pada Widget Kanban

| Fungsi                              | Aksi                         |
| --------------------------------- | -------------------------- |
| Menggulir daftar kartu | Arahkan kursor ke satu kolom, lalu gulir atas atau bawah. Berlaku bila tinggi kartu melebihi widget. |
| Menggulir kolom | Arahkan kursor ke widget, lalu gulir kiri atau kanan. Berlaku bila lebar kolom melebihi widget. |

## Menghapus Widget Kanban

Langkah menghapus Widget Kanban sama dengan menghapus widget lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan
> Menghapus widget akan menghapus semua konfigurasi yang ada termasuk Query yang sudah dibuat. Data sumber dan barisnya tetap aman. Setelah terhapus, aksi tidak bisa dikembalikan.

## Praktik Terbaik

- **Batasi data lewat [[Docs/Tipe Data/Query|Query]].** Tampilkan hanya data yang dibutuhkan pembaca agar widget tetap ringkas dan mudah dibaca.
- **Atur [[^field|min.]] tinggi dan lebar.** Beri ruang cukup agar isi widget tidak terpotong oleh widget lain pada Canvas.
- **Pastikan Query menghasilkan status atau kategori yang jelas.** Kolom Kanban dibentuk dari status atau kategori sehingga pembaca mudah memahami tahapan data.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Query seperti apa yang dipakai Widget Kanban?**
> Query harus mengikuti kaidah [[Docs/Tipe Data/Query#Kanban Output|Kanban Output]]. Atur melalui [[^button/q]] pada [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar|Header Toolbar]].
> **Mengapa saya tidak dapat memindahkan kartu?**
> Data hasil [[Docs/Tipe Data/Query|Query]] tidak dapat dimanipulasi dari Canvas. Gunakan [[Docs/Modul Interface/Kanban/Apa itu Kanban|Kanban]] untuk memindahkan kartu dan mengelola data.
> **Bagaimana mengatur ukuran dan jarak widget?**
> Gunakan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel|Layout Panel]] untuk mengatur [[^field|min.]], [[^field|padding]], dan [[^field|margin]].
> **Apakah menghapus widget menghapus data sumber?**
> Tidak. Menghapus widget hanya menghapus tampilan dan konfigurasinya, termasuk [[Docs/Tipe Data/Query|Query]]. Data sumber tetap aman.


---
status: draft
title: Widget Chart Linear
description: Widget Chart Linear menampilkan data Table sebagai bar linear dengan track, marker, threshold, dan animasi pada Canvas.
---
# Widget Chart Linear

>**note** Widget Chart Linear merupakan salah satu widget pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Daftar widget lainnya ada di [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget Canvas]].

Widget Chart Linear adalah [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai bar linear di dalam [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Data diambil melalui [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Series Output]], lalu setiap data digambarkan sebagai satu bar yang terisi sesuai nilainya.

Anda dapat mengatur batas nilai, posisi dan format nilai, mode, bentuk bar, orientasi, track, marker, threshold, label, dan animasi melalui Data Panel dan Design Panel.

## Menambahkan Widget Chart Linear

Ketik `/chart linear` dalam [[^field|Type something here to add...]] untuk menampilkan variasi lalu pilih salah satunya. Langkah lengkapnya ada di [[Docs/Modul Interface/Canvas/Widget/Menambahkan|Menambahkan Widget]].

## Antarmuka Widget Chart Linear

![[Docs/Modul Interface/Form/Widget/Chart Linear/interface-widget-chart-linear.png]]
Pada [[^mode/edit|Edit]], klik kiri widget untuk menampilkan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar]] di atas widget, serta [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]], [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Data Panel]], [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Design Panel]] di bawah widget.

### Header Toolbar

| Elemen | Fungsi |
| --- | --- |
| Ikon linear (paling kiri) | Menandai jenis widget. |
| Ikon pegangan ⋮⋮ | Memindahkan widget ke posisi atau Layout lain. |
| [[^field\|Data]] | [[Docs/Tipe Data/Query]] untuk data yang ditampilkan widget. Klik [[^button/q]] untuk membuka konfigurasi [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Series Output]] |
| [[^button/delete\|Remove]] | Menghapus widget dari Canvas. Lihat [[#Menghapus Widget Chart Linear]]. |

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* pada widget dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]].

### Data Panel

Data Panel (ikon database) mengatur skala dan tampilan nilai:

| Pengaturan | Fungsi |
| --- | --- |
| [[^field\|min/max]] dan toggle [[^toggle/auto\|Auto]] | Batas bawah dan batas atas skala. Toggle Auto mengatur batas otomatis. Jika nonaktif, skala mengikuti nilai pada kolom min sampai kolom [[^field\|until]]. |
| [[^field\|value]] | Posisi nilai pada bar: `Inside`, `End`, `Above`, `Below`, atau `None`. |
| [[^field\|format]] | Format nilai: `Value`, `Percent`, atau `Custom`. |
| [[^field\|size]] | Ukuran nilai (contoh 13). |

### Design Panel

Design Panel (ikon palet) mengatur tampilan bar:

| Pengaturan | Fungsi |
| --- | --- |
| [[^field\|mode]] | Mode bar: `Bars`, `Multi`, atau `Stacked`. |
| Dropdown bentuk bar (contoh `Stepped`) | Bentuk bar: `Plain`, `Split`, atau `Stepped`. |
| [[^toggle\|diverging]] | Toggle mode diverging. |
| [[^toggle\|orientasi]] | Toggle orientasi. Aktif berarti horizontal. |
| [[^toggle\|show track]] | Toggle untuk menampilkan track. Jika aktif, tampil isian [[^field\|track]] berupa opacity track (contoh 20%) dan warna track. |
| [[^toggle\|show marker]] | Toggle untuk menampilkan marker. Jika aktif, tampil isian [[^field\|marker]] berupa *marker width* (contoh 2), *marker height* (contoh 14%), dan warna marker. |
| [[^field\|theme]] | Tema pewarnaan. Pilihan sama dengan theme pada [[Docs/Modul Interface/Canvas/Widget/Chart Line#Design Panel\|Chart Line]]. |
| Ikon opacity (contoh 100%) | *Bar opacity*, yaitu opacity bar. |
| Ikon radius (contoh 3) | *Bar border radius*, yaitu kelengkungan sudut bar. |
| [[^button/add\|+ threshold]] | Menambahkan titik threshold. Setelah ada threshold, tampil toggle legenda threshold dan daftar titik. Setiap titik memiliki input [[^field\|at]] (dalam persen), warna, dan tombol hapus. Nilai di atas persentase threshold berubah menjadi warna yang ditentukan. |
| Ikon step ticks (contoh 10) dan step gap (contoh 3) | Tampil jika bentuk bar adalah `Stepped`. *Step ticks* mengatur jumlah langkah pada bar dan *step gap* mengatur jarak antar langkah. |
| [[^field\|label]] | Posisi label: `start`, `end`, `above`, `below`, atau `none`. |
| [[^field\|size]] | Ukuran label (contoh 12). |
| Ikon bar gap (contoh 11) | Jarak antar bar. |
| [[^toggle/animation\|count up]] | Toggle untuk memberi animasi *count up* saat widget pertama kali dibuka. |

### Interaksi pada Widget Chart Linear

| Fungsi | Aksi |
| --- | --- |
| Melihat nilai data | Nilai tampil pada bar sesuai pengaturan [[^field\|value]] dan [[^field\|format]]. |

## Menghapus Widget Chart Linear

Langkah menghapus Widget Chart Linear sama dengan menghapus widget lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan
> Menghapus widget akan menghapus semua konfigurasi yang ada termasuk Query yang sudah dibuat. Data sumber dan barisnya tetap aman. Setelah terhapus, aksi tidak bisa dikembalikan.

## Praktik Terbaik

- **Atur [[^field|min/max]] agar skala sesuai.** Aktifkan Auto bila nilai berubah, atau tentukan min dan max untuk skala tetap.
- **Gunakan threshold untuk menandai batas.** Warna bar berubah ketika nilai melewati persentase threshold.
- **Letakkan nilai dengan [[^field|value]].** Pilih `End` atau `Inside` agar nilai tidak menutupi label, atau `None` bila tidak diperlukan.
- **Gunakan orientasi horizontal untuk nama kategori yang panjang.** Aktifkan toggle orientasi.
- **Aktifkan track untuk melihat bagian yang belum terisi.** Atur opacity track agar tidak mengalahkan bar.
- **Pastikan Query mengikuti kaidah [[Docs/Tipe Data/Query#Series Output|Series Output]].** Query yang tidak sesuai membuat bar tidak tampil dengan benar.

## TL:DR

- Widget Chart Linear menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai bar linear di [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]].
- Tambahkan melalui [[^field|Type something here to add...]] dengan perintah `/chart linear` pada Edit Mode. Lihat [[#Menambahkan Widget Chart Linear]].
- Header Toolbar berisi [[^field|Data]] dan [[^button/q]]. Panel di bawah widget: Layout Panel, Data Panel, dan Design Panel. Lihat [[#Antarmuka Widget Chart Linear]].
- Data Panel mengatur [[^field|min/max]], [[^field|value]], [[^field|format]], dan [[^field|size]].
- Design Panel mengatur mode, bentuk bar, orientasi, track, marker, tema, threshold, [[^field|label]], dan animasi count up.
- Menghapus widget tidak menghapus data sumber.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Query seperti apa yang dipakai Widget Chart Linear?**
> Query harus mengikuti kaidah [[Docs/Tipe Data/Query#Series Output|Series Output]]. Atur melalui [[^button/q]] pada Header Toolbar.
> **Apa saja mode dan bentuk bar?**
> Mode: `Bars`, `Multi`, dan `Stacked`. Bentuk: `Plain`, `Split`, dan `Stepped`.
> **Kapan input step ticks dan step gap tampil?**
> Saat bentuk bar adalah `Stepped`.
> **Bagaimana threshold bekerja?**
> Klik [[^button/add|+ threshold]] untuk menambah titik. Setiap titik memiliki [[^field|at]] dalam persen dan warna. Nilai di atas persentase threshold berubah menjadi warna tersebut.
> **Kapan isian track dan marker tampil?**
> Isian track tampil bila toggle show track aktif, dan isian marker tampil bila toggle show marker aktif.
> **Apa pilihan posisi nilai dan label?**
> [[^field|value]]: `Inside`, `End`, `Above`, `Below`, `None`. [[^field|label]]: `start`, `end`, `above`, `below`, `none`.
> **Bagaimana membuat bar vertikal?**
> Nonaktifkan toggle orientasi. Jika aktif, bar horizontal.
> **Apakah menghapus widget menghapus data sumber?**
> Tidak. Menghapus widget hanya menghapus tampilan dan konfigurasinya, termasuk [[Docs/Tipe Data/Query|Query]]. Data sumber tetap aman.


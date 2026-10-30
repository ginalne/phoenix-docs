---
status: draft
title: Widget Chart Radial
description: Widget Chart Radial menampilkan data Table sebagai bar melingkar dengan needle, ruler, threshold, dan animasi pada Canvas.
---
# Widget Chart Radial

>**note** Widget Chart Radial merupakan salah satu widget pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Daftar widget lainnya ada di [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget Canvas]].

Widget Chart Radial adalah [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai bar melingkar di dalam [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Data diambil melalui [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Series Output]], sedangkan arah needle diambil dari Query terpisah yang mengikuti kaidah [[Docs/Tipe Data/Query#Single Output]].

Anda dapat mengatur ruler, batas nilai, bentuk lengkungan, ketebalan, threshold, track, needle, legenda, dan animasi melalui Data Panel dan Design Panel.

## Menambahkan Widget Chart Radial

Ketik `/chart radial` dalam [[^field|Type something here to add...]] untuk menampilkan variasi lalu pilih salah satunya. Langkah lengkapnya ada di [[Docs/Modul Interface/Canvas/Widget/Menambahkan|Menambahkan Widget]].

## Antarmuka Widget Chart Radial

![[Docs/Modul Interface/Form/Widget/Chart Radial/interface-widget-chart-radial.png]]
Pada [[^mode/edit|Edit]], klik kiri widget untuk menampilkan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar]] di atas widget, serta [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]], [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Data Panel]], [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Design Panel]] di bawah widget.

### Header Toolbar

| Elemen | Fungsi |
| --- | --- |
| Ikon radial (paling kiri) | Menandai jenis widget. |
| Ikon pegangan ⋮⋮ | Memindahkan widget ke posisi atau Layout lain. |
| [[^field|Needle]] | [[Docs/Tipe Data/Query]] untuk nilai arah needle. Klik [[^button/q]] di sebelah kanannya untuk membuka konfigurasi [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Single Output]]. Menampilkan [[^field|Empty]] bila belum diisi. |
| [[^field|Data]] | [[Docs/Tipe Data/Query]] untuk data yang ditampilkan widget. Klik [[^button/q]] untuk membuka konfigurasi [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Series Output]] |
| [[^button/delete|Remove]] | Menghapus widget dari Canvas. Lihat [[#Menghapus Widget Chart Radial]]. |

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* pada widget dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]].

### Data Panel

Data Panel (ikon database) mengatur skala dan tampilan nilai:

| Pengaturan | Fungsi |
| --- | --- |
| [[^field|ruler]] | Toggle untuk menampilkan atau menyembunyikan ruler. |
| [[^field|ticks]] | Banyaknya tick pada ruler, dilengkapi pilihan warna tick. |
| [[^field|min/max]] dan toggle [[^toggle/auto|Auto]] | Batas bawah dan batas atas skala. Toggle Auto mengatur batas otomatis. Jika nonaktif, skala mengikuti nilai pada kolom min sampai kolom [[^field|until]]. |
| [[^field|label]] | Label dari nilai needle. Isi untuk mengganti label bawaan. |
| [[^field|value]] | Tampilan nilai: `Value`, `Percent`, `Ratio`, atau `None`. |
| Ukuran dan warna teks (contoh 100%) | Ukuran (0 sampai 100%) dan warna teks label. |

### Design Panel

Design Panel (ikon palet) mengatur tampilan bar, track, dan needle:

| Pengaturan | Fungsi |
| --- | --- |
| [[^field|mode]] | Mode bar: `Multi` atau `Stacked`. |
| Dropdown bentuk lengkungan (contoh `Horseshoe`) | Bentuk lengkungan: `Full`, `Semi`, `Horseshoe`, `Fan`, atau `Custom`. Pilihan `Custom` menampilkan input tambahan dari derajat awal (from°) sampai derajat akhir (to°). |
| Ikon ketebalan (contoh 25) | *Thickness*, yaitu ketebalan bar. Nilai bawaan 25. |
| [[^field|arc]] | Bentuk ujung bar: `Round`, `Square`, atau `Butt`. |
| [[^field|style]] | Tema pewarnaan. Pilihan sama dengan theme pada [[Docs/Modul Interface/Canvas/Widget/Chart Line#Design Panel|Chart Line]]. |
| Ikon opacity (contoh 100%) | Opacity bar. |
| Ikon arc gap (contoh 17) | Jarak antar arc. |
| [[^button/add|+ threshold]] | Menambahkan titik threshold. Setiap titik memiliki input [[^field|at]] (dalam persen) dan warna. Nilai di atas persentase threshold berubah menjadi warna yang ditentukan. |
| [[^field|track]] | Warna track (contoh abu-abu), dengan ikon opacity track di sebelahnya (contoh 15%). |
| [[^field|needle]] | Warna needle (contoh hitam), dengan ikon panjang needle di sebelahnya (contoh 120%). Panjang dihitung dari persentase ruang di tengah. Nilai 120% membuat needle mengenai bar. |
| [[^toggle/legends|Legends]] | Toggle untuk menampilkan atau menyembunyikan legenda. |
| [[^toggle/animation|Animation at start]] | Toggle untuk memberi animasi needle saat widget pertama kali dibuka. |

### Interaksi pada Widget Chart Radial

| Fungsi | Aksi |
| --- | --- |
| Melihat nilai data | Nilai setiap data tampil pada legenda di tengah chart bila toggle [[^toggle/legends|Legends]] aktif. |

## Menghapus Widget Chart Radial

Langkah menghapus Widget Chart Radial sama dengan menghapus widget lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan
> Menghapus widget akan menghapus semua konfigurasi yang ada termasuk Query yang sudah dibuat. Data sumber dan barisnya tetap aman. Setelah terhapus, aksi tidak bisa dikembalikan.

## Praktik Terbaik

- **Atur [[^field|min/max]] agar skala sesuai.** Aktifkan Auto bila nilai berubah, atau tentukan min dan max untuk skala tetap.
- **Gunakan threshold untuk menandai batas.** Tambahkan titik threshold dengan persentase dan warna agar nilai tinggi langsung terlihat.
- **Aktifkan [[^field|ruler]] untuk membaca nilai.** Atur [[^field|ticks]] agar skala tidak terlalu padat.
- **Gunakan needle bila ada nilai acuan tunggal.** Isi [[^field|Needle]] dengan Query yang mengikuti kaidah Single Output.
- **Sesuaikan panjang needle.** Nilai 120% membuat needle mengenai bar.
- **Pastikan Query mengikuti kaidah [[Docs/Tipe Data/Query#Series Output|Series Output]].** Query yang tidak sesuai membuat bar tidak tampil dengan benar.

## TL:DR

- Widget Chart Radial menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai bar melingkar di [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]].
- Tambahkan melalui [[^field|Type something here to add...]] dengan perintah `/chart radial` pada Edit Mode. Lihat [[#Menambahkan Widget Chart Radial]].
- Header Toolbar berisi [[^field|Needle]] (Query Single Output), [[^field|Data]] (Query Series Output), dan [[^button/delete|Remove]]. Lihat [[#Antarmuka Widget Chart Radial]].
- Data Panel mengatur [[^field|ruler]], [[^field|ticks]], [[^field|min/max]], [[^field|label]], dan [[^field|value]].
- Design Panel mengatur mode, bentuk lengkungan, ketebalan, [[^field|arc]], tema, threshold, [[^field|track]], [[^field|needle]], legenda, dan animasi.
- Menghapus widget tidak menghapus data sumber.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Query seperti apa yang dipakai Widget Chart Radial?**
> Ada dua Query. [[^field|Data]] mengikuti kaidah [[Docs/Tipe Data/Query#Series Output|Series Output]], dan [[^field|Needle]] mengikuti kaidah [[Docs/Tipe Data/Query#Single Output|Single Output]] untuk nilai arah needle.
> **Apa fungsi Needle?**
> Needle adalah penunjuk nilai tunggal pada chart. Nilainya diambil dari Query pada [[^field|Needle]]. Menampilkan [[^field|Empty]] bila belum diisi.
> **Apa saja bentuk lengkungan?**
> `Full`, `Semi`, `Horseshoe`, `Fan`, dan `Custom`. Pada `Custom` Anda mengisi derajat awal (from°) dan derajat akhir (to°).
> **Bagaimana threshold bekerja?**
> Klik [[^button/add|+ threshold]] untuk menambah titik. Setiap titik memiliki [[^field|at]] dalam persen dan warna. Nilai di atas persentase threshold berubah menjadi warna tersebut.
> **Apa pilihan tampilan nilai?**
> [[^field|value]]: `Value`, `Percent`, `Ratio`, atau `None`.
> **Apa fungsi animation at start?**
> Memberi animasi needle saat widget pertama kali dibuka.
> **Apakah menghapus widget menghapus data sumber?**
> Tidak. Menghapus widget hanya menghapus tampilan dan konfigurasinya, termasuk [[Docs/Tipe Data/Query|Query]]. Data sumber tetap aman.


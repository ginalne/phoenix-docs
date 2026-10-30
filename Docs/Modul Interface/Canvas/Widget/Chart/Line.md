---
status: draft
title: Widget Chart Line
description: Widget Chart Line menampilkan data Table sebagai grafik garis dengan area, titik data, dan sumbu yang dapat diatur pada Canvas.
---
# Widget Chart Line

>**note** Widget Chart Line merupakan salah satu widget pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Daftar widget lainnya ada di [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget Canvas]].

Widget Chart Line adalah [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai grafik garis di dalam [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Data diambil melalui [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Series Output]], lalu setiap data digambarkan sebagai garis, titik, dan area pada sumbu X dan Y.

Anda dapat mengatur sumbu X, Y, dan Y2, jenis dan ketebalan garis, titik, grid, zoom, tema warna, area, dan legenda melalui Data Panel dan Design Panel.

## Menambahkan Widget Chart Line

Ketik `/chart line` dalam [[^field|Type something here to add...]] untuk menampilkan variasi lalu pilih salah satunya. Langkah lengkapnya ada di [[Docs/Modul Interface/Canvas/Widget/Menambahkan|Menambahkan Widget]].

## Antarmuka Widget Chart Line

![[Docs/Modul Interface/Form/Widget/Chart Line/interface-widget-chart-line.png]]
Pada [[^mode/edit|Edit]], klik kiri widget untuk menampilkan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar]] di atas widget, serta [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]], [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Data Panel]], [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Design Panel]] di bawah widget.

### Header Toolbar

| Elemen | Fungsi |
| --- | --- |
| Ikon garis (paling kiri) | Menandai jenis widget. |
| Ikon pegangan ⋮⋮ | Memindahkan widget ke posisi atau Layout lain. |
| [[^field\|Data]] | [[Docs/Tipe Data/Query]] untuk data yang ditampilkan widget. Klik [[^button/q]] untuk membuka konfigurasi [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Series Output]] |
| [[^button/delete\|Remove]] | Menghapus widget dari Canvas. Lihat [[#Menghapus Widget Chart Line]]. |

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* pada widget dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]].

### Data Panel

Data Panel (ikon database) mengatur tiga sumbu chart: X, Y, dan Y2. Setiap sumbu memiliki konfigurasi berikut:

| Pengaturan | Fungsi |
| --- | --- |
| [[^field\|min/max]] dan toggle [[^toggle/auto\|A]] | Batas bawah dan batas atas sumbu. Toggle A mengatur batas otomatis. Jika nonaktif, sumbu mengikuti nilai pada kolom awal sampai kolom [[^field\|until]]. Kolom yang dikosongkan berarti auto. |
| Ikon label (tag) | Toggle untuk menggunakan label pada sumbu. |
| [[^field\|tick]] | Banyaknya label pada sumbu. |
| [[^field\|format]] | Penulisan label. Kosong berarti default. |
| [[^toggle\|Y2]] | Sumbu Y kedua (sisi kanan) dengan isi konfigurasi yang sama dengan sumbu Y. |

### Design Panel

Design Panel (ikon palet) mengatur tampilan garis dan chart:

| Pengaturan | Fungsi |
| --- | --- |
| Ikon ketebalan garis (contoh 2.5) | Ketebalan garis. |
| Dropdown jenis garis (contoh `smooth`) | Jenis garis: `smooth`, `sharp`, atau `step`. |
| Ikon titik (contoh 4) | *Dot radius*, yaitu radius titik data. |
| [[^toggle/zoom\|Zoom]] (ikon kaca pembesar) | Toggle untuk mengaktifkan interaksi zoom in dan zoom out pada chart. |
| [[^toggle/grid\|Grid]] (ikon grid) | Toggle untuk menampilkan grid. |
| [[^field\|theme]] | Tema pewarnaan: `monochrome`, `phoenix`, `fun`, `classy`, `futuristic`, `elegant`, `aurora`, `forest`, `royal`, `obsidian`, `celestial`, `volcanic`, `lotus`, `cyberpunk`, `desert`. |
| [[^field\|area]] | Persentase opacity area di bawah garis. |
| [[^field\|legends]] | Posisi legenda: `right`, `bottom`, `left`, `top`, atau `hidden`. |

### Interaksi pada Widget Chart Line

| Fungsi | Aksi |
| --- | --- |
| Melihat nilai data | Arahkan kursor ke titik pada chart. Tooltip menampilkan waktu dan nilai data. |
| Zoom in dan zoom out | Aktifkan toggle [[^toggle/zoom\|Zoom]], lalu gunakan interaksi zoom pada chart. |

## Menghapus Widget Chart Line

Langkah menghapus Widget Chart Line sama dengan menghapus widget lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan
> Menghapus widget akan menghapus semua konfigurasi yang ada termasuk Query yang sudah dibuat. Data sumber dan barisnya tetap aman. Setelah terhapus, aksi tidak bisa dikembalikan.

## Praktik Terbaik

- **Gunakan batas otomatis untuk data yang berubah.** Aktifkan toggle [[^toggle/auto|A]] agar skala mengikuti data, dan nonaktifkan bila ingin skala tetap.
- **Pilih jenis garis sesuai data.** `smooth` untuk tren yang halus, `sharp` untuk garis lurus antar titik, dan `step` untuk perubahan bertahap.
- **Atur [[^field|tick]] agar label tidak menumpuk.** Kurangi jumlah label bila sumbu terlalu padat.
- **Atur [[^field|area]] agar garis tetap menonjol.** Opacity area yang rendah membuat garis lebih jelas.
- **Sesuaikan [[^field|legends]] dengan ruang.** Gunakan `hidden` pada widget kecil.
- **Pastikan Query mengikuti kaidah [[Docs/Tipe Data/Query#Series Output|Series Output]].** Query yang tidak sesuai membuat garis tidak tampil dengan benar.

## TL:DR

- Widget Chart Line menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai grafik garis di [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]].
- Tambahkan melalui [[^field|Type something here to add...]] dengan perintah `/chart line` pada Edit Mode. Lihat [[#Menambahkan Widget Chart Line]].
- Header Toolbar berisi [[^field|Data]] dan [[^button/q]]. Panel di bawah widget: Layout Panel, Data Panel, dan Design Panel. Lihat [[#Antarmuka Widget Chart Line]].
- Data Panel mengatur sumbu X, Y, dan Y2 lewat [[^field|min/max]], [[^field|tick]], dan [[^field|format]].
- Design Panel mengatur garis, titik, zoom, grid, [[^field|theme]], [[^field|area]], dan [[^field|legends]].
- Menghapus widget tidak menghapus data sumber.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Query seperti apa yang dipakai Widget Chart Line?**
> Query harus mengikuti kaidah [[Docs/Tipe Data/Query#Series Output|Series Output]]. Atur melalui [[^button/q]] pada Header Toolbar.
> **Apa arti toggle A pada min/max?**
> Toggle [[^field|A]] mengatur batas bawah dan batas atas sumbu secara otomatis. Jika nonaktif, sumbu mengikuti nilai [[^field|min/max]] sampai [[^field|until]]. Kolom yang dikosongkan berarti auto.
> **Bagaimana mengatur jumlah label pada sumbu?**
> Atur [[^field|tick]] pada sumbu yang bersangkutan. Penulisan label diatur lewat [[^field|format]], dan kosong berarti default.
> **Apa fungsi ikon kaca pembesar?**
> Toggle untuk mengaktifkan interaksi zoom in dan zoom out pada chart.
> **Apa saja pilihan theme dan legends?**
> [[^field|theme]]: `monochrome`, `phoenix`, `fun`, `classy`, `futuristic`, `elegant`, `aurora`, `forest`, `royal`, `obsidian`, `celestial`, `volcanic`, `lotus`, `cyberpunk`, `desert`. [[^field|legends]]: `right`, `bottom`, `left`, `top`, atau `hidden`.
> **Apa fungsi area?**
> [[^field|area]] mengatur persentase opacity area di bawah garis.
> **Apakah menghapus widget menghapus data sumber?**
> Tidak. Menghapus widget hanya menghapus tampilan dan konfigurasinya, termasuk [[Docs/Tipe Data/Query|Query]]. Data sumber tetap aman.

<!--
  * [TODO] Screenshot menampilkan nama Table dan nama data pribadi (misalnya "Catatan ..." dan nama status). Mohon ganti dengan data generik pada gambar bila perlu.
  * [TODO] Nama slug ikon untuk toggle dan tombol tanpa label (zoom, grid, tag, A, Auto, dan sebagainya) adalah tebakan. Mohon sesuaikan dengan nama ikon yang sebenarnya.
  * [TODO] Kaidah Query Chart Line diasumsikan Series Output (legend pada gambar memakai agregasi COUNT). Mohon konfirmasi.
  * [TODO] Penulis menyebut Data Panel Chart Line kemungkinan akan diganti seperti Chart Bar (label sumbu, Auto, dan sebagainya). Halaman ini mengikuti screenshot saat ini (toggle A, ikon label, tick, format). Perbarui setelah panel diganti.
  * [TODO] Konfirmasi: tombol Y2 menampilkan atau mengaktifkan sumbu Y kedua (pada Chart Line nonaktif, pada Chart Bar aktif dan sumbu kanan tampil).
  * [TODO] Konfirmasi gestur zoom (scroll, drag, atau tombol) serta isi tooltip.
  * [TODO] Halaman baru yang diusulkan: `Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Data Panel` (anchor baru untuk Data Panel), serta `Docs/Tipe Data/Query#Series Output`.
-->
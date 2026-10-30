---
    status: release
    title: Widget Chart Bar
    description: Widget Chart Bar menampilkan data Table sebagai grafik batang dengan mode, pola, dan label nilai yang dapat diatur pada Canvas.
    pageDecoration:
      tree:
        priority: 0
---
# Widget Chart Bar

>**note** Widget Chart Bar merupakan salah satu widget pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Daftar widget lainnya ada di [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget Canvas]].

Widget Chart Bar adalah [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai grafik batang di dalam [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Data diambil melalui [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Series Output]], lalu setiap data digambarkan sebagai batang pada sumbu X dan Y.

Anda dapat mengatur sumbu X, Y, dan Y2, mode dan orientasi batang, tema warna, pola, marker, label nilai, dan legenda melalui Data Panel dan Design Panel.

## Menambahkan Widget Chart Bar

Ketik `/chart bar` dalam [[^field|Type something here to add...]] untuk menampilkan variasi lalu pilih salah satunya. Langkah lengkapnya ada di [[Docs/Modul Interface/Canvas/Widget/Menambahkan|Menambahkan Widget]].

## Antarmuka Widget Chart Bar

![[Docs/Modul Interface/Form/Widget/Chart Bar/interface-widget-chart-bar.png]]
Pada [[^mode/edit|Edit]], klik kiri widget untuk menampilkan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar]] di atas widget, serta [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]], [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Data Panel]], [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Design Panel]] di bawah widget.

### Header Toolbar

| Elemen | Fungsi |
| --- | --- |
| Ikon batang (paling kiri) | Menandai jenis widget. |
| Ikon pegangan ⋮⋮ | Memindahkan widget ke posisi atau Layout lain. |
| [[^field|Data]] | [[Docs/Tipe Data/Query]] untuk data yang ditampilkan widget. Klik [[^button/q]] untuk membuka konfigurasi [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Series Output]] |
| [[^button/delete|Remove]] | Menghapus widget dari Canvas. Lihat [[#Menghapus Widget Chart Bar]]. |

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* pada widget dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]].

### Data Panel

Data Panel (ikon database) mengatur tiga sumbu chart: X, Y, dan Y2.

| Pengaturan | Fungsi |
| --- | --- |
| [[^field|X]] | Sumbu X. Hanya memiliki [[^field|label]] untuk mengganti label sumbu. |
| [[^field|Y]] | Sumbu Y. Memiliki [[^field|min/max]] dengan toggle Auto, [[^field|label]], [[^field|tick]], dan [[^field|format]]. |
| [[^toggle|Y2]] | Sumbu Y kedua (sisi kanan). Isi konfigurasinya sama dengan sumbu Y. |
| [[^field|min/max]] dan toggle [[^toggle/auto|Auto]] | Batas bawah dan batas atas sumbu. Toggle Auto mengatur batas otomatis. Jika nonaktif, sumbu mengikuti nilai pada kolom awal sampai kolom [[^field|until]]. |
| [[^field|label]] | Label sumbu. Isi untuk mengganti label bawaan. |
| [[^field|tick]] | Banyaknya label pada sumbu. |
| [[^field|format]] | Penulisan label. Kosong berarti default. |

### Design Panel

Design Panel (ikon palet) mengatur tampilan batang:

| Pengaturan | Fungsi |
| --- | --- |
| [[^toggle|diverging]], [[^toggle|reversed]], [[^toggle|orientasi]] | Tiga toggle pada baris [[^field|mode]]: mode diverging, mode reversed, dan orientasi batang. Orientasi nonaktif berarti vertikal. |
| Radio button mode batang | Pilihan `Grouped`, `Stacked`, atau `Full`. |
| [[^field|theme]] | Tema pewarnaan: `monochrome`, `phoenix`, `fun`, `classy`, `futuristic`, `elegant`, `aurora`, `forest`, `royal`, `obsidian`, `celestial`, `volcanic`, `lotus`, `cyberpunk`, `desert`. |
| Ikon opacity (contoh 90%) | *Bar opacity*, yaitu opacity batang. |
| Ikon radius (contoh 4) | *Bar border radius*, yaitu kelengkungan sudut batang. |
| [[^field|p]] | *Bar padding*, yaitu jarak antar batang (contoh 0.25%). |
| [[^field|marker]] | Pengaturan marker: warna marker, *marker length* (contoh 70%), dan *marker width* (contoh 3). |
| [[^field|pattern]] | Pola pada batang: `off`, `basic`, `all`, atau `series`. `basic` memakai pola garis-garis. `all` menerapkan satu pola ke semua batang dengan pilihan `Hatch`, `Dots`, `Cross`, atau `ZigZag`. `series` menentukan pola menurut urutan series, dan tombol [[^button/add|+]] menambahkan urutan. |
| [[^field|legends]] | Posisi legenda: `right`, `bottom`, `left`, `top`, atau `hidden`. |
| [[^toggle/zoom]] (ikon kaca pembesar) | Toggle untuk mengaktifkan interaksi zoom pada chart. |
| [[^toggle/grid|Grid]] (ikon grid) | Toggle untuk menampilkan grid. |
| [[^toggle/123]] | Toggle untuk menampilkan label nilai di atas batang. |
| [[^field|size]] | Ukuran font label nilai (contoh 11). |

### Interaksi pada Widget Chart Bar

| Fungsi | Aksi |
| --- | --- |
| Melihat nilai data | Aktifkan toggle [[^toggle/123|123]] untuk menampilkan label nilai di atas batang. |
| Zoom | Aktifkan toggle [[^toggle/zoom|Zoom]], lalu gunakan interaksi zoom pada chart. |

## Menghapus Widget Chart Bar

Langkah menghapus Widget Chart Bar sama dengan menghapus widget lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan
> Menghapus widget akan menghapus semua konfigurasi yang ada termasuk Query yang sudah dibuat. Data sumber dan barisnya tetap aman. Setelah terhapus, aksi tidak bisa dikembalikan.

## Praktik Terbaik

- **Gunakan mode batang sesuai tujuan.** `Grouped` untuk membandingkan series berdampingan, `Stacked` untuk melihat total, dan `Full` untuk komposisi penuh.
- **Tampilkan nilai dengan [[^field|123]].** Aktifkan label nilai dan atur [[^field|size]] agar angka mudah dibaca.
- **Gunakan [[^field|pattern]] agar series mudah dibedakan.** Berguna untuk tampilan cetak atau satu warna.
- **Atur [[^field|tick]] dan [[^field|min/max]] agar skala jelas.** Matikan Auto bila ingin skala tetap antar chart.
- **Gunakan orientasi horizontal untuk nama kategori yang panjang.** Aktifkan toggle orientasi.
- **Pastikan Query mengikuti kaidah [[Docs/Tipe Data/Query#Series Output|Series Output]].** Query yang tidak sesuai membuat batang tidak tampil dengan benar.

## TL:DR

- Widget Chart Bar menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai grafik batang di [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]].
- Tambahkan melalui [[^field|Type something here to add...]] dengan perintah `/chart bar` pada Edit Mode. Lihat [[#Menambahkan Widget Chart Bar]].
- Header Toolbar berisi [[^field|Data]] dan [[^button/q]]. Panel di bawah widget: Layout Panel, Data Panel, dan Design Panel. Lihat [[#Antarmuka Widget Chart Bar]].
- Data Panel mengatur sumbu X, Y, dan Y2 (label, [[^field|min/max]], [[^field|tick]], [[^field|format]]).
- Design Panel mengatur mode batang, orientasi, [[^field|style]], opacity, radius, [[^field|pattern]], marker, [[^field|legends]], zoom, grid, dan label nilai.
- Menghapus widget tidak menghapus data sumber.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Query seperti apa yang dipakai Widget Chart Bar?**
> Query harus mengikuti kaidah [[Docs/Tipe Data/Query#Series Output|Series Output]]. Atur melalui [[^button/q]] pada Header Toolbar.
> **Apa saja mode batang?**
> `Grouped`, `Stacked`, dan `Full`, dipilih lewat radio button pada baris [[^field|mode]]. Toggle diverging, reversed, dan orientasi dapat dikombinasikan.
> **Bagaimana membuat batang horizontal?**
> Aktifkan toggle orientasi. Jika nonaktif, batang vertikal.
> **Apa saja pilihan pattern?**
> [[^field|pattern]]: `off`, `basic` (garis-garis), `all` (`Hatch`, `Dots`, `Cross`, `ZigZag`), dan `series` (pola per series, tambah urutan dengan [[^button/add|+]]).
> **Bagaimana menampilkan nilai di atas batang?**
> Aktifkan toggle [[^field|123]], lalu atur ukuran font dengan [[^field|size]].
> **Apa fungsi Y2?**
> Y2 adalah sumbu Y kedua di sisi kanan chart dengan konfigurasi yang sama dengan sumbu Y.
> **Apakah menghapus widget menghapus data sumber?**
> Tidak. Menghapus widget hanya menghapus tampilan dan konfigurasinya, termasuk [[Docs/Tipe Data/Query|Query]]. Data sumber tetap aman.


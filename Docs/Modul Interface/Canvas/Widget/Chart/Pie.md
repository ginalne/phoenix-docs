---
    status: draft
    title: Widget Chart Pie
    description: Widget Chart Pie menampilkan data Table sebagai diagram pie pada Canvas, lengkap dengan pengaturan lubang, warna, label, legenda, dan total.
---
# Widget Chart Pie

>**note** Widget Chart Pie merupakan salah satu widget pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Daftar widget lainnya ada di [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget Canvas]].

Widget Chart Pie adalah [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai diagram pie di dalam [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Data diambil melalui [[Docs/Tipe Data/Query]] yang mengikuti kaidah [[Docs/Tipe Data/Query#Series Output]], lalu setiap data menjadi satu irisan pie.

Anda dapat mengatur jumlah data yang muncul, bentuk pie, warna, label, legenda, dan total di tengah pie melalui header toolbar dan design toolbar.

## Menambahkan Widget Chart Pie

Ketik `/chart pie` dalam [[^field|Type something here to add...]] untuk menampilkan variasi lalu pilih salah satunya. Langkah lengkapnya ada di [[Docs/Modul Interface/Canvas/Widget/Menambahkan|Menambahkan Widget]].

## Antarmuka Widget Chart Pie

![[Docs/Modul Interface/Form/Widget/Chart Pie/interface-widget-chart-pie.png]]

Pada [[^mode/edit|Edit]], klik kiri widget untuk menampilkan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar]] di atas widget, [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]] dan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Design Panel]] di bawah widget.

### Header Toolbar

| Elemen                                    | Fungsi                                                                                                                         |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Ikon Table (paling kiri)                  | Menandai jenis widget.                                                                                                         |
| Ikon pegangan ⋮⋮                          | Memindahkan widget ke posisi atau Layout lain.                                                                                 |
| [[^toggle|123]]                          | Toggle pagination. Menampilkan atau menyembunyikan bilah pagination di bagian bawah widget.                                    |
| [[^toggle/search|Search]] (ikon kaca pembesar) | Toggle toolbar search. Memunculkan atau menyembunyikan toolbar search di bagian atas widget.                                   |
| [[^field|Data]]                      | [[Docs/Tipe Data/Query]] untuk data yang ditampilkan widget. Klik [[^button/q]] untuk membuka konfigurasi [[Docs/Tipe Data/Query]] yang mengikuti kaidah  [[Docs/Tipe Data/Query#Series Output]].  |
| [[^field|Limit]]                         | Jumlah maksimal data yang muncul pada pie. Menampilkan [[^field|Empty]] bila belum diisi.                                     |
| [[^button/delete|Remove]]                | Menghapus widget dari Canvas. Lihat [[#Menghapus Widget Table]].                                                               |

Tombol toggle yang aktif ditandai dengan latar berwarna.

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* pada widget dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]].

## Design toolbar

| Pengaturan                  | Fungsi                                                                                                                                                         |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[^field|hole]]            | Besar lubang di tengah pie, dalam persen.                                                                                                                      |
| [[^field|gap]]             | Jarak antar data (antar irisan).                                                                                                                               |
| [[^field|theme]]           | Tema warna pie.                                                                                                                                                |
| [[^field|gradient]]        | Gradasi warna dari tengah ke pinggir (dari transparan ke warna), dalam persen.                                                                                 |
| [[^field|offset]]          | Batas akhir gradasi. Jika 75%, gradasi berjalan dari tengah sampai sekitar 75% ke ujung lingkaran.                                                             |
| [[^field|label]]           | Isi label di dalam pie: `none`, `label`, `value`, `percent`, atau `all` (label - value).                                                                       |
| [[^field|min]]             | Derajat minimum irisan agar label ditampilkan.                                                                                                                 |
| [[^field|legends]]         | Posisi legenda: `right`, `bottom`, atau `hidden`.                                                                                                              |
| [[^field|total]]           | Toggle untuk menampilkan total di tengah pie.                                                                                                                  |
| [[^field|size]]            | Ukuran font total yang tampil di tengah pie.                                                                                                                   |

## Menghapus Widget Table

Langkah menghapus Widget Table sama dengan menghapus widget lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan
> Menghapus widget akan menghapus semua konfigurasi yang ada termasuk Query yang sudah dibuat. Data sumber dan barisnya tetap aman. Setelah terhapus, aksi tidak bisa dikembalikan..

## Praktik Terbaik

- **Isi [[^field|Limit]] agar pie tidak terlalu padat.** Batasi jumlah data yang muncul supaya irisan tetap terbaca.
- **Atur [[^field|label]] sesuai kebutuhan.** Gunakan `percent` untuk komposisi, `value` untuk jumlah, atau `none` bila tampilan ingin bersih.
- **Atur [[^field|min]] untuk irisan kecil.** Label hanya tampil pada irisan yang cukup besar sehingga tidak menumpuk.
- **Sesuaikan [[^field|legends]] dengan ruang.** Gunakan `hidden` pada widget kecil, `bottom` untuk widget lebar.
- **Aktifkan [[^field|total]] untuk ringkasan.** Total di tengah memudahkan pembaca melihat jumlah keseluruhan.
- **Pastikan Query mengikuti kaidah [[Docs/Tipe Data/Query#Series Output|Series Output]].** Query yang tidak sesuai membuat pie tidak tampil dengan benar.

## TL:DR

- Widget Chart Pie menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai diagram pie di [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]].
- Tambahkan melalui [[^field|Type something here to add...]] dengan perintah `/chart` pada Edit Mode. Lihat [[#Menambahkan Widget Chart Pie]].
- Header toolbar berisi [[^field|Data]], [[^button/q]], [[^field|Limit]], dan [[^button/delete|Remove]]. Design toolbar berisi panel tata letak dan panel tampilan. Lihat [[#Antarmuka Widget Chart Pie]].
- Query harus mengikuti kaidah [[Docs/Tipe Data/Query#Series Output|Series Output]], dan [[^field|Limit]] membatasi jumlah data yang muncul.
- Atur tampilan lewat [[^field|hole]], [[^field|gap]], [[^field|theme]], [[^field|gradient]], [[^field|offset]], [[^field|label]], [[^field|min]], [[^field|legends]], [[^field|total]], dan [[^field|size]]. Lihat  [[#Design toolbar]].
- Menghapus widget tidak menghapus data sumber, dan semua perubahan mengikuti Data Access Canvas.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Query seperti apa yang dipakai Widget Chart Pie?**
> Query harus mengikuti kaidah [[Docs/Tipe Data/Query#Series Output|Series Output]]. Atur melalui [[^button/q]] pada header toolbar.
> **Apa fungsi Limit?**
> [[^field|Limit]] menentukan jumlah maksimal data yang muncul pada pie. Menampilkan [[^field|Empty]] bila belum diisi.
> **Apa bedanya gradient dan offset?**
> [[^field|gradient]] mengatur gradasi warna dari tengah ke pinggir (dari transparan ke warna), sedangkan [[^field|offset]] mengatur batas akhir gradasi. Jika [[^field|offset]] 75%, gradasi berjalan dari tengah sampai sekitar 75% ke ujung lingkaran.
> **Mengapa label tidak muncul pada irisan kecil?**
> [[^field|min]] adalah derajat minimum irisan agar label tampil. Irisan yang lebih kecil dari nilai tersebut tidak menampilkan label.
> **Bagaimana menampilkan atau menyembunyikan legenda?**
> Atur [[^field|legends]] ke `right`, `bottom`, atau `hidden`.
> **Bagaimana menampilkan total di tengah pie?**
> Aktifkan toggle [[^field|total]], lalu atur ukuran font dengan [[^field|size]].
> **Apakah menghapus widget menghapus data sumber?**
> Tidak. Menghapus widget hanya menghapus tampilan dan konfigurasinya, termasuk [[Docs/Tipe Data/Query|Query]]. Table sumber tetap aman.
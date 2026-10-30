---
    status: release
    title: "Antarmuka Table View"
    description: Penjelasan antarmuka di halaman kerja komponen Table View
    pageDecoration:
      tree:
        priority: 0
---
# Antarmuka Table View

![[Docs/Modul Interface/Table View/interface-tableview.png]]
Halaman kerja Table View terdiri dari bilah navigasi di bagian atas dan area Data di bagian bawah. Setiap Data tampil sebagai tabel yang dapat dilipat, dan Data baru ditambahkan lewat tombol [[^button/add|Add Data]] di bagian paling bawah.

Contoh gambar diatas merupakan halaman kerja Table View dengan dua Data bernama [[^field|On Progress...]] dan [[^field|Done belum diambil]].

## Bilah navigasi Table View

Bilah navigasi pada halaman kerja Table View terdiri dari:

| Elemen | Fungsi |
| ------ | ------ |
| Judul | Menampilkan ikon Table View dan [[^field|Header Name]]. |
| [[^button/edit|Edit]] | Mengubah atribut Table View. |
| [[^button/refresh|Refresh]] | Memuat ulang tampilan dan menjalankan kembali [[Docs/Tipe Data/Query]] pada setiap Data, sehingga [[Docs/Tipe Data/Row]] yang tidak lagi memenuhi syarat Query tidak ditampilkan lagi. |
| [[^field|Search TableView Data...]] | Mencari kata kunci di semua kolom pada Data. |

## Area Data Table View

Area Data pada halaman kerja Table View terdiri dari:

| Elemen | Fungsi |
| ------ | ------ |
| Judul Data | Menampilkan ikon panah, nama Data, dan angka jumlah [[Docs/Tipe Data/Row]] dalam tanda kurung. |
| [[^value/radio|full]], [[^value/radio/|half]], [[^value/radio|quarter]] | Menentukan porsi layar yang ditempati Data. Selengkapnya lihat [[#Mengatur Tampilan Data]]. |
| Tombol [[^button/q]] | Membuka pengaturan [[Docs/Tipe Data/Query]] untuk Data tersebut. |
| Kolom Data | Menampilkan kolom hasil [[Docs/Tipe Data/Query]], ditambah [[^field|Action]] di akhir |
| Baris Data | Menampilkan baris hasil [[Docs/Tipe Data/Query]], ditambah tombol [[^button/save|Save]] dan [[^button/delete|Delete]] |
| [[^button/add|Add Row]] | Menambahkan baris pada sumber Data. |
| [[^field|Show _ of _ items, on page]], [[^button/empty|Go]], [[^button/left|Prev]], [[^button/right|Next]] | Informasi jumlah Row dan perpindahan halaman, sama seperti pada [[Docs/Modul Data/Table/Apa itu Table|Table]]. |
| [[^field|Empty]] | Muncul pada Data yang [[Docs/Tipe Data/Query]]-nya belum diisi. |
| Error | Muncul ketika ada kesalahan dalam Query. Selengkapnya lihat [[Docs/Tipe Data/Query#Error]]

## Interaksi Antarmuka Table View

| Fungsi | Aksi |
| ------ | ---- |
| Melipat atau membuka Data | Klik judul Data. |
| Membuka menu konteks Data | Klik kanan pada judul Data, lalu pilih [[^field/edit|Rename]], [[^field/add|Add Row]], [[^field/add|Add Data]], atau [[^field/delete|Delete Data]]. |

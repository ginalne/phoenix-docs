---
    status: release
    title: Full (Elemen Layout)
    description: Full adalah Elemen Layout pada Form yang menampung Elemen lain dalam tampilan penuh sekaligus menjadi header Table bagi Elemen di dalamnya.
---
# Form Layout : Full

>**note** Layout Full merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Layout|Elemen Layout]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Layout Full adalah [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Elemen Layout]] yang dapat digunakan untuk menampung [[Docs/Modul Interface/Form/Elemen Form/Pengenalan|Elemen]] lain dalam tampilan penuh, sekaligus menentukan [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber data bagi Elemen di dalamnya.

## Menambahkan Layout Full

Anda dapat menambahkan Layout Full dengan dua cara:

- Memilih [[^field|Full Layout]] pada [[Docs/Modul Interface/Form/Form Page#Start Building|Start Building]] saat membuat Page.
- Memilih Layout Full pada [[^field|Type something here to add...]] di dalam Layout lain (menjadi Layout anak).

Langkah lengkapnya ada di [[Docs/Modul Interface/Form/Elemen Form/Menambahkan|Menambahkan Elemen]].

## Mengonfigurasi Layout Full

![[Docs/Modul Interface/Form/Elemen Form/Layout/full-header-form.png]]
![[Docs/Modul Interface/Form/Elemen Form/Layout/properties-form-full.png]]
Klik kiri Layout Full di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]]. Label Table (berikon tabel) juga tampil di atas Layout Full sebagai informasi Binding.

### Header Toolbar

Tidak ada perbedaan dari Elemen lain, yaitu hanya memiliki tombol [[^button/delete|Remove]] untuk [[#Menghapus Layout Full]].

### Properties Panel

| Bagian | Fungsi |
| --- | --- |
| [[^field|Binding]] | Menentukan header Layout Full. Lihat [[#Binding]]. |
| [[^field|State]] | Mengatur kondisi Layout Full. [[^field|Visible]] menampilkan atau menyembunyikan Layout Full. |
| [[^field|Children]] | Daftar Elemen di dalam Layout Full, lengkap dengan kategorinya ([[^field|display]] atau [[^field|input]]) dan namanya. |

### Binding

Binding dalam Layout Full sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/Binding#Binding Layout]].

### State

State dalam Layout Full sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/State]].

### Attribute

Tidak ada atribut yang dapat dikonfigurasi pada Layout Full.

### Children

Daftar [[^field|Children]] menampilkan setiap Elemen di dalam Layout Full. Setiap baris diberi kategori ([[^field|layout]], [[^field|display]] atau [[^field|input]]) dan nama Elemen. Tambahkan Elemen baru lewat [[^field|Type something here to add...]] di bagian bawah Layout Full.

## Menghapus Layout Full

Langkah menghapus Layout Full sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan LayoutFull
> Menghapus LayoutFull akan menghapus semua Elemen di dalamnya. Aksi tidak bisa dikembalikan.
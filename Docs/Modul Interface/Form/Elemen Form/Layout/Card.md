---
    status: release
    title: Card (Elemen Layout)
    description: Card adalah Elemen Layout pada Form yang menampung Elemen lain dalam satu kartu sekaligus menjadi header Table bagi Elemen di dalamnya.
---
# Form Layout : Card

>**note** Layout Card merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Layout|Elemen Layout]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Layout Card adalah [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Elemen Layout]] yang dapat digunakan untuk menampung [[Docs/Modul Interface/Form/Elemen Form/Pengenalan|Elemen]] lain dalam satu kartu.

## Menambahkan Layout Card

Anda dapat menambahkan Layout Card dengan dua cara:

- Memilih [[^field|Card Layout]] pada [[Docs/Modul Interface/Form/Form Page#Start Building|Start Building]] saat membuat Page.
- Memilih Layout Card pada [[^field|Type something here to add...]] di dalam Layout lain (menjadi Layout anak).

Langkah lengkapnya ada di [[Docs/Modul Interface/Form/Elemen Form/Menambahkan|Menambahkan Elemen]].

## Mengonfigurasi Layout Card

Klik kiri Layout Card di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]]. Label Table (berikon tabel) juga tampil di atas Layout Card sebagai informasi Binding.

### Header Toolbar

Tidak ada perbedaan dari Elemen lain, yaitu hanya memiliki tombol [[^button/delete|Remove]]  untuk [[#Menghapus Card]].

![[Docs/Modul Interface/Form/Elemen Form/Layout/card-header-form.png]]
### Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/Layout/properties-form-card.png]]
| Bagian | Fungsi |
| --- | --- |
| [[^field|Binding]] | Menentukan header Layout Card. Lihat [[#Binding]]. |
| [[^field|State]] | Mengatur kondisi Layout Card. [[^field|Visible]] menampilkan atau menyembunyikan LayoutCard. |
| [[^field|Children]] | Daftar Elemen di dalam Layout Card, lengkap dengan kategorinya ([[^field|display]] atau [[^field|input]]) dan namanya. |

### Binding

Binding dalam Layout Card sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/Binding#Binding Layout]].

### State

State dalam Layout Card sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/State]].

### Attribute

Tidak ada atribut yang dapat dikonfigurasi pada Layout Card.

### Children

Daftar [[^field|Children]] menampilkan setiap Elemen di dalamLayout Card. Setiap baris diberi kategori ([[^field|layout]], [[^field|display]] atau [[^field|input]]) dan nama Elemen. Tambahkan Elemen baru lewat [[^field|Type something here to add...]] di bagian bawah Layout Card.

## Menghapus Layout Card

Langkah menghapus Layout Card sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Layout Card
> Menghapus Layout Card akan menghapus semua Elemen di dalamnya. Aksi tidak bisa dikembalikan.
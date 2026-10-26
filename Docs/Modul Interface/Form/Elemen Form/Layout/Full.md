---
    status: draft
    title: Full (Elemen Layout)
    description: Full adalah Elemen Layout pada Form yang menampung Elemen lain dalam tampilan penuh sekaligus menjadi header Table bagi Elemen di dalamnya.
---
# Form Layout : Full

>**note** Full merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Layout|Elemen Layout]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Full adalah [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Elemen Layout]] yang dapat digunakan untuk menampung [[Docs/Modul Interface/Form/Elemen Form/Pengenalan|Elemen]] lain dalam tampilan penuh, sekaligus menentukan [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber data bagi Elemen di dalamnya.

Dengan Full, Anda tidak perlu memetakan Table pada setiap kolom isian. Cukup pilih Table pada Full, lalu Elemen Input di dalamnya tinggal memilih [[Docs/Tipe Data/Column]]. Untuk data yang berelasi, Full dapat disusun bertingkat dengan memakai pivot.

## Mengapa Menggunakan Layout Full?

Pilih Full bila Anda ingin Elemen di dalamnya tampil secara penuh.

## Menambahkan Layout Full

Anda dapat menambahkan Layout Full dengan dua cara:

- Memilih [[^field|Full Layout]] pada [[Docs/Modul Interface/Form/Form Page#Start Building|Start Building]] saat membuat Page.
- Memilih Full pada [[^field|Type something here to add...]] di dalam Layout lain (menjadi Layout anak).

Langkah lengkapnya ada di [[Docs/Modul Interface/Form/Elemen Form/Menambahkan|Menambahkan Elemen]].

## Mengonfigurasi Full

![[Docs/Modul Interface/Form/Elemen Form/Layout/full-header-form.png]]
![[Docs/Modul Interface/Form/Elemen Form/Layout/properties-form-full.png]]
Klik kiri Full di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]]. Label Table (berikon tabel) juga tampil di atas Full sebagai informasi Binding.

### Header Toolbar

Tidak ada perbedaan dari Elemen lain, yaitu hanya memiliki tombol [[^button/delete|Remove]] untuk [[#Menghapus Full]].

### Properties Panel

| Bagian | Fungsi |
| --- | --- |
| [[^field|Binding]] | Menentukan header Full. Lihat [[#Binding]]. |
| [[^field|State]] | Mengatur kondisi Full. [[^field|Visible]] menampilkan atau menyembunyikan Full. |
| [[^field|Children]] | Daftar Elemen di dalam Full, lengkap dengan kategorinya ([[^field|display]] atau [[^field|input]]) dan namanya. |

### Binding

Binding dalam Full sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/Binding#Binding Layout]].

### State

State dalam Full sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/State]].

### Attribute

Tidak ada atribut yang dapat dikonfigurasi pada Full.

### Children

Daftar [[^field|Children]] menampilkan setiap Elemen di dalam Full. Setiap baris diberi kategori ([[^field|layout]], [[^field|display]] atau [[^field|input]]) dan nama Elemen. Tambahkan Elemen baru lewat [[^field|Type something here to add...]] di bagian bawah Full.

## Menghapus Full

Langkah menghapus Full sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Full
> Menghapus Full akan menghapus semua Elemen di dalamnya. Aksi tidak bisa dikembalikan.
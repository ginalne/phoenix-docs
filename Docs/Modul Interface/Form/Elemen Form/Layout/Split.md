---
    status: draft
    title: Split (Elemen Layout)
    description: Split adalah Elemen Layout pada Form yang menampung Elemen lain dalam tampilan dibelah menjadi sisi kiri dan kanan, sekaligus menjadi header Table bagi Elemen di dalamnya.
---
# Form Layout : Split

>**note** Split merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Layout|Elemen Layout]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Split adalah [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Elemen Layout]] yang dapat digunakan untuk menampung [[Docs/Modul Interface/Form/Elemen Form/Pengenalan|Elemen]] lain dalam tampilan dibelah menjadi sisi kiri dan sisi kanan, sekaligus menentukan [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber data bagi Elemen di dalamnya.

Dengan Split, Anda tidak perlu memetakan Table pada setiap kolom isian. Cukup pilih Table pada Split, lalu Elemen Input di dalamnya tinggal memilih [[Docs/Tipe Data/Column]]. Untuk data yang berelasi, Split dapat disusun bertingkat dengan memakai pivot.

## Mengapa Menggunakan Split?

Pilih Split bila Anda ingin Elemen tampil berdampingan di sisi kiri dan kanan. Setiap sisi adalah [[Docs/Modul Interface/Form/Elemen Form/Layout/Full|Layout Full]], sehingga cara menambahkan Elemen di dalamnya sama dengan [[Docs/Modul Interface/Form/Elemen Form/Layout/Full|Layout Full]].

>**note** Perbedaan tampilan desktop dan mobile
> Di desktop, Split tampil dibelah menjadi sisi kiri dan kanan. Di mobile, Split tampil sebagai potongan atas dan bawah.

## Menambahkan Split

Anda dapat menambahkan Split dengan dua cara:

- Memilih [[^field|Split Layout]] pada [[Docs/Modul Interface/Form/Form Page#Start Building|Start Building]] saat membuat Page.
- Memilih Split pada [[^field|Type something here to add...]] di dalam Layout lain (menjadi Split anak).

Langkah lengkapnya ada di [[Docs/Modul Interface/Form/Elemen Form/Menambahkan|Menambahkan Elemen]].

## Mengonfigurasi Split

![[Docs/Modul Interface/Form/Elemen Form/Layout/split-header-form.png]]
![[Docs/Modul Interface/Form/Elemen Form/Layout/properties-form-split.png]]
Klik kiri Split di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]]. Label Table (berikon tabel) juga tampil di atas Split sebagai informasi Binding.

### Header Toolbar

Tidak ada perbedaan dari Elemen lain, yaitu hanya memiliki tombol [[^button/delete|Remove]] untuk [[#Menghapus Split]].

### Properties Panel

| Bagian | Fungsi |
| --- | --- |
| [[^field|Binding]] | Menentukan header Split. Lihat [[#Binding]]. |
| [[^field|State]] | Mengatur kondisi Split. [[^field|Visible]] menampilkan atau menyembunyikan Split. |
| [[^field|Children]] | Daftar Elemen di dalam Split. Lihat [[#Children]]. |

### Binding

Binding dalam Split sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/Binding#Binding Layout]]. Karena setiap sisi adalah Layout Full, kedua sisi juga dapat menentukan Table header masing-masing.

### State

State dalam Split sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/State]].

### Attribute

Tidak ada atribut yang dapat dikonfigurasi pada Split.

### Children

Split memiliki dua sisi, kiri dan kanan, dan setiap sisi adalah Layout [[Docs/Modul Interface/Form/Elemen Form/Layout/Full|Full]]. Fungsi menambahkan Elemen sama dengan Full: tambahkan Elemen baru lewat [[^field|Type something here to add...]] pada masing-masing sisi. Daftar [[^field|Children]] pada Layout Split adalah dua Elemen Full.

## Menghapus Split

Langkah menghapus Split sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Split
> Menghapus Split akan menghapus semua Elemen di sisi kiri dan sisi kanan. Aksi tidak bisa dikembalikan.
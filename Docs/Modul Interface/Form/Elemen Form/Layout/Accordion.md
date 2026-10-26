---
    status: draft
    title: Accordion (Elemen Layout)
    description: Accordion adalah Elemen Layout pada Form yang menampung Elemen lain dalam kartu dengan header yang dapat di-toggle, sekaligus menjadi header Table bagi Elemen di dalamnya.
---
# Form Layout : Accordion

>**note** Accordion merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Layout|Elemen Layout]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Accordion adalah [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Elemen Layout]] yang dapat digunakan untuk menampung [[Docs/Modul Interface/Form/Elemen Form/Pengenalan|Elemen]] lain dalam satu kartu dengan header yang dapat di-toggle untuk menyembunyikan dan menampilkan isinya, sekaligus menentukan [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber data bagi Elemen di dalamnya.

Dengan Accordion, Anda tidak perlu memetakan Table pada setiap kolom isian. Cukup pilih Table pada Accordion, lalu Elemen Input di dalamnya tinggal memilih [[Docs/Tipe Data/Column]]. Untuk data yang berelasi, Accordion dapat disusun bertingkat dengan memakai pivot.

## Mengapa Menggunakan Accordion?

Pilih Accordion bila Anda ingin Elemen tampil dalam kartu yang isinya dapat disembunyikan, misalnya untuk bagian Form yang tidak perlu selalu terlihat. Accordion memiliki header dengan [[^field|Label]] dan kondisi bawaan lewat [[^field|Default State]].

## Menambahkan Accordion

Anda dapat menambahkan Accordion dengan dua cara:

- Memilih [[^field|Accordion Layout]] pada [[Docs/Modul Interface/Form/Form Page#Start Building|Start Building]] saat membuat Page.
- Memilih Accordion pada [[^field|Type something here to add...]] di dalam Layout lain (menjadi Accordion anak).

Langkah lengkapnya ada di [[Docs/Modul Interface/Form/Elemen Form/Menambahkan|Menambahkan Elemen]].

## Mengonfigurasi Accordion

![[Docs/Modul Interface/Form/Elemen Form/Layout/accordion-header-form.png]]
![[Docs/Modul Interface/Form/Elemen Form/Layout/properties-form-accordion.png]]
Klik kiri Accordion di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]]. Label Table (berikon tabel) juga tampil di atas Accordion sebagai informasi Binding.

### Header Toolbar

Tidak ada perbedaan dari Elemen lain, yaitu hanya memiliki tombol [[^button/delete|Remove]] untuk [[#Menghapus Accordion]].

### Properties Panel

| Bagian | Fungsi |
| --- | --- |
| [[^field|Binding]] | Menentukan header Accordion. Lihat [[#Binding]]. |
| [[^field|State]] | Mengatur kondisi Accordion. [[^field|Visible]] menampilkan atau menyembunyikan seluruh Accordion. |
| [[^field|Attribute]] | Mengatur [[^field|Label]] pada header dan [[^field|Default State]]. Lihat [[#Attribute]]. |
| [[^field|Children]] | Daftar Elemen di dalam Accordion, lengkap dengan kategorinya ([[^field|display]] atau [[^field|input]]) dan namanya. |

### Binding

Binding dalam Accordion sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/Binding#Binding Layout]].

### State

State dalam Accordion sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/State]].

[[^field|Visible]] berbeda dengan kondisi `Collapsed` pada [[^field|Default State]]. [[^field|Visible]] bernilai [[^value/boolean/false]] menyembunyikan seluruh Accordion, sedangkan `Collapsed` hanya menyembunyikan isinya dan header tetap tampil.

### Attribute

Accordion memiliki dua atribut yang dapat dikonfigurasi:

| Atribut | Fungsi |
| --- | --- |
| [[^field|Label]] | Teks yang tampil sebagai title pada header Accordion. Hanya berupa teks statis dan tidak dapat memakai expression. |
| [[^field|Default State]] | Menentukan kondisi bawaan Accordion saat Form dibuka. Pilihannya `Expanded` (isi ditampilkan) dan `Collapsed` (isi disembunyikan). |

### Children

Daftar [[^field|Children]] menampilkan setiap Elemen di dalam Accordion. Setiap baris diberi kategori ([[^field|layout]], [[^field|display]] atau [[^field|input]]) dan nama Elemen. Tambahkan Elemen baru lewat [[^field|Type something here to add...]] di bagian bawah Accordion.

## Menghapus Accordion

Langkah menghapus Accordion sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Accordion
> Menghapus Accordion akan menghapus semua Elemen di dalamnya. Aksi tidak bisa dikembalikan.
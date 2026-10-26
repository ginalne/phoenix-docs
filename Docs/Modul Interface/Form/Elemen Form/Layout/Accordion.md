---
    status: release
    title: Accordion (Elemen Layout)
    description: Accordion adalah Elemen Layout pada Form yang menampung Elemen lain dalam kartu dengan header yang dapat di-toggle, sekaligus menjadi header Table bagi Elemen di dalamnya.
---
# Form Layout : Accordion

>**note** Layout Accordion merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Layout|Elemen Layout]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Layout Accordion adalah [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Elemen Layout]] yang dapat digunakan untuk menampung [[Docs/Modul Interface/Form/Elemen Form/Pengenalan|Elemen]] lain dalam satu kartu dengan header yang dapat di-toggle untuk menyembunyikan dan menampilkan isinya, sehingga Layout ini berguna untuk bagian Form yang tidak perlu selalu terlihat.

Layout Accordion memiliki header dengan [[^field|Label]] dan kondisi bawaan lewat [[^field|Default State]]. 

## Menambahkan Layout Accordion

Anda dapat menambahkan Layout Accordion dengan dua cara:

- Memilih [[^field|Accordion Layout]] pada [[Docs/Modul Interface/Form/Form Page#Start Building|Start Building]] saat membuat Page.
- Memilih Layout Accordion pada [[^field|Type something here to add...]] di dalam Layout lain (menjadi Layout anak).

Langkah lengkapnya ada di [[Docs/Modul Interface/Form/Elemen Form/Menambahkan|Menambahkan Elemen]].

## Mengonfigurasi Layout Accordion

![[Docs/Modul Interface/Form/Elemen Form/Layout/accordion-header-form.png]]
![[Docs/Modul Interface/Form/Elemen Form/Layout/properties-form-accordion.png]]
Klik kiri Layout Accordion di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]]. Label Table (berikon tabel) juga tampil di atas Layout Accordion sebagai informasi Binding.

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

Binding dalam Layout Accordion sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/Binding#Binding Layout]].

### State

State dalam Layout Accordion sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/State]].

[[^field|Visible]] berbeda dengan kondisi `Collapsed` pada [[^field|Default State]]. [[^field|Visible]] bernilai [[^value/boolean/false]] menyembunyikan seluruh Layout Accordion, sedangkan `Collapsed` hanya menyembunyikan isinya dan header tetap tampil.

### Attribute

Layout Accordion memiliki dua atribut yang dapat dikonfigurasi:

| Atribut | Fungsi |
| --- | --- |
| [[^field|Label]] | Teks yang tampil sebagai title pada header Accordion. Hanya berupa teks statis dan tidak dapat memakai expression. |
| [[^field|Default State]] | Menentukan kondisi bawaan Accordion saat Form dibuka. Pilihannya `Expanded` (isi ditampilkan) dan `Collapsed` (isi disembunyikan). |

### Children

Daftar [[^field|Children]] menampilkan setiap Elemen di dalam Layout Accordion. Setiap baris diberi kategori ([[^field|layout]], [[^field|display]] atau [[^field|input]]) dan nama Elemen. Tambahkan Elemen baru lewat [[^field|Type something here to add...]] di bagian bawah Layout Accordion.

## Menghapus Layout Accordion

Langkah menghapus Layout Accordion sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Layout Accordion
> Menghapus Layout Accordion akan menghapus semua Elemen di dalamnya. Aksi tidak bisa dikembalikan.
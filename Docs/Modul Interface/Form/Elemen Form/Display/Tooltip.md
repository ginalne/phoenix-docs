---
    status: draft
    title: "Form Display : Tooltip"
    description: Tooltip adalah Elemen Display pada Form untuk menampilkan kotak informasi berisi label dan keterangan yang selalu terlihat oleh pengisi.
---
# Form Display : Tooltip

>**note** Tooltip merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Display|Elemen Display]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Display Tooltip adalah [[Docs/Modul Interface/Form/Elemen Form/Display/Pengenalan|Elemen Display]] yang dapat digunakan untuk menampilkan kotak informasi di Form. Isinya diatur lewat dua atribut, yaitu [[^field|Label]] dan [[^field|Content]].

Dengan Display Tooltip, Anda dapat menyampaikan informasi tambahan kepada pengisi tanpa memengaruhi data.

>**note** Kotak informasi selalu tampil
> Meskipun bernama Tooltip, kotak informasi pada Display Tooltip selalu tampil dan tidak perlu diarahkan kursor terlebih dahulu.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara [[Docs/Modul Interface/Form/Elemen Form/Menghapus|menghapus Elemen]] ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Display Tooltip.

## Menambahkan Display Tooltip

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] pada [[Docs/Modul Interface/Form/Antarmuka|halaman kerja Form]]
2. Klik [[^field|Type something here to add...]] pada [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Layout]]
3. Pilih [[^field|Tooltip]] dari daftar, atau ketik untuk mencarinya
4. Isi [[^field|Label]] dan [[^field|Content]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengonfigurasi Display Tooltip

Klik kiri Display Tooltip di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]].

### Header Toolbar

![[Docs/Modul Interface/Form/Elemen Form/Display/toolbar-form-tooltip.png]]
Header Toolbar Display Tooltip hanya memiliki tombol [[^button/delete|Remove]] untuk [[#Menghapus Display Tooltip]].

### Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/Display/properties-form-tooltip.png]]
#### State

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan Tooltip. |

#### Attributes

| Atribut | Fungsi |
| --- | --- |
| [[^field|Label]] | Judul kotak informasi. |
| [[^field|Content]] | Isi keterangan yang ditampilkan pada kotak informasi. |

<!--
  * [TODO] Konfirmasi fungsi Label: apakah judul kotak informasi seperti yang ditulis di tabel Attributes, atau fungsi lain.
  * [TODO] Konfirmasi apakah Label dan Content hanya teks statis seperti Display Text. Jika ya, tambahkan kalimat "Saat ini hanya berupa teks statis dan belum dapat berisi [[Docs/Tipe Data/Expression]]." pada kedua baris.
-->

#### Parent

Menampilkan Layout tempat Display Tooltip berada. Ukuran, *padding*, dan *margin* Display Tooltip diatur lewat Layout Panel. Lihat [[Docs/Modul Interface/Form/Apa itu Form#Layout Panel]].

<!--
  * [TODO] Tempatkan screenshot Header Toolbar (toolbar-form-tooltip.png) dan Properties Panel (properties-form-tooltip.png) di folder Display. Anotasi yang disarankan: nomor 1 pada tombol Remove, nomor 2 pada Label dan Content.
-->

## Menghapus Display Tooltip

Langkah menghapus Display Tooltip sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Display Tooltip
> Menghapus Display Tooltip akan menghapus kotak informasi beserta isinya. Aksi tidak bisa dikembalikan.
---
    status: draft
    title: "Form Display : Tooltip"
    description: Tooltip adalah Elemen Display pada Form untuk menampilkan kotak informasi berisi label dan keterangan yang selalu terlihat oleh pengisi.
    pageDecoration:
      icon: x
      tree:
        priority: 0
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

Klik kiri Display Tooltip di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]], [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Layout Panel]].

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

#### Parent

Menampilkan Layout tempat Display Tooltip berada.

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* Display Tooltip dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Layout Panel]].

## Menghapus Display Tooltip

Langkah menghapus Display Tooltip sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Display Tooltip
> Menghapus Display Tooltip akan menghapus kotak informasi beserta isinya. Aksi tidak bisa dikembalikan.
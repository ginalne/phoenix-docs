---
    status: release
    title: "Form Display : Text"
    description: Text adalah Elemen Display pada Form untuk menampilkan teks statis seperti judul, keterangan, dan petunjuk pengisian.
    pageDecoration:
      tree:
        priority: 0
---
# Form Display : Text

>**note** Text merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Display|Elemen Display]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Display Text adalah [[Docs/Modul Interface/Form/Elemen Form/Display/Pengenalan|Elemen Display]] yang dapat digunakan untuk menampilkan teks statis di Form, misalnya judul, keterangan, atau petunjuk pengisian.

Dengan Display Text, Anda dapat memberi konteks kepada pengisi tanpa memengaruhi data. Teksnya dapat diatur ukuran dan gayanya langsung dari Header Toolbar.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara [[Docs/Modul Interface/Form/Elemen Form/Menghapus|menghapus Elemen]] ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Display Text.

## Menambahkan Display Text

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] pada [[Docs/Modul Interface/Form/Antarmuka|halaman kerja Form]]
2. Klik [[^field|Type something here to add...]] pada [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Layout]]
3. Pilih [[^field|Text]] dari daftar, atau ketik untuk mencarinya
4. Isi [[^field|Content]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengonfigurasi Display Text

Klik kiri Display Text di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]].

### Header Toolbar

![[Docs/Modul Interface/Form/Elemen Form/Display/toolbar-form-text.png]]
Selain tombol [[^button/delete|Remove]], Header Toolbar Display Text memiliki pengaturan teks: ukuran font, *bold*, *italic*, *underline*, serta rata kiri, tengah, dan kanan. Pengaturan ini berlaku pada teks yang sedang dipilih.

### Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/Display/properties-form-text.png]]
#### State

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan Text. |

#### Attributes

| Atribut | Fungsi |
| --- | --- |
| [[^field|Content]] | Isi teks yang ditampilkan. Saat ini hanya berupa teks statis dan belum dapat berisi [[Docs/Tipe Data/Expression]]. |

#### Parent

Menampilkan Layout tempat Display Text berada. Ukuran, *padding*, dan *margin* Display Text diatur lewat Layout Panel. Lihat [[Docs/Modul Interface/Form/Apa itu Form#Layout Panel]].

## Menghapus Display Text

Langkah menghapus Display Text sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Display Text
> Menghapus Display Text akan menghapus teks beserta isinya. Aksi tidak bisa dikembalikan.
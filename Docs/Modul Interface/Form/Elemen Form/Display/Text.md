---
    status: release
    title: "Form Display : Text"
    description: Text adalah Elemen Display pada Form untuk menampilkan teks statis seperti judul, keterangan, dan petunjuk pengisian.
---
# Form Display : Text

>**note** Text merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Display|Elemen Display]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Text adalah [[Docs/Modul Interface/Form/Elemen Form/Display/Pengenalan|Elemen Display]] yang dapat digunakan untuk menampilkan teks statis di Form, misalnya judul, keterangan, atau petunjuk pengisian.

Dengan Text, Anda dapat memberi konteks kepada pengisi tanpa memengaruhi data. Teksnya dapat diatur ukuran dan gayanya langsung dari Header Toolbar.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara [[Docs/Modul Interface/Form/Elemen Form/Menghapus|menghapus Elemen]] ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Text.

## Mengapa Menggunakan Text?

- **Pengisi lebih paham.** Judul dan petunjuk membuat tujuan Form dan cara mengisinya jelas.
- **Mudah diatur.** Isi teks cukup diubah pada field [[^field|Content]], tanpa Binding.
- **Tampilan dapat disesuaikan.** Ukuran font, *bold*, *italic*, *underline*, dan rata teks diatur dari Header Toolbar.
- **Tidak memengaruhi data.** Text hanya menampilkan informasi, sehingga tidak menambah isian ke Table.

## Menambahkan Text

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] pada [[Docs/Modul Interface/Form/Antarmuka|halaman kerja Form]]
2. Klik [[^field|Type something here to add...]] pada [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Layout]]
3. Pilih [[^field|Text]] dari daftar, atau ketik untuk mencarinya
4. Isi [[^field|Content]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengonfigurasi Text

![[Docs/Modul Interface/Form/Elemen Form/Display/properties-form-text.png]]
Klik kiri Text di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan Properties Panel dan Header Toolbar.

### State Text

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan Text. |

### Attributes Text

| Atribut | Fungsi |
| --- | --- |
| [[^field|Content]] | Isi teks yang ditampilkan. Saat ini hanya berupa teks statis dan belum dapat berisi [[Docs/Tipe Data/Expression]]. |

### Parent

Menampilkan Layout tempat Text berada. Ukuran, *padding*, dan *margin* Text diatur lewat Layout Panel. Lihat [[Docs/Modul Interface/Form/Apa itu Form#Layout Panel]].

### Header Toolbar teks

![[Docs/Modul Interface/Form/Elemen Form/Display/toolbar-form-text.png]]
Selain tombol [[^button/delete|Remove]], Header Toolbar Text memiliki pengaturan teks: ukuran font, *bold*, *italic*, *underline*, serta rata kiri, tengah, dan kanan. Pengaturan ini berlaku pada teks yang sedang dipilih.
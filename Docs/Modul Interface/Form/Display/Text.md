---
status: draft
title: Text (Elemen Display)
description: Text adalah Elemen Display pada Form untuk menampilkan teks statis seperti judul, keterangan, dan petunjuk pengisian.
---

# Text (Elemen Display)

>**note** Text merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Display|Elemen Display]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Text adalah Elemen Display yang dapat digunakan untuk menampilkan teks statis di Form, misalnya judul, keterangan, atau petunjuk pengisian.

Dengan Text, Anda dapat memberi konteks kepada pengisi tanpa memengaruhi data. Teksnya dapat diatur ukuran dan gayanya langsung dari Header Toolbar.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara menghapus Elemen ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Text.

## Mengapa Menggunakan Text?

- **Pengisi lebih paham.** Judul dan petunjuk membuat tujuan Form dan cara mengisinya jelas.
- **Mudah diatur.** Isi teks cukup diubah pada field [[^field|Content]], tanpa Binding.
- **Tampilan dapat disesuaikan.** Ukuran font, *bold*, *italic*, *underline*, dan rata teks diatur dari Header Toolbar.
- **Tidak memengaruhi data.** Text hanya menampilkan informasi, sehingga tidak menambah isian ke Table.

## Menambahkan Text

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]]
2. Klik [[^field|Type something here to add...]] pada Layout
3. Pilih Text dari daftar, atau ketik untuk mencarinya
4. Isi [[^field|Content]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengonfigurasi Text

![[Docs/Modul Interface/Form/Display/Text/properties-text.png]]
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

Selain tombol [[^button/delete|Remove]], Header Toolbar Text memiliki pengaturan teks: ukuran font, *bold*, *italic*, *underline*, serta rata kiri, tengah, dan kanan. Pengaturan ini berlaku pada teks yang sedang dipilih.

<!--
  * [TODO] Konfirmasi fungsi ikon `T` di kiri Header Toolbar Text, dan apakah teks dapat diedit langsung pada tampilan Form (selain lewat field Content).
  * [TODO] Konfirmasi alasan panel Text tidak memiliki bagian Binding (apakah karena isinya statis), dan apakah Expression direncanakan pada versi berikutnya.
-->

## Contoh Penggunaan

**Petunjuk pengisian pada Form pendaftaran**

Panitia sebuah kegiatan ingin pendaftar memahami cara mengisi Form tanpa perlu bertanya. Dengan Text, judul dan petunjuk ditampilkan tepat di atas isian, sehingga data yang masuk lebih lengkap dan benar.

**Komponen yang terlibat**

| Komponen | Peran |
| --- | --- |
| [[^field/form|Form Pendaftaran]] | Tempat pendaftar mengisi data lewat tautan publik. |
| Text | Menampilkan judul Form dan petunjuk pengisian. |
| [[Docs/Modul Interface/Form/Input/Basic/Penjelasan|Basic]] | Elemen Input untuk data pendaftar. |

<!--
  * [TODO] Nama Form pada contoh hanya penamaan generik. Sesuaikan dengan gambar yang Anda buat.
-->

**Hasil yang dirasakan**

- Pendaftar langsung memahami tujuan Form dan cara mengisinya.
- Isian yang masuk ke [[Docs/Modul Data/Table/Apa itu Table|Table]] lebih lengkap dan konsisten.
- Panitia mengurangi pertanyaan berulang dari pendaftar.

**Ide skenario lain**

| Jenis nilai | Contoh integrasi |
| --- | --- |
| Petunjuk | Text sebagai catatan di atas [[Docs/Modul Interface/Form/Input/Table/Penjelasan|Input Table]] untuk menjelaskan cara mengisi data berulang. |
| Judul | Text berukuran besar sebagai judul [[Docs/Modul Interface/Form/Layout/Card/Penjelasan|Card]]. |
| Pemisah | Beberapa Text sebagai penanda bagian pada Form yang panjang. |

Text membuat Form lebih mudah dipahami, sehingga data yang terkumpul lebih tepat sejak diisi.

## Praktik Terbaik

- **Singkat dan jelas.** Tulis [[^field|Content]] seperlunya agar pengisi tidak kewalahan.
- **Gunakan ukuran dan bold untuk judul.** Atur lewat [[#Header Toolbar teks|Header Toolbar teks]] agar judul menonjol.
- **Letakkan petunjuk dekat isian.** Taruh Text tepat di atas Elemen Input yang dijelaskan.
- **Gunakan Visible untuk petunjuk kondisional.** Sembunyikan Text dengan [[^field|Visible]] bila tidak diperlukan.

>**success** Text siap digunakan
> Setelah [[^field|Content]] terisi dan ukuran teks sesuai, Text siap tampil di Form.

## Batasan dan Catatan

- [[^field|Content]] saat ini hanya teks statis dan belum mendukung [[Docs/Tipe Data/Expression]].
- Panel Text tidak memiliki bagian Binding.
- Text tidak menambah isian ke Table dan tidak ikut dikirim sebagai Submission.
- Ukuran, *padding*, dan *margin* Text diatur lewat Layout Panel.

<!--
  * [TODO] Konfirmasi asumsi bahwa Text tidak ikut dikirim sebagai Submission dan tidak menambah isian ke Table (poin Batasan, TL:DR, dan FAQ).
  * [TODO] Halaman yang diusulkan dan belum ada: `Docs/Modul Interface/Form/Input/Table/Penjelasan` (dipakai pada Ide skenario lain).
-->

## TL:DR

- **Definisi.** Text adalah [[Docs/Modul Interface/Form/Apa itu Form#Elemen Display|Elemen Display]] untuk menampilkan teks statis.
- **Isi.** Atur teks lewat [[^field|Content]]; belum mendukung [[Docs/Tipe Data/Expression]].
- **Tampilan.** Ukuran dan gaya teks diatur dari [[#Header Toolbar teks|Header Toolbar teks]].
- **Kondisi.** [[^field|Visible]] menampilkan atau menyembunyikan Text.
- **Hati-hati.** Text tidak memiliki Binding dan tidak ikut dikirim sebagai Submission.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Apakah Content dapat menampilkan nilai dari Binding?**
> Belum. [[^field|Content]] saat ini hanya teks statis dan belum dapat berisi [[Docs/Tipe Data/Expression]].
> **Mengapa panel Text tidak punya Binding?**
> Text hanya menampilkan teks statis, sehingga tidak terikat ke data di [[Docs/Modul Data/Table/Apa itu Table|Table]].
> **Bagaimana mengubah ukuran teks?**
> Klik kiri Text di Edit Mode, lalu gunakan pengaturan ukuran font pada [[#Header Toolbar teks|Header Toolbar teks]].
> **Apakah isi Text dikirim sebagai Submission?**
> Tidak. Text hanya ditampilkan dan tidak menambah isian ke Table.
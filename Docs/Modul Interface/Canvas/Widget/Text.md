---
status: draft
title: Widget Text
description: Widget Text menampilkan teks berformat pada Canvas, dengan bagian teks yang dapat diganti oleh nilai dari Query.
---
# Widget Text

>**note** Widget Text merupakan salah satu widget pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Daftar widget lainnya ada di [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget Canvas]].

Widget Text adalah [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk menampilkan teks di dalam [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]], misalnya judul, keterangan, atau penjelasan yang melengkapi widget lain pada desain.

Teks dapat diformat (ukuran font, tebal, miring, garis bawah, dan rata teks), dan bagian teks dapat diganti dengan nilai dari [[Docs/Tipe Data/Query]] melalui daftar binding pada Data Panel.

## Menambahkan Widget Text

Ketik `/text` dalam [[^field|Type something here to add...]] untuk menambahkan teks. Langkah lengkapnya ada di [[Docs/Modul Interface/Canvas/Widget/Menambahkan|Menambahkan Widget]].

## Antarmuka Widget Text

![[Docs/Modul Interface/Form/Widget/Text/interface-widget-text.png]]
Pada [[^mode/edit|Edit]], klik kiri widget untuk menampilkan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar]] di atas widget, serta [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]] dan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Data Panel]] di bawah widget.

### Header Toolbar

| Elemen | Fungsi |
| --- | --- |
| Ikon Text (paling kiri) | Menandai jenis widget. |
| Ikon pegangan ⋮⋮ | Memindahkan widget ke posisi atau Layout lain. |
| Tombol − dan + dengan kolom ukuran (contoh 22) | Mengurangi dan menambah ukuran font teks. |
| [[^toggle/bold\|Bold]] | Toggle teks tebal. |
| [[^toggle/italic\|Italic]] | Toggle teks miring. |
| [[^toggle/underline\|Underline]] | Toggle teks bergaris bawah. |
| [[^toggle/align-left\|Rata kiri]], [[^toggle/align-center\|Rata tengah]], [[^toggle/align-right\|Rata kanan]] | Mengatur perataan teks. Pilihan yang aktif ditandai dengan latar berwarna. |
| [[^button/delete\|Remove]] | Menghapus widget dari Canvas. Lihat [[#Menghapus Widget Text]]. |

Tombol toggle yang aktif ditandai dengan latar berwarna.

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* pada widget dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]].

### Data Panel

Data Panel (ikon kode) berisi daftar binding untuk mengganti teks dengan nilai dari [[Docs/Tipe Data/Query]]. Query yang dipakai mengikuti kaidah [[Docs/Tipe Data/Query#Single Output]].

| Elemen | Fungsi |
| --- | --- |
| [[^button/add\|Parse Query]] | Menambahkan binding ke daftar. Setiap binding mengganti teks dengan nilai dari Query yang mengikuti kaidah Single Output. |

## Menghapus Widget Text

Langkah menghapus Widget Text sama dengan menghapus widget lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan
> Menghapus widget akan menghapus semua konfigurasi yang ada termasuk teks dan Query pada binding yang sudah dibuat. Data sumber dan barisnya tetap aman. Setelah terhapus, aksi tidak bisa dikembalikan.

## Praktik Terbaik

- **Bedakan judul dan keterangan lewat ukuran font.** Gunakan font lebih besar dan [[^toggle/bold|Bold]] untuk judul, dan font lebih kecil untuk keterangan.
- **Gunakan binding untuk teks yang berubah.** Ganti bagian teks dengan nilai dari Query pada Data Panel agar teks mengikuti data.
- **Pastikan Query mengikuti kaidah [[Docs/Tipe Data/Query#Single Output|Single Output]].** Query yang tidak sesuai membuat nilai tidak tampil dengan benar.
- **Atur [[^field|min.]], [[^field|padding]], dan [[^field|margin]].** Beri ruang cukup agar teks tidak terpotong oleh widget lain pada Canvas.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Format teks apa saja yang tersedia?**
> Ukuran font, [[^toggle/bold|Bold]], [[^toggle/italic|Italic]], [[^toggle/underline|Underline]], dan rata teks (kiri, tengah, kanan), semuanya diatur pada [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar|Header Toolbar]].
> **Bagaimana mengganti sebagian teks dengan data?**
> Buka Data Panel, klik [[^button/add|Parse Query]] untuk menambahkan binding, lalu atur Query yang mengikuti kaidah [[Docs/Tipe Data/Query#Single Output|Single Output]].
> **Query seperti apa yang dipakai binding Widget Text?**
> Query harus mengikuti kaidah [[Docs/Tipe Data/Query#Single Output|Single Output]].
> **Bagaimana mengatur ukuran dan jarak widget?**
> Gunakan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel|Layout Panel]] untuk mengatur [[^field|min.]], [[^field|padding]], dan [[^field|margin]].
> **Bagaimana memindahkan teks ke posisi lain?**
> Gunakan ikon pegangan ⋮⋮ pada [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar|Header Toolbar]] untuk memindahkan widget ke posisi atau Layout lain.

<!--
  * [TODO] Cara mengganti teks dengan binding belum dijelaskan: bagaimana binding direferensikan di dalam teks (penanda atau nama binding), kolom pada setiap item binding (nama, Query), cara mengatur Query (tombol Q atau popup), dan cara menghapus item. Tambahkan bagian "Mengatur Widget Text" setelah informasi tersedia.
  * [TODO] Tombol Parse Column pada Data Panel akan dihapus oleh penulis, jadi tidak ditulis di halaman ini. Hapus TODO ini setelah screenshot diperbarui. Nama tombol Parse Query juga mungkin berubah.
  * [TODO] Konfirmasi: Bold, Italic, Underline, dan rata teks berlaku untuk seluruh teks atau hanya teks yang diseleksi. Juga satuan dan rentang ukuran font (contoh 22) serta apakah kolom ukuran dapat diisi langsung.
  * [TODO] Konfirmasi: cara mengisi dan mengubah teks (diketik langsung pada widget?) dan perilaku kolom min. w dan h pada Layout Panel (contoh 0%).
  * [TODO] Konfirmasi: Widget Text tidak memiliki Design Panel (tidak ada panel palet pada screenshot).
  * [TODO] Nama slug ikon toggle (bold, italic, underline, align-left, align-center, align-right) adalah tebakan. Pada screenshot (tampilan mobile) tombol Remove hanya menampilkan ikon tempat sampah tanpa label.
  * [TODO] Konfirmasi perintah `/text` (Add text) dan apakah ada variasi pada dropdown seperti widget lain.
  * [TODO] Teks "This is title" pada screenshot adalah contoh isi. Mohon ganti dengan teks generik bila perlu.
  * [TODO] Halaman baru yang diusulkan: `Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Data Panel` dan `Docs/Tipe Data/Query#Single Output`. Path gambar `Docs/Modul Interface/Form/Widget/Text/interface-widget-text.png` mengikuti halaman widget lain, mohon konfirmasi apakah dipindah ke `Docs/Modul Interface/Canvas/Widget/Text/`.
-->
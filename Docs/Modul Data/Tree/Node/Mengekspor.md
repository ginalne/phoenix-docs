---
    status: draft
    title: Mengekspor Node
    description: Cara mengekspor Node beserta keturunannya dari Tree menjadi file.
    pageDecoration:
      icon: x
      tree:
        priority: 4
---
# Mengekspor Node

Mengekspor menyimpan [[Docs/Tipe Data/Node|Node]] beserta seluruh keturunannya ke dalam file. Gunakan ekspor untuk membuat cadangan atau memindahkan struktur ke [[Docs/Modul Data/Tree/Apa itu Tree|Tree]] lain lewat [[Docs/Modul Data/Tree/Node/Mengimpor|Mengimpor]].

## Langkah Mengekspor

1. Buka halaman kerja [[Docs/Modul Data/Tree/Apa itu Tree|Tree]].
2. Klik kanan [[Docs/Tipe Data/Node|Node]] yang akan diekspor ➜ [[^field/export|Export]].
3. Simpan file hasil ekspor.

>**success** Node berhasil diekspor
> File berisi Node yang Anda pilih beserta seluruh keturunannya.

Ekspor tidak mengubah data Tree. Untuk mengekspor seluruh Tree, ekspor Node Origin.

Format isi file dijelaskan di [[Docs/Modul Data/Tree/Node/Format Import dan Export|Format Import dan Export]].

<!--
  * [TODO] Langkah di atas tebakan: Export langsung mengunduh file tanpa dialog. Mohon konfirmasi apakah ada dialog (misalnya pilihan format atau nama file) dan apakah yang diekspor selalu Node terpilih beserta keturunannya.
    Jawaban: Export saat ini hanya mengunduh file, karena hanya format json yang disediakan (tidak ada dalam pilihan).
  * [TODO] Halaman baru yang diusulkan: Docs/Modul Data/Tree/Node/Format Import dan Export. Isi yang diharapkan: format file, atribut yang disertakan (Name, Order, Children), dan contoh isi file. Satu halaman ini dipakai bersama oleh Mengekspor dan Mengimpor.
    Jawaban: akan dibuat nanti ketika ada.
-->

>**note** Hak akses
> Ekspor hanya membaca data sehingga tidak memerlukan [[Docs/Modul Developer/Workspace/Data Access#Data yang Diatur pada Setiap Komponen|Data Access]] Add, Update, atau Delete.

<!--
  * [TODO] Mohon konfirmasi apakah Export dibatasi hak akses tertentu pada Workspace.
    Jawaban: Tidak
-->

## Lihat Juga

- [[Docs/Modul Data/Tree/Node/Mengimpor|Mengimpor Node]]
- [[Docs/Modul Data/Tree/Node/Format Import dan Export|Format Import dan Export]]
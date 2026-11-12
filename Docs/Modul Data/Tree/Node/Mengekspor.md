---
    status: release
    title: Mengekspor Node
    description: Cara mengekspor Node beserta keturunannya dari Tree menjadi file.
    pageDecoration:
      tree:
        priority: 4
---
# Mengekspor Node

Mengekspor menyimpan [[Docs/Tipe Data/Node|Node]] beserta seluruh keturunannya ke dalam file JSON. Gunakan ekspor untuk membuat cadangan atau memindahkan struktur ke [[Docs/Modul Data/Tree/Apa itu Tree|Tree]] lain lewat [[Docs/Modul Data/Tree/Node/Mengimpor|Mengimpor]].

## Langkah Mengekspor

1. Buka halaman kerja [[Docs/Modul Data/Tree/Apa itu Tree|Tree]].
2. Klik kanan [[Docs/Tipe Data/Node|Node]] yang akan diekspor ➜ [[^field/export|Export]].
3. Tunggu file JSON terunduh.

Ekspor langsung mengunduh file tanpa dialog atau pilihan format karena hanya format JSON yang tersedia.

>**success** Node berhasil diekspor
> File berisi Node yang Anda pilih beserta seluruh keturunannya.

Ekspor tidak mengubah data Tree. Untuk mengekspor seluruh Tree, ekspor Node Origin.

Format isi file dijelaskan di [[Docs/Modul Data/Tree/Node/Format Import dan Export|Format Import dan Export]].

>**note** Hak akses
> Ekspor hanya membaca data dan tidak dibatasi hak akses tertentu pada [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].

## Lihat Juga

- [[Docs/Modul Data/Tree/Node/Mengimpor|Mengimpor Node]]
- [[Docs/Modul Data/Tree/Node/Format Import dan Export|Format Import dan Export]]
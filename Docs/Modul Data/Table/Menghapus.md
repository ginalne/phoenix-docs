---
    status: release
    title: "Menghapus Table"
    description: Penjelasan cara menghapus komponen Table
    pageDecoration:
      tree:
        priority: 1
---
# Menghapus Table

1. Buka folder yang berisi Table
2. Klik kanan Table, pilih [[^button/delete|Delete]]
3. Konfirmasi dengan [[^button|Delete]]

>**warning** Seluruh data Table ikut terhapus
> Menghapus Table menghapus seluruh [[Docs/Tipe Data/Column|Column]], [[Docs/Tipe Data/Row|Row]], dan [[Docs/Tipe Data/TableData|TableData]] di dalamnya. Komponen atau [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] yang menggunakan Table ini, termasuk [[Docs/Event/Menghubungkan Event|Event]] yang sudah terhubung dan field berformat Row yang merujuk ke Table ini, tidak lagi dapat mengambil datanya.


---
    status: release
    title: "Membuat Kanban Baru"
    description: Penjelasan cara membuat komponen Kanban baru.
    pageDecoration:
      tree:
        priority: 2
    tags:
      draft
---
# Membuat Kanban

![[Docs/Modul Interface/Kanban/add-kanban.png]]

1. Buka folder tempat Kanban akan ditempatkan di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan ➜ [[^field/add|Add]] ➜ [[^field|Interface]] ➜ [[^field/kanban|Kanban]]
3. Isi [[^field|Name]] dan [[^field|Description]]
4. Pilih [[^field|Table - Column]]
5. Klik [[^button|Create]]

>**note** Table - Column wajib diisi
>[[^field|Table - Column]] berisi daftar [[Docs/Tipe Data/Column]] berformat [[Docs/Tipe Data/EnumData|EnumData]]. Setiap [[Docs/Tipe Data/EnumData]] pada [[Docs/Tipe Data/Enum]] tersebut menjadi satu kolom Kanban. Misalnya, jika [[Docs/Tipe Data/Enum]] Status memiliki 4 [[Docs/Tipe Data/EnumData]], maka Kanban memiliki 4 kolom.

>**success** Kanban berhasil dibuat
>Kanban yang baru dibuat belum memiliki template, sehingga setiap kartu hanya menampilkan [[Docs/Modul Data/Table/Apa itu Table#Membuat Table|Alias]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]]. Atur tampilan kartu di [[#Mengatur Template Kartu]].

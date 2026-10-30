---
    status: release
    title: "Mengelola Row pada Table View Data"
    description: Penjelasan cara mengelola Row pada Table View Data
    pageDecoration:
      tree:
        priority: 0
---
# Table View Data : Mengelola Row

Row ditambahkan dan diisi seperti pada komponen Table. Cara mengisi setiap Format Column dijelaskan di [[Docs/Modul Data/Table/Apa itu Table#Mengelola Data Table]].

>**note** Kolom yang Terisi Otomatis
> Data hanya menampilkan baris yang memenuhi [[Docs/Tipe Data/Query]]. Jika [[Docs/Tipe Data/Query]] memiliki filter pada kolom yang tidak ditampilkan (artinya tidak bisa diisi melalui Data Table View), kolom tersebut tetap terisi otomatis saat baris ditambahkan. Dengan begitu, baris baru tetap memenuhi syarat Query dan tidak hilang bahkan setelah [[^button/refresh|Refresh]].
>Misalnya, Data berjudul [[^field|Menunggu Diproses]] memiliki kondisi Query pada kolom [[^field|Status]] (berformat [[Docs/Tipe Data/EnumData|EnumData]]) bernilai [[^field|Menunggu]], sementara kolom [[^field|Status]] tidak ditampilkan. Saat Anda menambahkan baris dari Data tersebut, kolom [[^field|Status]] langsung terisi [[^field|Menunggu]].

>**danger** Row pada Table ikut terhapus
> Baris yang ditampilkan Table View adalah data ril milik sumber. Menghapus baris dari Table View secara otomatis menghapusnya dari sumber dan tidak dapat dikembalikan.


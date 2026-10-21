---
    status: release
    title: "Membuat Table Baru"
    description: Penjelasan cara membuat komponen Table baru.
    pageDecoration:
      tree:
        priority: 2
    tags:
      draft
---
# Membuat Table Baru

![[Docs/Modul Data/Table/add-table.png]]
1. Buka folder tempat Table akan ditempatkan di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan ➜ [[^field/add|Add]] ➜ [[^field|Data]] ➜ [[^field/table|Table]]
3. Periksa [[^field|Directory]] yang terisi otomatis sesuai folder yang Anda klik kanan, atau pilih folder lain. Biarkan kosong untuk letak _root_.
4. Isi [[^field|Name]] dan [[^field|Description]]
5. Pada bagian [[^field|Column]], isi [[^field|Name]], pilih Format, dan isi Description untuk setiap Column
6. Klik [[^button/add|Add Column]] jika Anda membutuhkan Column tambahan
7. Isi kolom dengan sesuai (lihat [[#Mengisi Column]])
8. Pilih satu Column sebagai Alias dengan mengklik ikon bintang pada kolom [[^field|Alias]]
9. Klik [[^button|Create]]

Anda juga dapat membuat Table dari file dengan mengklik [[^button/upload|Upload]] di pojok kanan atas dialog. Selengkapnya lihat [[Docs/Modul Data/Table/Upload]].

Beberapa aturan penting:

- Table minimal memiliki satu Column.
- Setiap Table harus memiliki satu Alias. Pilih salah satu Column sebagai Alias.
- Pada field berformat Row, nilai ditampilkan dengan pola `ID - Alias Value`. Contoh: jika Alias adalah Column Nama dan Row dengan ID 1 bernilai "Kopi Arabika", field menampilkan `1 - Kopi Arabika`.

>**success** Table berhasil dibuat
> Table yang baru dibuat belum memiliki data. Tambahkan Row di [[#Mengelola Data Table]].


### Mengisi Column

Bagian [[^field|Column]] pada dialog [[^field|Create New Table]] atau [[^field|Update Table]] berupa tabel dengan kolom berikut:

| Elemen                      | Fungsi                                                                                                        |
| -------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [[^field|Index]]           | Nomor urut Column.                                                                                            |
| [[^field|Name]]            | Nama Column.                                                                                                  |
| [[^field|Format]]          | Format data Column. Pilih lewat [[^field|Select Data Format...]]. Selengkapnya lihat [[Docs/Tipe Data/Column]]. |
| [[^field|Header]]          | Header yang dibutuhkan oleh Format tertentu. Bernilai [[^field|N/A]] (*not applicable*) jika Format tidak membutuhkannya. Contoh: Format bertipe [[Docs/Tipe Data/EnumData|EnumData]] membutuhkan Header [[Docs/Tipe Data/Enum|Enum]], dan Format bertipe [[Docs/Tipe Data/Node|Node]] membutuhkan Header [[Docs/Tipe Data/Tree|Tree]]. |
| [[^field|Description]]     | Penjelasan singkat tentang isi Column.                                                                        |
| [[^field|Alias]]           | Penanda Column yang dipilih sebagai Alias. Hanya satu Column yang dapat dipilih.                              |
| [[^field|Action]]          | Berisi tombol [[^button/delete|Delete]] untuk menghapus Column dari dialog.                                  |

---
    status: release
    title: "Membuat Enum Baru"
    description: Penjelasan cara membuat komponen Enum baru.
    pageDecoration:
      tree:
        priority: 2
    tags:
      draft
---
# Membuat Table Baru

![[Docs/Modul Data/Enum/add-enum.png]]
1. Buka folder tempat Enum akan ditempatkan di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan ➜ [[^field/add|Add]] ➜ [[^field|Data]] ➜ [[^field/enum|Enum]]
3. Isi [[^field|Name]] dan [[^field|Description]]
4. Pilih [[^field|Format]] dan atur [[^field|Strict On Selected]] sesuai kebutuhan
5. Klik [[^button|Create]]

>**success** Enum berhasil dibuat
> Enum yang baru dibuat belum memiliki data. Tambahkan [[Docs/Tipe Data/EnumData]] di [[#Mengelola EnumData]].


## Konfigurasi Enum

Setiap Enum memiliki atribut berikut:

| Atribut | Penjelasan |
| --- | --- |
| [[^field|Name]] | Nama Enum. Tidak boleh sama dengan komponen sejenis di folder yang sama. |
| [[^field|Description]] | Keterangan singkat tentang kegunaan Enum. |
| [[^field|Format]] | Format data untuk kolom [[^field|Value]] pada setiap baris. Format dapat diubah setelah Enum dibuat (lihat [[#Mengubah Enum]]). |
| [[^field|Header]] | Header untuk [[^field|Format]] dengan tipe data yang membutuhkan header. Bernilai N/A jika [[^field|Format]] tidak membutuhkannya. |
| [[^field|Strict On Selected]] | Pengaturan ketegasan pilihan. Selengkapnya lihat [[Docs/Modul Data/Enum/Konfigurasi Tegas]]. |

Pasangan tipe data [[^field|Format]] dan [[^field|Header]]:

| Tipe data Format | Tipe data Header |
| --- | --- |
| [[Docs/Tipe Data/EnumData|EnumData]] | [[Docs/Tipe Data/Enum|Enum]] |
| [[Docs/Tipe Data/Column|Column]] | [[Docs/Tipe Data/Table|Table]] |
| [[Docs/Tipe Data/Row|Row]] | [[Docs/Tipe Data/Table|Table]] |
| [[Docs/Tipe Data/TableData|TableData]] | [[Docs/Tipe Data/Column|Column]] |
| [[Docs/Tipe Data/Node|Node]] | [[Docs/Tipe Data/Tree|Tree]] |
| Lainnya | N/A |

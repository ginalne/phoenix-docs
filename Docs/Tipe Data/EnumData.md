---
    status: draft
    pageDecoration:
      icon: x
      tree:
        priority: 0
---
# EnumData
EnumData adalah tipe data yang berisi data dari [[Docs/Modul Data/Enum/Apa itu Enum|Enum]].

## Attribute
![[Docs/Tipe Data/enum-data.png|Contoh halaman kerja Enum]]
Setiap EnumData memiliki atribut sebagai berikut:
* [[#Name]]
* [[#Description]]
* [[#Value]]
* [[#Selectable]]

### Name
Name adalah *key* dalam EnumData, setiap EnumData tidak boleh memiliki nama yang sama. Atribut ini akan tampil saat dalam pilihan.

### Description
Description adalah atribut teks yang menjadi keterangan pada EnumData, setiap . Atribut ini akan tampil saat dalam pilihan (terkadang opsional). Setiap EnumData boleh memiliki deskripsi yang sama.

## Penggunaan dalam Interface
EnumData cukup baik dalam menyimpan data opsional, sehingga dapat digunakan secara interaktif dengan interface [[Docs/Modul Interface/Kanban/Apa itu Kanban|Kanban]]

## Format
>**note** Tipe data ini tidak memiliki format khusus.


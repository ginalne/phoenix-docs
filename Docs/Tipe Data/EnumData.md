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
*Key* dalam EnumData, setiap EnumData tidak boleh memiliki nama yang sama. Atribut ini akan tampil saat dalam pilihan.

### Description
Atribut teks yang menjadi keterangan pada EnumData, setiap EnumData boleh memiliki deskripsi yang sama. Atribut ini akan tampil saat dalam pilihan (terkadang opsional).

### Value
Atribut tambahan yang bisa dapat diakses dan berguna dalam proses logika seperti komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]].

### Selectable
Atribut dalam EnumData sebagai status pemilihan, jika [[badge/yes|Yes]] maka EnumData ini akan muncul dalam pilihan saat dipilih.

## Penggunaan dalam Interface
EnumData cukup baik dalam menyimpan data opsional, sehingga dapat digunakan secara interaktif dengan interface [[Docs/Modul Interface/Kanban/Apa itu Kanban|Kanban]]

## Format
>**note** Tipe data ini tidak memiliki format khusus.


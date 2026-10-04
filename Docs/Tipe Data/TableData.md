---
    status: release
    title: "TableData"
    description: 
    pageDecoration:
      tree:
        priority: 0
---
# TableData
TableData adalah tipe data khusus yang digunakan oleh komponen [[Docs/Modul Data/Table/Apa itu Table|Table]].

## Attribute
![[Docs/Tipe Data/enum-data.png|Contoh halaman kerja Enum]]
Setiap [[Docs/Tipe Data/TableData]] memiliki atribut sebagai berikut:
* [[#Name]]
* [[#Description]]
* [[#Value]]
* [[#Selectable]]

### Name
Atribut Enum sebagai *Key* dalam item [[Docs/Tipe Data/EnumData]], setiap EnumData tidak boleh memiliki nama yang sama. Atribut ini akan tampil saat dalam pilihan.

### Description
Atribut Enum berbentuk [[Docs/Tipe Data/Text]] yang menjadi keterangan pada item EnumData, setiap EnumData boleh memiliki deskripsi yang sama. Atribut ini akan tampil saat dalam pilihan (terkadang opsional).

### Value
Atribut tambahan yang bisa dapat diisi, diakses dan berguna dalam proses logika seperti komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]].

### Selectable
Atribut Enum berbentuk [[Docs/Tipe Data/Boolean]] dalam EnumData sebagai status pemilihan, jika [[value/boolean/true|Yes]] maka EnumData ini akan muncul dalam pilihan saat dipilih.

## Penggunaan dalam Interface
EnumData cukup baik dalam menyimpan data opsional, sehingga dapat digunakan secara interaktif dengan interface seperti [[Docs/Modul Interface/Kanban/Apa itu Kanban|Kanban]]

## Format
>**note** Tipe data ini tidak memiliki format khusus.


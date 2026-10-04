---
    status: release
    title: "EnumData"
    description: 
    pageDecoration:
      tree:
        priority: 0
---
# EnumData
Tipe data yang berisi data dari [[Docs/Modul Data/Enum/Apa itu Enum|Enum]].

## Attribute
![[Docs/Tipe Data/enum-data.png|Contoh halaman kerja Enum]]
Setiap EnumData memiliki atribut sebagai berikut:
* [[#Name]]
* [[#Description]]
* [[#Value]]
* [[#Selectable]]

### Name
Atribut Enum sebagai *Key* dalam item EnumData, setiap EnumData tidak boleh memiliki nama yang sama. Atribut ini akan tampil saat dalam pilihan.

### Description
Atribut Enum berbentuk [[Docs/Tipe Data/Text]] yang menjadi keterangan pada item EnumData, setiap EnumData boleh memiliki deskripsi yang sama. Atribut ini akan tampil saat dalam pilihan (terkadang opsional).

### Value
Atribut tambahan yang bisa dapat diisi, diakses dan berguna dalam proses logika seperti komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]].

### Selectable
Atribut Enum berbentuk [[Docs/Tipe Data/Boolean]] dalam EnumData sebagai status pemilihan, jika [[value/boolean/true|Yes]] maka EnumData ini akan muncul dalam pilihan saat dipilih.

## Penggunaan dalam Interface
EnumData cukup baik dalam menyimpan data opsional, sehingga dapat digunakan secara interaktif dengan interface seperti [[Docs/Modul Interface/Kanban/Apa itu Kanban|Kanban]]

## Format
* [[Docs/Format Data/EnumData/Dropdown]]
* [[Docs/Format Data/EnumData/Multiple Choices]]

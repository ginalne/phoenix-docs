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

Setiap [[Docs/Tipe Data/TableData]] memiliki atribut sebagai berikut:
* [[#Row]]
* [[#Column]]
* [[#Type]]
* [[#Val]]

### Row

Atribut yang berelasi dengan [[Docs/Tipe Data/Row]] dalam [[Docs/Modul Data/Table/Apa itu Table|Table]].

### Column

Atribut yang berelasi dengan [[Docs/Tipe Data/Column]] dalam [[Docs/Modul Data/Table/Apa itu Table|Table]].

### Type

Atribut yang terisi otomatis dan sesuai dengan Type dalam [[Docs/Tipe Data/Column]]. Perubahan Type dalam TabelData tidak dapat diubah secara langsung, akan tetapi harus dengan mengubahnya melalui [[Docs/Tipe Data/Column]] yang terelasi. 

### Value
Atribut tambahan yang bisa dapat diisi, diakses dan berguna dalam proses logika seperti komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]].

### Selectable
Atribut Enum berbentuk [[Docs/Tipe Data/Boolean]] dalam EnumData sebagai status pemilihan, jika [[value/boolean/true|Yes]] maka EnumData ini akan muncul dalam pilihan saat dipilih.

## Penggunaan dalam Interface
EnumData cukup baik dalam menyimpan data opsional, sehingga dapat digunakan secara interaktif dengan interface seperti [[Docs/Modul Interface/Kanban/Apa itu Kanban|Kanban]]

## Format
>**note** Tipe data ini tidak memiliki format khusus.


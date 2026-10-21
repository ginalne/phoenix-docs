---
    status: release
    title: "Cara Kerja Enum"
    description: Penjelasan cara kerja komponen Enum
    pageDecoration:
      tree:
        priority: 3
    tags:
      draft
---
# Cara Kerja Enum

Enum menyimpan banyak [[Docs/Tipe Data/EnumData]], lalu field berformat [[Docs/Tipe Data/EnumData]] di komponen lain menampilkan [[Docs/Tipe Data/EnumData]] tersebut sebagai daftar pilihan.

```mermaid
flowchart LR
  A["Enum"] -->|"&nbsp;berisi banyak&nbsp;"| B["EnumData"]
  C["Field berformat EnumData"] -.->|"&nbsp;merujuk ke&nbsp;"| A
  B -->|"&nbsp;tampil sebagai pilihan&nbsp;<br>&nbsp;(Selectable = Yes)&nbsp;"| C
```

Hanya [[Docs/Tipe Data/EnumData]] dengan [[^field|Selectable]] bernilai [[^value/boolean/true]] yang tampil pada daftar pilihan. [[Docs/Tipe Data/EnumData]] dengan nilai [[^value/boolean/false]] tidak tampil sebagai pilihan di field, tetapi tetap dapat dipakai di tempat lain.
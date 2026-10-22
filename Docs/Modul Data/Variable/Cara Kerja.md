---
    status: release
    title: "Cara Kerja Variable"
    description: Penjelasan cara kerja komponen Variable
    pageDecoration:
      tree:
        priority: 3
    tags:
      draft
---
# Cara Kerja Variable

Variable adalah satu sumber data yang dikenali oleh semua komponen di dalam ruang lingkup Pro.
```mermaid
flowchart TB
    V -.->|"Value"| L["Komponen di Modul Logic"]
    P["Pro"] -->|"Membuat otomatis"| V["Komponen Variable"]
    L -.->|"Alias Valid"| V
    V -->|"Name dan Desc<br>(pilihan)"| F["Field bertipe Variable (komponen lain)"]
    L -.->|"Alias tidak valid"| A["Nilai Kosong atau Error"]
```

Ada dua cara komponen merujuk ke Variable:

- **Field bertipe Variable.** Pada komponen yang memiliki field dengan [[Docs/Tipe Data/Variable|tipe data Variable]], pilihannya adalah daftar [[^field|Name]] dan [[^field|Description]] dari Variable Data.
- **Komponen di modul Logic.** Komponen dalam [[Docs/Modul Logic]] dapat mengisi field Variable cukup dengan [[^field|Alias]]. Jika [[^field|Alias]] tidak valid di Variable (tidak ada [[^field|Nama]] yang cocok), maka tidak ada nilai yang diterima atau error.
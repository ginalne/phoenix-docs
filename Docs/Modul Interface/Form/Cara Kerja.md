---
    status: release
    title: "Cara Kerja Form"
    description: Penjelasan cara kerja komponen Form
    pageDecoration:
      tree:
        priority: 9
    tags:
      draft
---
# Cara Kerja Form

Form tersusun dari [[#Mengelola Page Form|Page]], setiap Page tersusun dari [[#Memahami Elemen|Elemen]], dan Elemen yang diikat lewat [[#Binding Form|Binding]] menghubungkan isian Form ke [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]].

```mermaid
flowchart LR
  A["Form"] -->|&nbsp;Memiliki&nbsp;| B["Page"]
  B -->|&nbsp;Tersusun dari&nbsp;| C["Elemen"]
  C -.->|&nbsp;Binding&nbsp;| D["Row"]
  A -.->|&nbsp;Publish&nbsp;| E["Pengguna publik"]
  E -->|&nbsp;Submission&nbsp;| D
```

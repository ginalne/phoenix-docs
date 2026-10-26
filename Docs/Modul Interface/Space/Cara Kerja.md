---
    status: release
    title: "Cara Kerja Space"
    description: Penjelasan cara kerja komponen Space
    pageDecoration:
      tree:
        priority: 3
    tags:
      draft
---
# Cara Kerja Space

Space menaungi data Weather, Environment, dan Object lalu menampilkannya bersama dalam satu ruang 3D, dengan Weather dan Object mengambil nilainya dari [[Docs/Tipe Data/Query]] sedangkan Environment memakai file 3D.

```mermaid
flowchart LR
  W["Workspace"] -->|"&nbsp;Data Access&nbsp;"| S["Space"]
  S --> A["Weather"]
  S --> B["Environment"]
  S --> C["Object"]
  T["Table"] -.->|"&nbsp;Query Single Output&nbsp;"| A
  T -.->|"&nbsp;Query Table Output&nbsp;"| C
  M["Model<br/>(modul Developer)"] -->|"&nbsp;Model&nbsp;"| C
  F["File 3D"] -->|"&nbsp;Upload&nbsp;"| B
```

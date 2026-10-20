---
    status: release
    title: "Cara Kerja Table View"
    description: Penjelasan cara kerja komponen Table View
    pageDecoration:
      tree:
        priority: 3
    tags:
      draft
---
# Cara Kerja Table View

Tree menyimpan [[Docs/Tipe Data/Node]] secara bertingkat, dan hanya Tree dengan Merger Mode yang dapat menambahkan Node dari Tree lain.

```mermaid
flowchart LR
    M["**Tree Merger Mode**"] -->|"&nbsp;memiliki&nbsp;"| N1["Node"]
    M -->|"&nbsp;memiliki&nbsp;"| N4["Node"]
    N2["Node"] -.->|"&nbsp;Clone&nbsp;"| N1
    N3["Node"] -.->|"&nbsp;Clone&nbsp;"| N4
    A["**Tree Non-Merger**<br>Read Only"] -->|"&nbsp;memiliki&nbsp;"| N2
    B["**Tree Non-Merger**<br>"] -->|"&nbsp;memiliki&nbsp;"| N3
    N4["Node"] -.->|"&nbsp;Perubahan&nbsp;"| N3
```

Tree yang tidak bersifat merger tidak dapat menambahkan Node dari Tree lain. Node *clone* di Tree penggabung dapat dibuat dengan atau tanpa mengikuti perubahan Node asalnya, dan pilihan ini berkaitan dengan [[#External Read Only]]. Selengkapnya lihat [[Docs/Modul Data/Tree/Konfigurasi Merger Mode]].
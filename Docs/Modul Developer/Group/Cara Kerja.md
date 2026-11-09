---
    status: release
    title: "Cara Kerja Group"
    description: Penjelasan cara kerja komponen Group
    pageDecoration:
      tree:
        priority: 3
---
# Cara Kerja Group

User menjadi anggota Group, dan Group menentukan Workspace yang dapat diakses oleh seluruh anggotanya.

```mermaid
flowchart LR
    U["User"] -->|"&nbsp;Anggota&nbsp;"| G["Group"]
    G -->|"&nbsp;Akses&nbsp;"| W["Workspace"]
    G -.->|"&nbsp;Anak&nbsp;"| C["Group Anak"]
    C -->|"&nbsp;Akses&nbsp;"| W
```

Setiap Group, termasuk Group anak, memiliki daftar Workspace sendiri. Group anak tidak mewarisi Workspace dari Group induk, sehingga Workspace perlu ditambahkan kembali pada setiap Group.
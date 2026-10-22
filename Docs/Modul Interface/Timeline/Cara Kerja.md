---
    status: release
    title: "Cara Kerja Timeline"
    description: Penjelasan cara kerja komponen Timeline
    pageDecoration:
      tree:
        priority: 4
---
# Cara Kerja Timeline

Timeline mempertemukan dua hal dalam satu sumbu waktu: Timeline Event yang memicu Pulser sesuai jadwal, dan Timeline Data yang menampilkan Row dari data sumber berdasarkan Query.
```mermaid
flowchart LR
    A["Timeline"] -->|"&nbsp;memiliki&nbsp;"| TE["Timeline Event"]
    TE -.->|"&nbsp;memicu&nbsp;"| PL["Pulser"]
    
    A -..->|"&nbsp;memiliki&nbsp;"| B["Timeline Data<br>( editable )"]
    A -..->|"&nbsp;memiliki&nbsp;"| C["Timeline Data<br>( readonly )"]
    A -..->|"&nbsp;memiliki&nbsp;"| D["Timeline Data<br>( editable )"]
    
    B -->|&nbsp;Query&nbsp;| X
    C -->|&nbsp;Query&nbsp;| Y
    D -->|&nbsp;Query&nbsp;| Z

    X["Table A"] --> F["Row<br>( editable )"]
    Y["Table B"] --> G["Row<br>( readonly )"]
    Z["Table C"] --> H["Row<br>( readonly )"]
    W["Workspace : Data Access"] -->|&nbsp;allow&nbsp;| X
    W -->|&nbsp;allow&nbsp;| Y
    W -->|&nbsp;disallow&nbsp;| Z
```

Row hanya dapat diubah dari Timeline bila dua syarat terpenuhi: Timeline Data berada pada mode `editable` dan Data Access data sumber di Workspace mengizinkan. Lihat [[#Hak Akses Timeline Data]].

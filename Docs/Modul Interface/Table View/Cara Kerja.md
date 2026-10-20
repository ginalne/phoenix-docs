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

Table View menjalankan [[Docs/Tipe Data/Query|Query]] pada setiap Data, lalu menampilkan hasilnya sebagai tabel [[Docs/Tipe Data/Row]] yang dapat dikelola langsung (_editable_) atau hanya dapat dibaca (_readonly_).

```mermaid
flowchart LR
    A["Table View"] -..-> B["TableView Data<br>( editable )"]
    A -..-> C["TableView Data<br>( readonly )"]
    A -..-> D["TableView Data<br>( editable )"]
    B -->|&nbsp;Query&nbsp;| X
    C -->|&nbsp;Query&nbsp;| Y
    D -->|&nbsp;Query&nbsp;| Z

    X["Table A"] --> F["Table Row<br>( editable )"]
    Y["Table B"] --> G["Table Row<br>( readonly )"]
    Z["Table C"] --> H["Table Row<br>( readonly )"]
    W -->|&nbsp;allow&nbsp;| Y
    W -->|&nbsp;disallow&nbsp;| Z
    W["Workspace : Data Access"] -->|&nbsp;allow&nbsp;| X
```
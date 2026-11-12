---
    status: release
    title: "Menghapus Node"
    description: 
status: draft
title: Menghapus Node
description: Cara menghapus Node dari Tree beserta dampaknya pada Node anak.
pageDecoration:
  tree:
    priority: 7
---
# Menghapus Node

Menghapus [[Docs/Tipe Data/Node|Node]] berarti membuangnya dari [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]. Node dihapus lewat Node induknya, sehingga Origin tidak dapat dihapus karena tidak memiliki induk.

## Langkah Menghapus

1. Buka halaman kerja [[Docs/Modul Data/Tree/Apa itu Tree|Tree]].
2. Klik kanan [[Docs/Tipe Data/Node|Node]] induk dari Node yang akan dihapus ➜ [[^field/edit|Edit]].
3. Pada bagian [[^field|Children]], klik [[^button/delete|Delete]] pada Node yang akan dihapus.
4. Konfirmasi dengan klik [[^button|Delete]].

>**danger** Penghapusan tidak dapat dikembalikan
> Node yang dihapus tidak dapat dipulihkan. Seluruh Node anak dan keturunannya ikut terhapus.

>**warning** Node yang sedang digunakan
> Penghapusan ditolak bila Node, atau Node anak yang ikut terhapus, sedang digunakan komponen lain, misalnya [[Docs/Tipe Data/Column|Column]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]] yang berformat [[Docs/Tipe Data/Node|Node]]. Lepaskan penggunaannya lebih dulu.

>**warning** Node hasil clone di Tree merger
> Menghapus Node pada Tree non-merger ikut menghapus Node hasil *clone* di Tree merger. Sebaliknya, menambahkan atau menghapus Node hasil *clone* di Tree merger tidak memengaruhi Tree sumber.

>**note** Hak akses dan Event
> Menghapus Node memerlukan [[Docs/Modul Developer/Workspace/Data Access#Data yang Diatur pada Setiap Komponen|Data Access]] Delete pada Tree: Node bernilai [[^value/boolean/allow]]. Menghapus Node yang memiliki anak menghasilkan satu event [[^value/string|delete]] pada Node itu di [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]], dengan seluruh Children tercatat di `Old`.

## Lihat Juga

- [[Docs/Modul Data/Tree/Node/Mengimpor|Mengimpor Node]] untuk mengisi kembali Node dari file.
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Delete Node|Delete Node Block]] untuk menghapus Node lewat Flow.
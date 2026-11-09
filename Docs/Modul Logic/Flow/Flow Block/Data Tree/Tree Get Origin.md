---
status: draft
title: Tree Get Origin Block
description: Flow Block Data Tree yang mengambil Node Origin dari sebuah Tree.
pageDecoration:
  tree:
    priority: 13
---

# Tree Get Origin Block

>**note** Tree Get Origin Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Tree Get Origin Block adalah Flow Block yang mengambil [[Docs/Tipe Data/Node]] Origin dari sebuah [[Docs/Tipe Data/Tree]]. Setiap Tree yang baru dibuat otomatis memiliki Node Origin sebagai Node awal, dan block ini menjadikannya titik awal bagi Flow, misalnya untuk menambahkan Node langsung di bawah Origin.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/tree-get-origin-block-flow.png|Tree Get Origin Block pada Blueprint Flow]]

## Input dan Output

Tree Get Origin Block memiliki 1 input di sisi kiri, 1 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Tree]] | [[Docs/Tipe Data/Tree]] | Pilih Tree atau hubungkan dari output block lain. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|The Origin (Node)]] | [[Docs/Tipe Data/Node]] | Node Origin dari Tree yang diinput. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Isi [[^input|Tree]] dengan [[Docs/Tipe Data/Tree]] atau hubungkan dari output block lain.
2. Saat dieksekusi, [[^output|The Origin (Node)]] mengeluarkan Node Origin Tree tersebut.
3. Hubungkan output ke block berikutnya, misalnya ke input [[^input|Parent]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]].

## Contoh Penggunaan

Tabel berikut menunjukkan hasil Tree Get Origin Block pada Tree Kategori Produk.

| Kondisi | The Origin (Node) | Status |
| ------- | ----------------- | ------ |
| Tree terisi | [[^value/node|Origin]] | [[^flowstate|Succeed]] |
| [[^input|Tree]] dibiarkan kosong | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Hubungkan **[[^output|The Origin (Node)]]** ke [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]] untuk menambahkan Node langsung di bawah Origin, atau ke [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]] untuk membaca anak pertama Tree.

## Batasan dan Catatan

- Setiap Tree memiliki Node Origin sehingga block ini tidak memiliki output Not Found.
- [[^input|Tree]] yang kosong membuat block berstatus [[^flowstate|Fatal Error]] dan output tidak ada.
- Karena bukan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]], Tree Get Origin Block hanya dieksekusi bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree|Tree Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]]
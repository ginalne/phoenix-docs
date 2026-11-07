---
    status: draft
    title: Tree Get Origin Block
    description: Flow Block Data Tree yang mengambil Node Origin dari sebuah Tree.
---
# Tree Get Origin Block

>**note** Tree Get Origin Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam kategori Data di komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Tree Get Origin Block adalah Flow Block yang mengambil [[Docs/Modul Data/Tree/Apa itu Tree|Node Origin]] dari sebuah [[Docs/Tipe Data/Tree]]. Origin adalah titik awal setiap Tree, sehingga block ini menjadi pintu masuk untuk menelusuri atau menambah [[Docs/Tipe Data/Node]] dari akar Tree.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/tree-get-origin-block-flow.png|Tree Get Origin Block pada Blueprint Flow]]
## Input dan Output

Block ini tidak memiliki Control. Block hanya memiliki input di sisi kiri dan output di sisi kanan.

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Tree]] | [[Docs/Tipe Data/Tree]] | Tree yang Origin-nya akan diambil. Isi dengan Tree atau hubungkan dari output block lain. Wajib diisi. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|The Origin]] | [[Docs/Tipe Data/Node]] | Node Origin dari Tree yang diinput. |

Saat berhasil, [[^output|The Origin]] meneruskan aliran. Saat [[^flowstate|Fatal Error]], [[^output|The Origin]] tidak meneruskan aliran. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block menerima [[Docs/Tipe Data/Tree]] dari [[^input|Tree]].
2. Block mengambil Node Origin dari Tree tersebut. Setiap Tree yang baru dibuat otomatis memiliki satu Node bernama Origin.
3. Block meneruskan Node Origin lewat [[^output|The Origin]].
4. Bila [[^input|Tree]] dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]], pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]], dan tidak ada output yang meneruskan aliran.

## Contoh Penggunaan

Tabel berikut menunjukkan hasil block pada setiap kondisi input.

| Peristiwa | Status | [[^output|The Origin]] |
| - | - | - |
| [[^input|Tree]] terisi | [[^flowstate|Succeed]] | Node Origin dari Tree |
| [[^input|Tree]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - |

## Praktik Terbaik

- **Mulai penelusuran dari [[^output|The Origin]].** Hubungkan ke [[^input|Node]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]] untuk turun ke level pertama Tree.
- **Tambahkan Node level pertama dengan Origin sebagai Parent.** Hubungkan [[^output|The Origin]] ke [[^input|Parent]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]].
- **Ambil [[Docs/Tipe Data/Tree]] dari block lain.** Hubungkan [[^output|Tree]] dari [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]] ke [[^input|Tree]] agar block ini bekerja pada Tree tempat Node berada.

## Batasan dan Catatan

- Block ini tidak memiliki output [[^output|Not Found]] karena setiap Tree memiliki Node Origin.
- Bila [[^input|Tree]] kosong, block berstatus [[^flowstate|Fatal Error]] dan seluruh output tidak ada.
- Block hanya membaca dan tidak mengubah [[Docs/Tipe Data/Tree]].
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree|Tree Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]]

<!--
  * [TODO] Konfirmasi label output persis: `The Origin` (huruf besar pada kata The mengikuti tulisan penulis).
  * [TODO] Konfirmasi perilaku pada Tree Merger: apakah Node Origin yang diambil adalah Origin milik Tree Merger itu sendiri.
-->

<!--
  * [TODO] Halaman yang ditautkan dan mungkin belum ada: `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan anchor `Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output`.
-->
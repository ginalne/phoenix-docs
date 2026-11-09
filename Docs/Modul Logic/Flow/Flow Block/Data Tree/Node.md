---
    status: draft
    title: Node Block
    description: Flow Block Data Tree yang mengambil atribut Node, yaitu Order, Name, dan Tree.
    pageDecoration:
      tree:
        priority: 18
---
# Node Block

>**note** Node Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Node Block adalah Flow Block yang menerima sebuah [[Docs/Tipe Data/Node]] lalu mengeluarkan atribut Node tersebut, yaitu Order, Name, dan Tree tempat Node berada. Gunakan block ini bila Flow membutuhkan informasi sebuah Node sebelum memprosesnya lebih lanjut.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/node-block-flow.png|Node Block pada Blueprint Flow]]
## Input dan Output

Node Block memiliki 1 input di sisi kiri, 4 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Pilih Node atau hubungkan dari output block lain. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Pass]] | [[Docs/Tipe Data/Node]] | Meneruskan Node yang diinput. |
| [[^output|Tree]] | [[Docs/Tipe Data/Tree]] | Tree tempat Node berada. |
| [[^output|Order]] | [[Docs/Tipe Data/Number]] | Order Node di antara saudara kandungnya. |
| [[^output|Name]] | [[Docs/Tipe Data/String]] | Name Node. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Isi [[^input|Node]] dengan [[Docs/Tipe Data/Node]] atau hubungkan dari output block lain.
2. Saat dieksekusi, [[^output|Pass]] meneruskan Node yang diinput, sedangkan [[^output|Tree]], [[^output|Order]], dan [[^output|Name]] mengeluarkan atribut Node tersebut.
3. Hubungkan output yang Anda butuhkan ke block berikutnya.

## Contoh Penggunaan

Tabel berikut menunjukkan hasil Node Block pada Tree Kategori Produk.

| Kondisi | Pass | Tree | Order | Name | Status |
| ------- | ---- | ---- | ----- | ---- | ------ |
| Node yang berada di bawah Node lain | [[^value/node|Ponsel]] | [[^value/tree|Kategori Produk]] | [[^value/number|1]] | [[^value/string|Ponsel]] | [[^flowstate|Succeed]] |
| Node yang menjadi anak pertama | [[^value/node|Komputer]] | [[^value/tree|Kategori Produk]] | [[^value/number|0]] | [[^value/string|Komputer]] | [[^flowstate|Succeed]] |
| [[^input|Node]] dibiarkan kosong | - | - | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Gunakan **[[^output|Tree]]** untuk menghubungkan Node ke [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree|Tree Block]] bila Flow membutuhkan informasi Tree tempat Node berada.
- Hubungkan **[[^output|Pass]]** ke block berikutnya bila Flow masih membutuhkan Node yang sama.

## Batasan dan Catatan

- Node Block tidak mengeluarkan parent maupun anak Node. Untuk menelusuri hubungan Node, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]], [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]], atau [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]].
- [[^input|Node]] yang kosong membuat block berstatus [[^flowstate|Fatal Error]] dan semua output tidak ada.
- Karena bukan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]], Node Block hanya dieksekusi bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree|Tree Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]]


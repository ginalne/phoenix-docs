---
    status: draft
    title: Node Get Children Block
    description: Flow Block Data Tree yang mengambil anak langsung sebuah Node berdasarkan Order.
    pageDecoration:
      tree:
        priority: 11
---
# Node Get Children Block

>**note** Node Get Children Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Node Get Children Block adalah Flow Block yang mengambil anak langsung sebuah [[Docs/Tipe Data/Node]] berdasarkan Order yang ditentukan. Gunakan block ini untuk membaca isi satu tingkat di bawah Node, misalnya mengambil subkategori pertama dari sebuah kategori.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/node-get-children-block-flow.png|Node Get Children Block pada Blueprint Flow]]
## Input dan Output

Node Get Children Block memiliki 2 input di sisi kiri, 2 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Node yang anaknya diambil. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |
| [[^input|Child Order]] | [[Docs/Tipe Data/Number]] | Order anak yang dicari. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|The Children (Node)]] | [[Docs/Tipe Data/Node]] | Anak langsung Node yang memiliki Order sesuai Child Order. Keluar bila anak ditemukan. |
| [[^output|Not Found]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Node tidak memiliki anak dengan Order sesuai Child Order. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Isi [[^input|Node]] dan [[^input|Child Order]], langsung pada block atau dari output block lain.
2. Block mencari anak langsung Node yang memiliki Order sesuai [[^input|Child Order]].
3. Bila anak ditemukan, hanya [[^output|The Children (Node)]] yang meneruskan aliran.
4. Bila tidak ditemukan, hanya [[^output|Not Found]] yang meneruskan aliran.

## Contoh Penggunaan

Tabel berikut memakai Node [[^value/node|Elektronik]] yang memiliki anak [[^value/node|Komputer]] (Order [[^value/number|0]]) dan [[^value/node|Ponsel]] (Order [[^value/number|1]]). Node [[^value/node|Laptop]] adalah anak dari [[^value/node|Komputer]].

| Kondisi | The Children (Node) | Not Found | Status |
| ------- | ------------------- | --------- | ------ |
| Child Order [[^value/number|0]] | [[^value/node|Komputer]] | - | [[^flowstate|Succeed]] |
| Child Order [[^value/number|1]] | [[^value/node|Ponsel]] | - | [[^flowstate|Succeed]] |
| Child Order [[^value/number|2]], tidak ada anak dengan Order tersebut | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| Node [[^value/node|Laptop]] tidak memiliki anak, Child Order [[^value/number|0]] | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| [[^input|Node]] atau [[^input|Child Order]] dibiarkan kosong | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Error]] dan [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Untuk menelusuri lebih dalam, hubungkan **[[^output|The Children (Node)]]** ke Node Get Children Block berikutnya, satu tingkat untuk setiap block.
- Gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]] bila Anda ingin mengambil Node pada silsilah dari Origin menuju sebuah Node.

## Batasan dan Catatan

- Block ini hanya mengambil anak langsung. Node pada tingkat yang lebih dalam tidak ikut diambil.
- Satu eksekusi hanya mengeluarkan satu anak, yaitu anak dengan Order yang diinput.
- Karena bukan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]], Node Get Children Block hanya dieksekusi bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]]
---
    status: draft
    title: Node Get Parent Block
    description: Flow Block Data Tree yang menelusuri parent sebuah Node ke atas berdasarkan Depth.
    pageDecoration:
      tree:
        priority: 12
---
# Node Get Parent Block

>**note** Node Get Parent Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Node Get Parent Block adalah Flow Block yang menelusuri parent sebuah [[Docs/Tipe Data/Node]] ke arah Origin sejauh Depth yang ditentukan. Gunakan block ini untuk mengetahui induk sebuah Node, misalnya mencari kategori induk dari sebuah kategori.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/node-get-parent-block-flow.png|Node Get Parent Block pada Blueprint Flow]]
## Input dan Output

Node Get Parent Block memiliki 2 input di sisi kiri, 2 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Node yang parent-nya ditelusuri. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |
| [[^input|Depth]] | [[Docs/Tipe Data/Number]] | Jumlah tingkat penelusuran ke atas. [[^value/number|1]] menghasilkan parent langsung Node, [[^value/number|2]] menghasilkan parent dari parent, dan seterusnya. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|The Parent (Node)]] | [[Docs/Tipe Data/Node]] | Parent hasil penelusuran sesuai Depth. Keluar bila parent ditemukan. |
| [[^output|Not Found]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila parent tidak ditemukan, yaitu bila Depth kurang dari [[^value/number|1]], Depth melebihi kedalaman Node, atau Node adalah Origin. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Isi [[^input|Node]] dan [[^input|Depth]], langsung pada block atau dari output block lain.
2. Block menelusuri parent Node ke atas sebanyak Depth tingkat.
3. Bila parent ditemukan, hanya [[^output|The Parent (Node)]] yang meneruskan aliran.
4. Bila tidak ditemukan, hanya [[^output|Not Found]] yang meneruskan aliran.

## Contoh Penggunaan

Tabel berikut memakai Node [[^value/node|Laptop]] pada silsilah Origin ➜ Elektronik ➜ Komputer ➜ Laptop.

| Kondisi | The Parent (Node) | Not Found | Status |
| ------- | ----------------- | --------- | ------ |
| Depth [[^value/number|1]] | [[^value/node|Komputer]] | - | [[^flowstate|Succeed]] |
| Depth [[^value/number|2]] | [[^value/node|Elektronik]] | - | [[^flowstate|Succeed]] |
| Depth [[^value/number|3]] | [[^value/node|Origin]] | - | [[^flowstate|Succeed]] |
| Depth [[^value/number|4]], melebihi kedalaman Node | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| Depth [[^value/number|0]], kurang dari [[^value/number|1]] | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| Node yang diinput adalah Origin, Depth [[^value/number|1]] | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| [[^input|Node]] atau [[^input|Depth]] dibiarkan kosong | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Error]] dan [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Gunakan Node Get Parent Block bila Anda menghitung dari Node ke atas, dan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]] bila Anda menghitung dari Origin ke bawah.

## Batasan dan Catatan

- Penelusuran dihitung dari Node yang diinput ke arah Origin, dan [[^value/number|1]] adalah parent langsung.
- Node Origin tidak memiliki parent sehingga selalu menghasilkan [[^output|Not Found]].
- Karena bukan Flow Block Event, Node Get Parent Block hanya dieksekusi bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]]


---
    status: draft
    title: Node Get Ancestor Block
    description: Flow Block Data Tree yang mengambil leluhur sebuah Node berdasarkan Anc. Level, dihitung dari Origin.
    pageDecoration:
      tree:
        priority: 13
---

# Node Get Ancestor Block

>**note** Node Get Ancestor Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Node Get Ancestor Block adalah Flow Block yang mengambil leluhur sebuah [[Docs/Tipe Data/Node]] pada silsilah dari Origin menuju Node tersebut. Gunakan block ini untuk mengetahui Node yang berada pada tingkat tertentu dalam silsilah, misalnya kategori utama dari sebuah kategori.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/node-get-ancestor-block-flow.png|Node Get Ancestor Block pada Blueprint Flow]]
## Input dan Output

Node Get Ancestor Block memiliki 2 input di sisi kiri, 2 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Node yang leluhurnya diambil. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |
| [[^input|Anc. Level]] | [[Docs/Tipe Data/Number]] | Tingkat leluhur yang diambil, dihitung dari Origin. [[^value/number|1]] menghasilkan Origin, [[^value/number|2]] menghasilkan Node berikutnya pada silsilah, dan seterusnya. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|The Ancestor (Node)]] | [[Docs/Tipe Data/Node]] | Leluhur pada tingkat Anc. Level. Keluar bila leluhur ditemukan. |
| [[^output|Not Found]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Anc. Level kurang dari [[^value/number|1]] atau melebihi jumlah leluhur Node. Node yang diinput bukan leluhurnya sendiri sehingga tidak dapat ditemukan. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Isi [[^input|Node]] dan [[^input|Anc. Level]], langsung pada block atau dari output block lain.
2. Block menelusuri silsilah dari Origin menuju Node dan mengambil leluhur pada tingkat [[^input|Anc. Level]].
3. Bila leluhur ditemukan, hanya [[^output|The Ancestor (Node)]] yang meneruskan aliran.
4. Bila tidak ditemukan, hanya [[^output|Not Found]] yang meneruskan aliran.

<!--
  * [TODO] Konfirmasi: status block pada kasus Not Found diasumsikan Error (seperti Is Empty pada TableData Getter), tanpa output lain yang meneruskan aliran.
-->

## Contoh Penggunaan

Tabel berikut memakai Node [[^value/node|Laptop]] pada silsilah Origin ➜ Elektronik ➜ Komputer ➜ Laptop.

| Kondisi | The Ancestor (Node) | Not Found | Status |
| ------- | ------------------- | --------- | ------ |
| Anc. Level [[^value/number|1]] | [[^value/node|Origin]] | - | [[^flowstate|Succeed]] |
| Anc. Level [[^value/number|2]] | [[^value/node|Elektronik]] | - | [[^flowstate|Succeed]] |
| Anc. Level [[^value/number|3]] | [[^value/node|Komputer]] | - | [[^flowstate|Succeed]] |
| Anc. Level [[^value/number|4]], menunjuk Node itu sendiri | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| Anc. Level [[^value/number|0]], kurang dari [[^value/number|1]] | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| [[^input|Node]] atau [[^input|Anc. Level]] dibiarkan kosong | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Error]] dan [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Gunakan Node Get Ancestor Block bila Anda menghitung dari Origin ke bawah, dan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]] bila Anda menghitung dari Node ke atas.
- Gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]] bila Anda hanya membutuhkan Origin, tanpa perlu menentukan Node.

## Batasan dan Catatan

- Penelusuran dihitung dari Origin menuju Node yang diinput, dan [[^value/number|1]] adalah Origin.
- Node yang diinput bukan leluhurnya sendiri, sehingga tingkat yang menunjuk Node itu menghasilkan [[^output|Not Found]].
- Karena bukan Flow Block Event, Node Get Ancestor Block hanya dieksekusi bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]]
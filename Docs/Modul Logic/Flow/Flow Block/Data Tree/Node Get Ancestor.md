---
    status: draft
    title: Node Get Ancestor Block
    description: Flow Block Data Tree yang mengambil leluhur dari sebuah Node dengan menelusuri dari Origin sesuai Anc. Level.
---
# Node Get Ancestor Block

>**note** Node Get Ancestor Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam kategori Data di komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Node Get Ancestor Block adalah Flow Block yang mengambil leluhur dari sebuah [[Docs/Tipe Data/Node]] dengan menelusuri jalur dari Origin menuju Node tersebut. [[^input|Anc. Level]] menentukan leluhur yang diambil: nilai 1 menghasilkan leluhur pertama pada jalur dari Origin, dan nilai berikutnya menghasilkan leluhur selanjutnya.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/node-get-ancestor-block-flow.png|Node Get Ancestor Block pada Blueprint Flow]]
## Input dan Output

Block ini tidak memiliki Control. Block hanya memiliki input di sisi kiri dan output di sisi kanan.

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Node yang leluhurnya akan diambil. Pilih Node atau hubungkan dari output block lain. Wajib diisi. |
| [[^input|Anc. Level]] | [[Docs/Tipe Data/Number]] | Urutan leluhur pada jalur dari Origin ke Node. Wajib diisi. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|The Ancestor]] | [[Docs/Tipe Data/Node]] | Leluhur pada Anc. Level yang diinput. Hanya meneruskan aliran bila ditemukan. |
| [[^output|Not Found]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila leluhur tidak ditemukan. Hanya meneruskan aliran bila tidak ditemukan. |

Bila leluhur ditemukan, hanya [[^output|The Ancestor]] yang meneruskan aliran. Bila tidak ditemukan, hanya [[^output|Not Found]] yang meneruskan aliran. Saat [[^flowstate|Fatal Error]], tidak ada output yang meneruskan aliran. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block menerima [[Docs/Tipe Data/Node]] dari [[^input|Node]] dan [[Docs/Tipe Data/Number]] dari [[^input|Anc. Level]].
2. Block menelusuri jalur dari Origin menuju Node. [[^input|Anc. Level]] bernilai 1 menghasilkan leluhur pertama pada jalur tersebut, dan seterusnya sampai leluhur terakhir sebelum Node.
3. Bila leluhur pada level tersebut ada, block meneruskannya lewat [[^output|The Ancestor]].
4. Bila [[^input|Anc. Level]] kurang dari 1 atau melebihi jumlah leluhur pada jalur dari Origin ke Node, [[^output|Not Found]] bernilai [[^value/boolean/true]].
5. Bila [[^input|Node]] atau [[^input|Anc. Level]] dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]] dan tidak ada output yang meneruskan aliran.
6. Penelusuran ini dihitung dari Origin ke bawah. Untuk penelusuran yang dihitung dari Node ke atas, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]].

## Contoh Penggunaan

Contoh berikut memakai [[Docs/Tipe Data/Tree]] dengan jalur [[^value/node|Origin]] ➜ [[^value/node|Kategori]] ➜ [[^value/node|Subkategori]] ➜ [[^value/node|Produk]], dan [[^input|Node]] berisi [[^value/node|Produk]].

| Peristiwa | Status | [[^output|The Ancestor]] | [[^output|Not Found]] |
| - | - | - | - |
| [[^input|Anc. Level]] bernilai [[^value/number|1]] | [[^flowstate|Succeed]] | [[^value/node|Origin]] | - |
| [[^input|Anc. Level]] bernilai [[^value/number|2]] | [[^flowstate|Succeed]] | [[^value/node|Kategori]] | - |
| [[^input|Anc. Level]] bernilai [[^value/number|3]] | [[^flowstate|Succeed]] | [[^value/node|Subkategori]] | - |
| [[^input|Anc. Level]] bernilai [[^value/number|4]] (melebihi jumlah leluhur) | [[^flowstate|Succeed]] | - | [[^value/boolean/true]] |
| [[^input|Anc. Level]] kurang dari [[^value/number|1]] | [[^flowstate|Succeed]] | - | [[^value/boolean/true]] |
| [[^input|Node]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - | - |
| [[^input|Anc. Level]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - | - |

## Praktik Terbaik

- **Gunakan Anc. Level untuk posisi tetap dari Origin.** Misalnya Anc. Level 2 selalu mengambil Node level kedua pada jalur, berapa pun kedalaman Node yang diinput.
- **Hubungkan block penanganan langsung ke [[^output|Not Found]].** Misalnya [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]] untuk Node yang berada di level lebih dangkal dari yang Anda harapkan.
- **Pilih [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]] bila posisi dihitung dari Node.** Gunakan Node Get Ancestor bila posisi dihitung dari Origin.

## Batasan dan Catatan

- [[^input|Anc. Level]] dihitung dari Origin ke bawah, berbeda dengan [[^input|Depth]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]] yang dihitung dari Node ke atas.
- Node yang diinput tidak dihitung sebagai leluhurnya sendiri.
- [[^output|Not Found]] bukan error. Block berstatus [[^flowstate|Succeed]] dan Flow tetap berjalan pada jalur [[^output|Not Found]].
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]]

<!--
  * [TODO] Konfirmasi bahwa Node Origin dihitung sebagai [[^input|Anc. Level]] 1 (leluhur pertama dari Origin) dan bahwa Node yang diinput tidak dihitung sebagai leluhur. Contoh dan tabel mengikuti asumsi ini.
  * [TODO] Konfirmasi kondisi [[^output|Not Found]] untuk Node Origin (tidak memiliki leluhur): saya menulis [[^output|Not Found]] bernilai [[^value/boolean/true]] pada semua [[^input|Anc. Level]].
  * [TODO] Konfirmasi status block saat [[^input|Node]] atau [[^input|Anc. Level]] kosong. Saya menulis [[^flowstate|Fatal Error]] mengikuti block Data Tree lainnya.
  * [TODO] Konfirmasi status block saat [[^output|Not Found]]: saya menulis [[^flowstate|Succeed]].
  * [TODO] Nama Node pada contoh (Origin, Kategori, Subkategori, Produk) bersifat generik. Sesuaikan dengan gambar bila perlu.
-->

<!--
  * [TODO] Halaman yang ditautkan dan mungkin belum ada: `Docs/Modul Logic/Flow/Flow Block/Error/Error Message`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan anchor `Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output`.
-->
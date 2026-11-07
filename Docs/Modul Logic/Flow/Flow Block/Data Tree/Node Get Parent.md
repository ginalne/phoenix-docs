---
    status: draft
    title: Node Get Parent Block
    description: Flow Block Data Tree yang menelusuri Parent dari sebuah Node ke atas sesuai Depth.
---
# Node Get Parent Block

>**note** Node Get Parent Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam kategori Data di komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Node Get Parent Block adalah Flow Block yang menelusuri Parent dari sebuah [[Docs/Tipe Data/Node]] ke arah Origin. Anda menentukan seberapa jauh penelusuran lewat [[^input|Depth]]: Depth 1 menghasilkan Parent langsung, Depth 2 menghasilkan Parent dari Parent tersebut, dan seterusnya.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/node-get-parent-block-flow.png|Node Get Parent Block pada Blueprint Flow]]
## Input dan Output

Block ini tidak memiliki Control. Block hanya memiliki input di sisi kiri dan output di sisi kanan.

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Node yang akan ditelusuri Parent-nya. Pilih Node atau hubungkan dari output block lain. Wajib diisi. |
| [[^input|Depth]] | [[Docs/Tipe Data/Number]] | Jumlah tingkat penelusuran ke atas dari Node. Wajib diisi. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|The Parent]] | [[Docs/Tipe Data/Node]] | Node hasil penelusuran sesuai Depth. Hanya meneruskan aliran bila ditemukan. |
| [[^output|Not Found]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila Parent pada Depth tersebut tidak ditemukan. Hanya meneruskan aliran bila tidak ditemukan. |

Bila Parent ditemukan, hanya [[^output|The Parent]] yang meneruskan aliran. Bila tidak ditemukan, hanya [[^output|Not Found]] yang meneruskan aliran. Saat [[^flowstate|Fatal Error]], tidak ada output yang meneruskan aliran. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block menerima [[Docs/Tipe Data/Node]] dari [[^input|Node]] dan [[Docs/Tipe Data/Number]] dari [[^input|Depth]].
2. Block menelusuri Parent dari Node ke arah Origin sebanyak [[^input|Depth]] tingkat. Depth 1 adalah Parent langsung, Depth 2 adalah Parent dari Parent, dan seterusnya.
3. Bila Node pada tingkat tersebut ada, block meneruskannya lewat [[^output|The Parent]].
4. Bila tidak ada, misalnya [[^input|Depth]] melebihi jumlah tingkat di atas Node, [[^output|Not Found]] bernilai [[^value/boolean/true]].
5. Bila [[^input|Node]] atau [[^input|Depth]] dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]] dan tidak ada output yang meneruskan aliran.
6. Penelusuran ini dihitung dari Node ke atas. Untuk penelusuran yang dihitung dari Origin ke bawah, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]].

## Contoh Penggunaan

Contoh berikut memakai [[Docs/Tipe Data/Tree]] dengan jalur [[^value/node|Origin]] ➜ [[^value/node|Kategori]] ➜ [[^value/node|Subkategori]] ➜ [[^value/node|Produk]], dan [[^input|Node]] berisi [[^value/node|Produk]].

| Peristiwa | Status | [[^output|The Parent]] | [[^output|Not Found]] |
| - | - | - | - |
| [[^input|Depth]] bernilai [[^value/number|1]] | [[^flowstate|Succeed]] | [[^value/node|Subkategori]] | - |
| [[^input|Depth]] bernilai [[^value/number|2]] | [[^flowstate|Succeed]] | [[^value/node|Kategori]] | - |
| [[^input|Depth]] bernilai [[^value/number|3]] | [[^flowstate|Succeed]] | [[^value/node|Origin]] | - |
| [[^input|Depth]] bernilai [[^value/number|4]] (melebihi jumlah tingkat di atas Node) | [[^flowstate|Succeed]] | - | [[^value/boolean/true]] |
| [[^input|Depth]] kurang dari [[^value/number|1]] | [[^flowstate|Succeed]] | - | [[^value/boolean/true]] |
| [[^input|Node]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - | - |
| [[^input|Depth]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - | - |

## Praktik Terbaik

- **Gunakan Depth 1 untuk Parent langsung.** Nilai Depth yang lebih besar berguna ketika Anda perlu naik beberapa tingkat, misalnya mencari Kategori dari sebuah Produk.
- **Hubungkan block penanganan langsung ke [[^output|Not Found]].** Misalnya [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]] atau block lain yang menangani Node tanpa Parent pada Depth tersebut.
- **Pakai [[^output|The Parent]] untuk menelusuri berantai.** Hubungkan ke [[^input|Node]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]] berikutnya, atau ke [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]] untuk membaca Name dan Order Parent.

## Batasan dan Catatan

- Block hanya menelusuri Parent, tidak menelusuri anak. Untuk anak, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]].
- [[^input|Depth]] dihitung dari Node ke atas, berbeda dengan [[^input|Anc. Level]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]] yang dihitung dari Origin ke bawah.
- [[^output|Not Found]] bukan error. Block berstatus [[^flowstate|Succeed]] dan Flow tetap berjalan pada jalur [[^output|Not Found]].
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]]

<!--
  * [TODO] Konfirmasi kondisi [[^output|Not Found]]: saya menulis bernilai [[^value/boolean/true]] bila Depth melebihi jumlah tingkat di atas Node (termasuk Node Origin yang tidak memiliki Parent) dan bila Depth kurang dari 1, mengikuti aturan Node Get Ancestor.
  * [TODO] Konfirmasi status block saat [[^input|Node]] atau [[^input|Depth]] kosong. Saya menulis [[^flowstate|Fatal Error]] mengikuti block Data Tree lainnya.
  * [TODO] Konfirmasi apakah status block saat [[^output|Not Found]] adalah [[^flowstate|Succeed]] atau [[^flowstate|Error]]. Saya menulis [[^flowstate|Succeed]].
  * [TODO] Konfirmasi perilaku Depth berupa bilangan desimal. Belum ditulis di halaman ini.
  * [TODO] Nama Node pada contoh (Origin, Kategori, Subkategori, Produk) bersifat generik. Sesuaikan dengan gambar bila perlu.
-->

<!--
  * [TODO] Halaman yang ditautkan dan mungkin belum ada: `Docs/Modul Logic/Flow/Flow Block/Error/Error Message`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan anchor `Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output`.
-->
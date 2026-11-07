---
status: draft
title: Node Get Children Block
description: Flow Block Data Tree yang mengambil anak langsung dari sebuah Node berdasarkan Order.
---

# Node Get Children Block

>**note** Node Get Children Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam kategori Data di komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Node Get Children Block adalah Flow Block yang mengambil anak langsung dari sebuah [[Docs/Tipe Data/Node]] berdasarkan Order. Block ini hanya mengambil satu tingkat ke bawah, bukan seluruh keturunan.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/node-get-children-block-flow.png|Node Get Children Block pada Blueprint Flow]]

<!--
  * [TODO] Tambahkan screenshot Node Get Children Block pada Blueprint Flow dengan nama file `node-get-children-block-flow.png` di folder `Docs/Modul Logic/Flow/Flow Block/Data Tree/`. Anotasi yang disarankan: ① input Node dan Child Order di sisi kiri, ② output The Children dan Not Found di sisi kanan.
-->

## Input dan Output

Block ini tidak memiliki Control. Block hanya memiliki input di sisi kiri dan output di sisi kanan.

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Node yang anaknya akan diambil. Pilih Node atau hubungkan dari output block lain. Wajib diisi. |
| [[^input|Child Order]] | [[Docs/Tipe Data/Number]] | Order dari anak yang ingin diambil. Wajib diisi. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|The Children]] | [[Docs/Tipe Data/Node]] | Anak langsung dari Node dengan Order yang diinput. Hanya meneruskan aliran bila ditemukan. |
| [[^output|Not Found]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila tidak ada anak dengan Order yang diinput. Hanya meneruskan aliran bila tidak ditemukan. |

Bila anak ditemukan, hanya [[^output|The Children]] yang meneruskan aliran. Bila tidak ditemukan, hanya [[^output|Not Found]] yang meneruskan aliran. Saat [[^flowstate|Fatal Error]], tidak ada output yang meneruskan aliran. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block menerima [[Docs/Tipe Data/Node]] dari [[^input|Node]] dan [[Docs/Tipe Data/Number]] dari [[^input|Child Order]].
2. Block mencari anak langsung dari Node yang memiliki Order sama dengan [[^input|Child Order]].
3. Bila ditemukan, block meneruskan anak tersebut lewat [[^output|The Children]].
4. Bila tidak ada anak dengan Order tersebut, termasuk bila Node tidak memiliki anak, [[^output|Not Found]] bernilai [[^value/boolean/true]].
5. Bila [[^input|Node]] atau [[^input|Child Order]] dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]] dan tidak ada output yang meneruskan aliran.
6. Untuk mengambil cucu atau keturunan lebih dalam, hubungkan [[^output|The Children]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]] berikutnya.

## Contoh Penggunaan

Contoh berikut memakai [[^input|Node]] berisi [[^value/node|Kategori]] yang memiliki dua anak langsung, yaitu [[^value/node|Subkategori Pertama]] dengan Order [[^value/number|1]] dan [[^value/node|Subkategori Kedua]] dengan Order [[^value/number|2]].

| Peristiwa | Status | [[^output|The Children]] | [[^output|Not Found]] |
| - | - | - | - |
| [[^input|Child Order]] bernilai [[^value/number|1]] | [[^flowstate|Succeed]] | [[^value/node|Subkategori Pertama]] | - |
| [[^input|Child Order]] bernilai [[^value/number|2]] | [[^flowstate|Succeed]] | [[^value/node|Subkategori Kedua]] | - |
| [[^input|Child Order]] bernilai [[^value/number|3]] (tidak ada anak dengan Order tersebut) | [[^flowstate|Succeed]] | - | [[^value/boolean/true]] |
| [[^input|Node]] tidak memiliki anak | [[^flowstate|Succeed]] | - | [[^value/boolean/true]] |
| [[^input|Node]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - | - |
| [[^input|Child Order]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - | - |

## Praktik Terbaik

- **Mulai dari Origin.** Hubungkan [[^output|The Origin]] dari [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]] ke [[^input|Node]] untuk mengambil Node level pertama.
- **Hubungkan block penanganan langsung ke [[^output|Not Found]].** Misalnya [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]] atau [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]] untuk membuat anak dengan Order tersebut bila belum ada.
- **Telusuri berantai untuk level yang lebih dalam.** Hubungkan [[^output|The Children]] ke [[^input|Node]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]] berikutnya.

## Batasan dan Catatan

- Block hanya mengambil anak langsung, bukan keturunan yang lebih dalam.
- Block mengambil satu anak setiap eksekusi, yaitu anak dengan Order yang diinput.
- [[^output|Not Found]] bukan error. Block berstatus [[^flowstate|Succeed]] dan Flow tetap berjalan pada jalur [[^output|Not Found]].
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]]

<!--
  * [TODO] Konfirmasi status block saat [[^input|Node]] atau [[^input|Child Order]] kosong. Saya menulis [[^flowstate|Fatal Error]] mengikuti block Data Tree lainnya.
  * [TODO] Konfirmasi status block saat [[^output|Not Found]]: saya menulis [[^flowstate|Succeed]].
  * [TODO] Konfirmasi perilaku bila beberapa anak memiliki Order yang sama (anak mana yang diambil). Belum ditulis di halaman ini.
  * [TODO] Nama Node pada contoh (Kategori, Subkategori Pertama, Subkategori Kedua) bersifat generik. Sesuaikan dengan gambar bila perlu.
-->

<!--
  * [TODO] Halaman yang ditautkan dan mungkin belum ada: `Docs/Modul Logic/Flow/Flow Block/Error/Error Message`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan anchor `Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output`.
-->
---
status: draft
title: Delete Node Block
description: Flow Block Data Tree yang menghapus sebuah Node, dengan pilihan hapus paksa untuk Node yang sudah digunakan.
---
# Delete Node Block

>**note** Delete Node Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam kategori Data di komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Delete Node Block adalah Flow Block yang menghapus sebuah [[Docs/Tipe Data/Node]] dari [[Docs/Tipe Data/Tree]]. Block ini menghasilkan dua output Boolean, yaitu [[^output|Succeed]] saat berhasil dan [[^output|Error]] saat penghapusan ditolak, sehingga Flow dapat bercabang sesuai hasilnya.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/delete-node-block-flow.png|Delete Node Block pada Blueprint Flow]]
## Input dan Output

Block ini tidak memiliki Control. Block hanya memiliki input di sisi kiri dan output di sisi kanan.

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Node yang akan dihapus. Pilih Node atau hubungkan dari output block lain. Wajib diisi. |
| [[^input|Force]] | [[Docs/Tipe Data/Boolean]] | Isi [[^value/boolean/true]] untuk menghapus Node yang sudah digunakan. Isi [[^value/boolean/false]] untuk menolak penghapusan Node yang sudah digunakan. Wajib diisi. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Succeed]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila Node berhasil dihapus. Hanya meneruskan aliran pada kasus berhasil. |
| [[^output|Error]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila penghapusan ditolak. Hanya meneruskan aliran pada kasus gagal. |

Pada kasus berhasil, hanya [[^output|Succeed]] yang meneruskan aliran. Pada kasus gagal, hanya [[^output|Error]] yang meneruskan aliran. Saat [[^flowstate|Fatal Error]], tidak ada output yang meneruskan aliran. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**danger** Penghapusan tidak dapat dikembalikan
> [[Docs/Tipe Data/Node]] yang sudah dihapus tidak dapat dikembalikan. Periksa kembali [[^input|Node]] sebelum menjalankan Flow.

>**warning** Hapus paksa pada Node yang sudah digunakan
> Bila [[^input|Force]] bernilai [[^value/boolean/true]], Node yang sudah digunakan tetap dihapus. Flow, data lain, atau riwayat yang merujuk Node tersebut dapat terputus.

>**warning** Tree dengan Merger Mode atau External Read Only
> Flow dapat mengubah atau menghapus [[Docs/Tipe Data/Node]] pada [[Docs/Tipe Data/Tree]] yang memakai [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] atau [[Docs/Modul Data/Tree/Konfigurasi External Read Only|External Read Only]], termasuk Node hasil *clone*. Pastikan perubahan tersebut memang Anda inginkan sebelum menjalankan Flow.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Perubahan [[Docs/Tipe Data/Node]] yang dilakukan block ini tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]] maupun Flow Block Event lainnya.

## Cara Kerja

1. Block menerima [[Docs/Tipe Data/Node]] dari [[^input|Node]] dan nilai [[Docs/Tipe Data/Boolean]] dari [[^input|Force]].
2. Block memeriksa apakah Node sudah digunakan, yaitu sedang dipakai pada Flow atau data lain, atau riwayat activity mencatat pemakaiannya.
3. Bila Node belum digunakan, Node dihapus dan [[^output|Succeed]] bernilai [[^value/boolean/true]].
4. Bila Node sudah digunakan dan [[^input|Force]] bernilai [[^value/boolean/false]], penghapusan ditolak. Block berstatus [[^flowstate|Error]], pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]], dan [[^output|Error]] bernilai [[^value/boolean/true]].
5. Bila Node sudah digunakan dan [[^input|Force]] bernilai [[^value/boolean/true]], Node tetap dihapus dan [[^output|Succeed]] bernilai [[^value/boolean/true]].
6. Bila [[^input|Node]] atau [[^input|Force]] dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]] dan tidak ada output yang meneruskan aliran.

## Contoh Penggunaan

Tabel berikut menunjukkan hasil block pada setiap kombinasi kondisi.

| Peristiwa | Status | [[^output|Succeed]] | [[^output|Error]] |
| - | - | - | - |
| Node belum digunakan, [[^input|Force]] bernilai [[^value/boolean/false]] | [[^flowstate|Succeed]] | [[^value/boolean/true]] | - |
| Node belum digunakan, [[^input|Force]] bernilai [[^value/boolean/true]] | [[^flowstate|Succeed]] | [[^value/boolean/true]] | - |
| Node sudah digunakan, [[^input|Force]] bernilai [[^value/boolean/false]] | [[^flowstate|Error]] | - | [[^value/boolean/true]] |
| Node sudah digunakan, [[^input|Force]] bernilai [[^value/boolean/true]] | [[^flowstate|Succeed]] | [[^value/boolean/true]] | - |
| [[^input|Node]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - | - |
| [[^input|Force]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - | - |

## Praktik Terbaik

- **Mulai dengan [[^input|Force]] bernilai [[^value/boolean/false]].** Gunakan hapus paksa hanya setelah Anda memastikan Node yang sudah digunakan memang boleh dihapus.
- **Isi [[^input|Force]] pada setiap eksekusi.** Berbeda dengan sebagian block Data lain, [[^input|Force]] yang kosong tidak dianggap [[^value/boolean/false]] dan menghasilkan [[^flowstate|Fatal Error]].
- **Hubungkan block penanganan langsung ke [[^output|Error]].** Misalnya [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]] agar kegagalan penghapusan tercatat dengan jelas. [[^output|Succeed]] dan [[^output|Error]] tidak meneruskan aliran bersamaan, sehingga tiap kasus dapat memiliki jalurnya sendiri.

## Batasan dan Catatan

- Bila [[^input|Node]] atau [[^input|Force]] kosong, block berstatus [[^flowstate|Fatal Error]] dan seluruh output tidak ada.
- Penolakan penghapusan karena Node sudah digunakan berstatus [[^flowstate|Error]], bukan [[^flowstate|Fatal Error]].
- Block menghapus satu [[Docs/Tipe Data/Node]] setiap eksekusi.
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]]

<!--
  * [TODO] Konfirmasi perilaku Node anak saat Node induk dihapus lewat Flow (ikut terhapus, naik ke Parent, atau penghapusan ditolak). Belum ditulis di halaman ini.
  * [TODO] Konfirmasi apakah Node Origin dapat dihapus dan hasilnya (Error atau Fatal Error). Belum ditulis di halaman ini.
  * [TODO] Konfirmasi definisi Node yang "sudah digunakan" (saya mengikuti definisi Variable Data: dipakai pada Flow atau data lain, atau tercatat di riwayat activity).
  * [TODO] Konfirmasi penyebab lain penghapusan ditolak selain Node sudah digunakan.
-->

<!--
  * [TODO] Halaman yang ditautkan dan mungkin belum ada: `Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event`, `Docs/Modul Logic/Flow/Flow Block/Error/Error Message`, `Docs/Modul Data/Tree/Konfigurasi External Read Only` (usulan), `Docs/Modul Data/Tree/Konfigurasi Merger Mode`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan anchor `Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output`.
-->
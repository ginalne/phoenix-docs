---
status: draft
title: Node Block
description: Flow Block Data Tree yang mengambil atribut dari sebuah Node, yaitu Order, Name, dan Tree.
---

# Node Block

>**note** Node Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam kategori Data di komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Node Block adalah Flow Block yang mengambil atribut dari sebuah [[Docs/Tipe Data/Node]]. Gunakan block ini ketika alur Flow Anda membutuhkan Order, Name, atau Tree dari Node tertentu. Block ini hanya membaca dan tidak mengubah Node. Untuk mengubah Node, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]].

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/node-block-flow.png|Node Block pada Blueprint Flow]]

<!--
  * [TODO] Tambahkan screenshot Node Block pada Blueprint Flow dengan nama file `node-block-flow.png` di folder `Docs/Modul Logic/Flow/Flow Block/Data Tree/`. Anotasi yang disarankan: ① input Node di sisi kiri, ② output Pass, Order, Name, dan Tree di sisi kanan.
-->

## Input dan Output

Block ini tidak memiliki Control. Block hanya memiliki input di sisi kiri dan output di sisi kanan.

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Node yang atributnya akan diambil. Pilih Node atau hubungkan dari output block lain. Jika dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Pass]] | [[Docs/Tipe Data/Node]] | Meneruskan Node yang diinput agar dapat dipakai block berikutnya. |
| [[^output|Order]] | [[Docs/Tipe Data/Number]] | Order dari Node. |
| [[^output|Name]] | [[Docs/Tipe Data/String]] | Name dari Node. |
| [[^output|Tree]] | [[Docs/Tipe Data/Tree]] | Tree tempat Node berada. |

Saat berhasil, output meneruskan aliran ke block yang terhubung. Saat [[^flowstate|Fatal Error]], tidak ada output yang meneruskan aliran. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block menerima [[Docs/Tipe Data/Node]] dari [[^input|Node]].
2. Block membaca Order, Name, dan Tree dari Node tersebut.
3. Block mengirim ketiganya ke [[^output|Order]], [[^output|Name]], dan [[^output|Tree]], serta meneruskan Node yang sama lewat [[^output|Pass]].
4. Jika [[^input|Node]] dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]], pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]], dan tidak ada output yang meneruskan aliran.

## Contoh Penggunaan

Tabel berikut menunjukkan hasil block pada setiap kondisi input.

| Peristiwa | Status | [[^output|Pass]] | [[^output|Order]] | [[^output|Name]] | [[^output|Tree]] |
| - | - | - | - | - | - |
| [[^input|Node]] terisi | [[^flowstate|Succeed]] | Node yang diinput | Order Node | Name Node | Tree tempat Node berada |
| [[^input|Node]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - | - | - | - |

## Praktik Terbaik

- **Ambil nilai saat ini sebelum mengubah Node.** Hubungkan [[^output|Order]] dan [[^output|Name]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]] agar atribut yang tidak ingin diubah tetap memakai nilai saat ini.
- **Teruskan [[^output|Tree]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree|Tree Block]]** untuk mengambil Name atau Merger Mode dari Tree tempat Node berada.
- **Gunakan block penelusuran untuk relasi.** Block ini tidak mengambil Parent dan Children. Gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]] atau [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]].

## Batasan dan Catatan

- Block hanya membaca atribut [[Docs/Tipe Data/Node]] dan tidak mengubahnya.
- Block tidak mengambil Parent dan Children dari Node.
- Saat [[^input|Node]] kosong, block berstatus [[^flowstate|Fatal Error]] dan seluruh output tidak ada.
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Data/Tree/Node/Pengenalan|Tree Node]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]]

<!--
  * [TODO] Konfirmasi label output yang tampil di aplikasi (Pass, Order, Name, Tree) dan urutannya.
  * [TODO] Konfirmasi status block saat [[^input|Node]] kosong. Saya menulis [[^flowstate|Fatal Error]] mengikuti Enum Block dan Node Setter.
-->

<!--
  * [TODO] Halaman yang ditautkan dan mungkin belum ada: `Docs/Modul Data/Tree/Node/Pengenalan`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan anchor `Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output`.
-->
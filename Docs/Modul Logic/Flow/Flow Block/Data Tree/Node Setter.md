---
status: draft
title: Node Setter Block
description: Flow Block Data Tree yang mengubah Name dan Order dari sebuah Node.
---

# Node Setter Block

>**note** Node Setter Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam kategori Data di komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Node Setter Block adalah Flow Block yang mengubah Name dan Order dari sebuah [[Docs/Tipe Data/Node]]. Setelah perubahan tersimpan, block meneruskan Node tersebut lewat [[^output|Pass]].

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/node-setter-block-flow.png|Node Setter Block pada Blueprint Flow]]

<!--
  * [TODO] Tambahkan screenshot Node Setter Block pada Blueprint Flow dengan nama file `node-setter-block-flow.png` di folder `Docs/Modul Logic/Flow/Flow Block/Data Tree/`. Anotasi yang disarankan: ① input Node, Order, dan Name di sisi kiri, ② output Pass di sisi kanan.
-->

## Input dan Output

Block ini tidak memiliki Control. Block hanya memiliki input di sisi kiri dan output di sisi kanan.

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Node yang akan diubah. Pilih Node atau hubungkan dari output block lain. Wajib diisi. |
| [[^input|Order]] | [[Docs/Tipe Data/Number]] | Nilai Order baru untuk Node. Wajib diisi. |
| [[^input|Name]] | [[Docs/Tipe Data/String]] | Name baru untuk Node. Wajib diisi. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Pass]] | [[Docs/Tipe Data/Node]] | Node yang diinput, setelah Name dan Order diperbarui. Meneruskan aliran hanya bila berhasil. |

Saat berhasil, [[^output|Pass]] meneruskan aliran. Bila salah satu input kosong, block berstatus [[^flowstate|Fatal Error]] dan [[^output|Pass]] tidak meneruskan aliran. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**warning** Tree dengan Merger Mode atau External Read Only
> Flow dapat mengubah atau menghapus [[Docs/Tipe Data/Node]] pada [[Docs/Tipe Data/Tree]] yang memakai [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] atau [[Docs/Modul Data/Tree/Konfigurasi External Read Only|External Read Only]], termasuk Node hasil *clone*. Pastikan perubahan tersebut memang Anda inginkan sebelum menjalankan Flow.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Perubahan [[Docs/Tipe Data/Node]] yang dilakukan block ini tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]] maupun Flow Block Event lainnya.

## Cara Kerja

1. Block menerima [[Docs/Tipe Data/Node]] dari [[^input|Node]], serta nilai baru dari [[^input|Order]] dan [[^input|Name]].
2. Block mengubah Order dan Name Node menjadi nilai yang diinput dalam satu eksekusi.
3. Block meneruskan Node yang sudah diperbarui lewat [[^output|Pass]].
4. Jika salah satu input wajib dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]], pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]], dan tidak ada output yang meneruskan aliran.
5. Karena ketiga input wajib terisi, isi atribut yang tidak ingin diubah dengan nilainya saat ini, misalnya dari [[^output|Order]] dan [[^output|Name]] milik [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]].

## Contoh Penggunaan

Tabel berikut menunjukkan hasil block pada setiap kondisi input.

| Peristiwa | Status | [[^output|Pass]] |
| - | - | - |
| [[^input|Node]], [[^input|Order]], dan [[^input|Name]] terisi | [[^flowstate|Succeed]] | Node yang diinput, sudah diperbarui |
| [[^input|Node]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - |
| [[^input|Order]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - |
| [[^input|Name]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - |

## Praktik Terbaik

- **Gunakan nilai saat ini untuk atribut yang tidak berubah.** Ambil dari [[^output|Order]] dan [[^output|Name]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]] lalu hubungkan ke input yang sesuai.
- **Gunakan [[^output|Pass]] untuk melanjutkan alur.** Hubungkan ke block berikutnya, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]] untuk memindahkan Node yang baru diubah.
- **Periksa Tree sebelum mengubah.** Pastikan [[Docs/Tipe Data/Node]] bukan bagian dari [[Docs/Tipe Data/Tree]] yang dilindungi [[Docs/Modul Data/Tree/Konfigurasi External Read Only|External Read Only]] atau memakai [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] bila Anda tidak ingin Node tersebut ikut berubah.

## Batasan dan Catatan

- Block mengubah Name dan Order sekaligus. Block tidak dapat mengubah satu atribut saja.
- Block tidak memindahkan Node ke Parent lain. Untuk memindahkan Node, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]].
- Setiap eksekusi mengubah satu [[Docs/Tipe Data/Node]].
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]]

<!--
  * [TODO] Konfirmasi apakah ada pemeriksaan konflik (misalnya Name atau Order yang sama dengan Node saudara). Saya tidak menulis output konflik karena belum dijelaskan.
  * [TODO] Konfirmasi dampak perubahan Order terhadap Node saudara (apakah Order Node lain ikut bergeser). Belum ditulis di halaman ini.
  * [TODO] Konfirmasi aturan [[^input|Name]] Node (sama seperti Name Variable Data: membedakan huruf besar dan kecil, menerima simbol, di-trim saat disimpan).
-->

<!--
  * [TODO] Halaman yang ditautkan dan mungkin belum ada: `Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event`, `Docs/Modul Data/Tree/Konfigurasi External Read Only` (usulan), `Docs/Modul Data/Tree/Konfigurasi Merger Mode`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan anchor `Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output`.
-->
---
status: draft
title: Add Node Block
description: Flow Block Data Tree yang menambahkan Node baru sebagai anak dari sebuah Node.
---

# Add Node Block

>**note** Add Node Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam kategori Data di komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Add Node Block adalah Flow Block yang menambahkan [[Docs/Tipe Data/Node]] baru ke sebuah [[Docs/Tipe Data/Tree]]. Node baru ditempatkan sebagai anak dari Parent yang Anda pilih, sehingga Anda dapat membangun struktur Tree langsung dari Flow.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/add-node-block-flow.png|Add Node Block pada Blueprint Flow]]

<!--
  * [TODO] Tambahkan screenshot Add Node Block pada Blueprint Flow dengan nama file `add-node-block-flow.png` di folder `Docs/Modul Logic/Flow/Flow Block/Data Tree/`. Anotasi yang disarankan: ① input Parent, Order, dan Name di sisi kiri, ② output New Node di sisi kanan.
-->

## Input dan Output

Block ini tidak memiliki Control. Block hanya memiliki input di sisi kiri dan output di sisi kanan.

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Parent]] | [[Docs/Tipe Data/Node]] | Node yang menjadi Parent dari Node baru. Pilihan menampilkan seluruh Node dari semua Tree. Wajib diisi. |
| [[^input|Order]] | [[Docs/Tipe Data/Number]] | Order untuk Node baru. Wajib diisi. |
| [[^input|Name]] | [[Docs/Tipe Data/String]] | Name untuk Node baru. Wajib diisi. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|New Node]] | [[Docs/Tipe Data/Node]] | Node baru yang berhasil ditambahkan. Meneruskan aliran hanya bila berhasil. |

Saat berhasil, [[^output|New Node]] meneruskan aliran. Bila salah satu input kosong, block berstatus [[^flowstate|Fatal Error]] dan [[^output|New Node]] tidak meneruskan aliran. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**warning** Tree dengan Merger Mode atau External Read Only
> Flow dapat mengubah atau menghapus [[Docs/Tipe Data/Node]] pada [[Docs/Tipe Data/Tree]] yang memakai [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] atau [[Docs/Modul Data/Tree/Konfigurasi External Read Only|External Read Only]], termasuk Node hasil *clone*. Pastikan perubahan tersebut memang Anda inginkan sebelum menjalankan Flow.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Perubahan [[Docs/Tipe Data/Node]] yang dilakukan block ini tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]] maupun Flow Block Event lainnya.

## Cara Kerja

1. Block menerima [[Docs/Tipe Data/Node]] dari [[^input|Parent]], serta [[^input|Order]] dan [[^input|Name]] untuk Node baru.
2. Block membuat Node baru sebagai anak dari [[^input|Parent]]. Node baru berada di [[Docs/Tipe Data/Tree]] yang sama dengan Parent.
3. Block meneruskan Node baru lewat [[^output|New Node]].
4. Jika salah satu input wajib dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]], pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]], dan tidak ada output yang meneruskan aliran.
5. Untuk menambahkan Node pada level pertama Tree, hubungkan [[^output|The Origin]] dari [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]] ke [[^input|Parent]].

## Contoh Penggunaan

Tabel berikut menunjukkan hasil block pada setiap kondisi input.

| Peristiwa | Status | [[^output|New Node]] |
| - | - | - |
| [[^input|Parent]], [[^input|Order]], dan [[^input|Name]] terisi | [[^flowstate|Succeed]] | Node baru |
| [[^input|Parent]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - |
| [[^input|Order]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - |
| [[^input|Name]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - |

## Praktik Terbaik

- **Tentukan Parent dari alur, bukan dari pilihan manual.** Hubungkan [[^output|The Origin]] dari [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]] atau [[^output|The Children]] dari [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]] agar Flow tetap bekerja walau Tree berubah.
- **Pilih [[^input|Order]] yang konsisten.** Tentukan aturan Order untuk Node saudara agar urutan Node mudah dibaca dan ditelusuri dengan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]].
- **Gunakan [[^output|New Node]] untuk langkah lanjutan.** Hubungkan ke [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]] atau block lain yang bekerja pada Node baru tersebut.

## Batasan dan Catatan

- Block hanya menambahkan Node baru. Untuk menempatkan Node yang sudah ada ke Parent lain, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]].
- Pilihan [[^input|Parent]] menampilkan Node dari semua Tree, sehingga [[Docs/Tipe Data/Tree]] tujuan ditentukan oleh Parent yang dipilih.
- Bila [[^input|Parent]], [[^input|Order]], atau [[^input|Name]] kosong, block berstatus [[^flowstate|Fatal Error]] dan seluruh output tidak ada.
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Delete Node|Delete Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]]

<!--
  * [TODO] Konfirmasi output [[^output|New Node]]. Halaman ini belum mendapat daftar output dari penulis, saya mengikuti pola Add Variable (New Variable) dan Add EnumData (New EnumData).
  * [TODO] Konfirmasi apakah ada pemeriksaan konflik (Name atau Order yang sama dengan Node saudara) dan outputnya. Belum ditulis di halaman ini.
  * [TODO] Konfirmasi bahwa Node baru berada di Tree yang sama dengan [[^input|Parent]] (disimpulkan dari pilihan Parent yang menampilkan Node semua Tree).
-->

<!--
  * [TODO] Halaman yang ditautkan dan mungkin belum ada: `Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event`, `Docs/Modul Data/Tree/Konfigurasi External Read Only` (usulan), `Docs/Modul Data/Tree/Konfigurasi Merger Mode`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Delete Node`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan anchor `Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output`.
-->
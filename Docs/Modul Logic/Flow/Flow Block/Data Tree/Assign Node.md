---
    status: draft
    title: Assign Node Block
    description: Flow Block Data Tree yang menempatkan sebuah Node sebagai anak dari Node lain dengan Order tertentu.
---
# Assign Node Block

>**note** Assign Node Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam kategori Data di komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Assign Node Block adalah Flow Block yang menempatkan [[Docs/Tipe Data/Node]] yang sudah ada sebagai anak dari Node lain. Gunakan block ini ketika struktur [[Docs/Tipe Data/Tree]] perlu disusun ulang tanpa membuat Node baru.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/assign-node-block-flow.png|Assign Node Block pada Blueprint Flow]]
## Input dan Output

Block ini tidak memiliki Control. Block hanya memiliki input di sisi kiri dan output di sisi kanan.

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Parent]] | [[Docs/Tipe Data/Node]] | Node yang akan menjadi Parent. Pilih Node atau hubungkan dari output block lain. Wajib diisi. |
| [[^input|Order]] | [[Docs/Tipe Data/Number]] | Nilai yang akan menjadi Order dari Node children. Wajib diisi. |
| [[^input|Node children]] | [[Docs/Tipe Data/Node]] | Node yang akan ditempatkan di bawah Parent. Wajib diisi. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Pass children]] | [[Docs/Tipe Data/Node]] | Node children yang diinput. Meneruskan aliran hanya bila berhasil. |

Saat berhasil, [[^output|Pass children]] meneruskan aliran. Saat [[^flowstate|Error]] atau [[^flowstate|Fatal Error]], [[^output|Pass children]] tidak meneruskan aliran. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**warning** Tree dengan Merger Mode atau External Read Only
> Flow dapat mengubah atau menghapus [[Docs/Tipe Data/Node]] pada [[Docs/Tipe Data/Tree]] yang memakai [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] atau [[Docs/Modul Data/Tree/Konfigurasi External Read Only|External Read Only]], termasuk Node hasil *clone*. Pastikan perubahan tersebut memang Anda inginkan sebelum menjalankan Flow.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Perubahan [[Docs/Tipe Data/Node]] yang dilakukan block ini tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]] maupun Flow Block Event lainnya.

## Cara Kerja

1. Block menerima [[Docs/Tipe Data/Node]] dari [[^input|Parent]], nilai [[^input|Order]], dan Node dari [[^input|Node children]].
2. Block memeriksa bahwa Parent dan Node children berada di [[Docs/Tipe Data/Tree]] yang sama.
3. Bila sama, Node children ditempatkan di bawah Parent dengan Order sesuai [[^input|Order]], lalu diteruskan lewat [[^output|Pass children]].
4. Bila berbeda Tree, block berstatus [[^flowstate|Error]], pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]], dan [[^output|Pass children]] tidak meneruskan aliran.
5. Bila [[^input|Parent]], [[^input|Order]], atau [[^input|Node children]] kosong, block berstatus [[^flowstate|Fatal Error]] dan tidak ada output yang meneruskan aliran.

## Contoh Penggunaan

Tabel berikut menunjukkan hasil block pada setiap kondisi input.

| Peristiwa | Status | [[^output|Pass children]] |
| - | - | - |
| [[^input|Parent]] dan [[^input|Node children]] berada di Tree yang sama | [[^flowstate|Succeed]] | Node children |
| [[^input|Parent]] dan [[^input|Node children]] berada di Tree yang berbeda | [[^flowstate|Error]] | - |
| [[^input|Parent]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - |
| [[^input|Order]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - |
| [[^input|Node children]] dibiarkan kosong | [[^flowstate|Fatal Error]] | - |

## Praktik Terbaik

- **Pastikan Parent dan Node children satu Tree.** Ambil keduanya dari Tree yang sama, misalnya dengan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]] atau [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]], agar block tidak berstatus [[^flowstate|Error]].
- **Tangani [[^flowstate|Error]] lewat Flow Activity.** Pantau [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]] untuk mengetahui Assign Node yang gagal karena beda Tree.
- **Gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]] untuk Node baru.** Assign Node hanya menempatkan Node yang sudah ada.

## Batasan dan Catatan

- Block hanya bekerja bila Parent dan Node children berada di [[Docs/Tipe Data/Tree]] yang sama.
- Bila [[^input|Parent]], [[^input|Order]], atau [[^input|Node children]] kosong, block berstatus [[^flowstate|Fatal Error]] dan seluruh output tidak ada.
- Block tidak membuat Node baru dan tidak mengubah Name. Untuk mengubah Name dan Order tanpa memindahkan Node, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]].
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Delete Node|Delete Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]]

<!--
  * [TODO] Konfirmasi apakah ada output Error pada block ini. Saya hanya menulis output Pass children sesuai penjelasan penulis, dan Error ditulis sebagai status yang tampil di Flow Activity.
  * [TODO] Konfirmasi perilaku penempatan: apakah Node children berpindah dari Parent lama (Node hanya memiliki satu Parent), dan bagaimana bila Parent adalah keturunan Node children atau bila Node children adalah Origin. Belum ditulis di halaman ini.
  * [TODO] Konfirmasi dampak Order terhadap Node saudara yang sudah memiliki Order yang sama.
  * [TODO] Konfirmasi label persis input dan output: `Node children` dan `Pass children` (huruf kecil pada kata kedua mengikuti tulisan penulis).
-->

<!--
  * [TODO] Halaman yang ditautkan dan mungkin belum ada: `Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event`, `Docs/Modul Data/Tree/Konfigurasi External Read Only` (usulan), `Docs/Modul Data/Tree/Konfigurasi Merger Mode`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Delete Node`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin`, `Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan anchor `Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output`.
-->
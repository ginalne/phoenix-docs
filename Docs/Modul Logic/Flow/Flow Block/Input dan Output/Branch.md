---
    status: draft
    title: Branch Block
    description: Flow Block untuk meneruskan satu data Input ke beberapa Output sekaligus pada komponen Flow.
    pageDecoration:
      tree:
        priority: 2
---

# Branch Block

>**note** Branch Block merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Pengenalan|Flow Block Input dan Output]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Branch Block adalah Flow Block yang meneruskan satu data [[^input|Input]] ke beberapa [[^output|Output]] sekaligus. Setiap Output membawa data yang sama dengan Input, sehingga satu data dapat dipakai oleh banyak block tanpa perlu diisi berulang.

Satu Output hanya dapat terhubung ke satu Input block lain ([[Docs/Modul Logic/Flow/Flow Block/Aturan Koneksi|Aturan Koneksi]]). Branch Block mengatasi batasan ini dengan menyediakan beberapa Output dari satu data. Branch Block bukan block bersyarat: tidak ada kondisi yang diperiksa, dan setiap Output yang terhubung menerima data yang sama.

Branch Block tersedia dalam empat varian, yaitu Branch 2 sampai Branch 5. Angka pada nama menunjukkan jumlah Output. Fungsi dan aturan seluruh varian sama, sehingga semuanya dijelaskan pada halaman ini.

![[Docs/Modul Logic/Flow/Flow Block/Input dan Output/branch-block-flow.png|Branch Block varian Branch 2 sampai Branch 5]]

<!--
  * [DONE] Penempatan gambar: potong screenshot menjadi satu gambar `branch-block-flow.png` yang memuat empat varian (Branch 2 sampai Branch 5), simpan di folder `Docs/Modul Logic/Flow/Flow Block/Input dan Output/`.
  * [TODO] Judul block pada screenshot tertulis "Data Branch 2" dan seterusnya, sedangkan halaman memakai "Branch Block" sesuai alias tautan pada halaman kategori. Mohon konfirmasi istilah yang dipakai.
    Jawaban: Karena Branch Block memiliki variasi hanya untuk meluaskan jumlah output, maka diharapkan halaman ini bisa digunakan untuk menjelaskan variasi tersebut karena secara fungsi sama.
  * [TODO] Tautan asumsi: `Docs/Tipe Data/Pengenalan` (daftar seluruh Tipe Data, dipakai pada langkah Change Type).
    Jawaban: Iya benar.
-->

## Input dan Output

Branch Block memiliki satu input di sisi kiri, dua sampai lima output di sisi kanan sesuai varian dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Input]] | [[^field|N/A Type]] | Data yang diteruskan ke seluruh Output. Dapat berupa tipe data apa pun dan harus ditentukan lebih dulu lewat [[#Menentukan Tipe Data Input]]. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Output 1]] | Sama dengan tipe data [[^input|Input]] | Meneruskan data [[^input|Input]] bila Output ini terhubung ke block lain. Tersedia pada semua varian. |
| [[^output|Output 2]] | Sama dengan tipe data [[^input|Input]] | Meneruskan data [[^input|Input]] bila Output ini terhubung ke block lain. Tersedia pada semua varian. |
| [[^output|Output 3]] | Sama dengan tipe data [[^input|Input]] | Meneruskan data [[^input|Input]] bila Output ini terhubung ke block lain. Tersedia mulai Branch 3. |
| [[^output|Output 4]] | Sama dengan tipe data [[^input|Input]] | Meneruskan data [[^input|Input]] bila Output ini terhubung ke block lain. Tersedia mulai Branch 4. |
| [[^output|Output 5]] | Sama dengan tipe data [[^input|Input]] | Meneruskan data [[^input|Input]] bila Output ini terhubung ke block lain. Tersedia pada Branch 5. |

Output yang tidak memiliki koneksi tidak mengeluarkan data, termasuk bila Output tersebut berada di tengah. Output lain yang terhubung tetap mengeluarkan data. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

<!--
  * [TODO] Teks penulis menyebut "urutan aliran mulai dari Output 2, Output 3 dan seterusnya". Diasumsikan maksudnya penomoran Output (dimulai dari Output 1 sesuai screenshot), bukan urutan eksekusi, karena urutan eksekusi cabang tidak dapat diprediksi. Mohon konfirmasi.
    Jawaban: Terkait dengan block ini, urutan eksekusi adalah sesuai penomoran. Maksud dari urutan eksekusi yang tidak diprediksi adalah ketika banyak koneksi antar blok yang dimana pengguna akan kesulitan menghubungkan block terakhir (semisal ada 5) tersebut mana yang akan terlebih dahulu di eksekusi, seperti ketika ingin menyusun array dengan menghubungkan banyak output ke satu input, urutannya menjadi sulit terprediksi.
-->

### Menentukan Tipe Data Input

Teks merah [[^field|N/A Type]] pada [[^input|Input]] berarti tipe data belum ditentukan. Tentukan tipe data dengan langkah berikut:

1. Klik kanan pada [[^input|Input]].
2. Pilih [[^field|Change Type]].
3. Pilih [[Docs/Tipe Data/Pengenalan|tipe data]] yang sesuai dengan data yang akan dialirkan.

## Cara Kerja

1. Isi [[^input|Input]] langsung pada block atau hubungkan dari output block lain. [[^input|Input]] yang diisi langsung pada block mendefinisikan data yang dapat dipakai oleh banyak block sekaligus.
2. Setelah Branch Block memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat eksekusi]], data [[^input|Input]] diteruskan ke setiap Output yang memiliki koneksi.
3. Output yang tidak memiliki koneksi tidak mengeluarkan data, sedangkan Output lain tetap berjalan seperti biasa.

## Contoh Penggunaan

Contoh berikut memakai Branch 3 dengan [[^input|Input]] bertipe [[Docs/Tipe Data/String]] berisi [[^value/string|PSN-001]] (nomor pesanan).

| Kondisi | Output 1 | Output 2 | Output 3 | Status |
| - | - | - | - | - |
| Ketiga Output terhubung | [[^value/string|PSN-001]] | [[^value/string|PSN-001]] | [[^value/string|PSN-001]] | [[^flowstate|Succeed]] |
| Output 2 tidak terhubung (berada di tengah) | [[^value/string|PSN-001]] | - | [[^value/string|PSN-001]] | [[^flowstate|Succeed]] |
| Hanya Output 1 yang terhubung | [[^value/string|PSN-001]] | - | - | [[^flowstate|Succeed]] |
| [[^input|Input]] dibiarkan [[^field|N/A Type]] | - | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

<!--
  * [TODO] Diasumsikan Fatal Error pada [[^input|Input]] yang dibiarkan [[^field|N/A Type]] berlaku selalu (berbeda dengan Passer Block yang bergantung pada koneksi Output). Mohon konfirmasi apakah Fatal Error tetap terjadi bila tidak ada Output yang terhubung.
    Jawaban: Ya sudah betul.
-->

## Praktik Terbaik

- **Pilih varian sesuai jumlah tujuan.** Gunakan Branch Block dengan jumlah [[^output|Output]] yang sama dengan jumlah block tujuan agar tidak ada Output yang tidak terpakai.
- **Tentukan tipe data [[^input|Input]] sebelum menghubungkan Output.** [[^field|N/A Type]] pada [[^input|Input]] menghasilkan [[^flowstate|Fatal Error]].
- **Isi [[^input|Input]] langsung** bila data yang sama dipakai oleh banyak block, sehingga data tidak perlu diisi berulang pada setiap block.
- **Jangan mengandalkan urutan Output.** Urutan eksekusi aliran yang bercabang tidak dapat diprediksi. Bila sebuah block harus menunggu beberapa aliran selesai, gunakan [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Passer|Passer Block]].

## Batasan dan Catatan

- Branch Block tidak memeriksa kondisi dan tidak mengubah data. Setiap [[^output|Output]] yang terhubung membawa data [[^input|Input]] yang sama.
- [[^output|Output]] yang tidak memiliki koneksi tidak mengeluarkan data, termasuk bila berada di tengah. [[^output|Output]] lain tidak terpengaruh.
- Branch Block tidak berstatus [[^flowstate|Error]]. Block hanya dapat berstatus [[^flowstate|Fatal Error]] bila [[^input|Input]] dibiarkan [[^field|N/A Type]].
- Urutan eksekusi aliran yang bercabang dari beberapa [[^output|Output]] tidak dapat diprediksi.
- Branch Block tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat Flow Block diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Pengenalan|Flow Block Input dan Output]]
- [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Passer|Passer Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Aturan Koneksi]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]]
- [[Docs/Modul Logic/Flow/Flow Activity]]
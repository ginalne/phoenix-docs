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

### Menentukan Tipe Data Input

Teks merah [[^field|N/A Type]] pada [[^input|Input]] berarti tipe data belum ditentukan. Tentukan tipe data dengan langkah berikut:

1. Klik kanan pada [[^input|Input]].
2. Pilih [[^field|Change Type]].
3. Pilih [[Docs/Tipe Data/Pengenalan|tipe data]] yang sesuai dengan data yang akan dialirkan.

## Cara Kerja

1. Isi [[^input|Input]] langsung pada block atau hubungkan dari output block lain. [[^input|Input]] yang diisi langsung pada block mendefinisikan data yang dapat dipakai oleh banyak block sekaligus.
2. Setelah Branch Block memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat eksekusi]], data [[^input|Input]] diteruskan ke setiap Output yang memiliki koneksi. Aliran dari Output tersebut dieksekusi berurutan sesuai penomoran Output.
3. Output yang tidak memiliki koneksi tidak mengeluarkan data, sedangkan Output lain tetap berjalan seperti biasa.

## Contoh Penggunaan

Contoh berikut memakai Branch 3 dengan [[^input|Input]] bertipe [[Docs/Tipe Data/String]] berisi [[^value/string|PSN-001]] (nomor pesanan).

| Kondisi | Output 1 | Output 2 | Output 3 | Status |
| - | - | - | - | - |
| Ketiga Output terhubung | [[^value/string|PSN-001]] | [[^value/string|PSN-001]] | [[^value/string|PSN-001]] | [[^flowstate/Succeed]] |
| Output 2 tidak terhubung (berada di tengah) | [[^value/string|PSN-001]] | - | [[^value/string|PSN-001]] | [[^flowstate/Succeed]] |
| Hanya Output 1 yang terhubung | [[^value/string|PSN-001]] | - | - | [[^flowstate/Succeed]] |
| [[^input|Input]] dibiarkan [[^field|N/A Type]] | - | - | - | [[^flowstate/Fatal Error]] |

Status [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Pilih varian sesuai jumlah tujuan.** Gunakan Branch Block dengan jumlah [[^output|Output]] yang sama dengan jumlah block tujuan agar tidak ada Output yang tidak terpakai.
- **Tentukan tipe data [[^input|Input]] sebelum menghubungkan Output.** [[^field|N/A Type]] pada [[^input|Input]] menghasilkan [[^flowstate/Fatal Error]].
- **Isi [[^input|Input]] langsung** bila data yang sama dipakai oleh banyak block, sehingga data tidak perlu diisi berulang pada setiap block.
- **Atur urutan lewat penomoran Output.** Aliran dieksekusi sesuai penomoran, sehingga hubungkan block yang harus berjalan lebih dulu ke [[^output|Output]] bernomor lebih kecil.

## Batasan dan Catatan

- Branch Block tidak memeriksa kondisi dan tidak mengubah data. Setiap [[^output|Output]] yang terhubung membawa data [[^input|Input]] yang sama.
- [[^output|Output]] yang tidak memiliki koneksi tidak mengeluarkan data, termasuk bila berada di tengah. [[^output|Output]] lain tidak terpengaruh.
- Branch Block tidak berstatus [[^flowstate/Error]]. Block hanya dapat berstatus [[^flowstate/Fatal Error]] bila [[^input|Input]] dibiarkan [[^field|N/A Type]].
- Aliran dari [[^output|Output]] dieksekusi sesuai penomoran Output.
- Urutan eksekusi sulit diprediksi bila banyak koneksi dari beberapa block bertemu pada satu input, misalnya saat menyusun [[Docs/Tipe Data/Array]] dari banyak output.
- Branch Block tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat Flow Block diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Pengenalan|Flow Block Input dan Output]]
- [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Passer|Passer Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Aturan Koneksi]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]]
- [[Docs/Modul Logic/Flow/Flow Activity]]
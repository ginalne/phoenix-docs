---
    status: draft
    title: Passer Block
    description: Flow Block untuk meneruskan beberapa data Input ke Output yang bersesuaian tanpa mengubahnya pada komponen Flow.
    pageDecoration:
      tree:
        priority: 1
---

# Passer Block

>**note** Passer Block merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Pengenalan|Flow Block Input dan Output]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Passer Block adalah Flow Block yang meneruskan data dari setiap [[^input|Data]] ke [[^output|Pass]] dengan nomor yang sama tanpa mengubahnya. Data 1 diteruskan ke Pass 1, Data 2 ke Pass 2, dan seterusnya.

Block hanya diproses setelah setiap input yang terhubung dari output block lain berisi data ([[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Eksekusi]]). Dengan aturan ini, Passer Block dapat dipakai untuk memastikan beberapa aliran selesai lebih dulu sebelum aliran berikutnya dilanjutkan.

Passer Block tersedia dalam lima varian, yaitu Passer 1 sampai Passer 5. Angka pada nama menunjukkan jumlah pasangan [[^input|Data]] dan [[^output|Pass]]. Fungsi dan aturan seluruh varian sama, sehingga semuanya dijelaskan pada halaman ini.

![[Docs/Modul Logic/Flow/Flow Block/Input dan Output/passer-block-flow.png|Passer Block varian Passer 1 sampai Passer 5]]

## Input dan Output

Passer Block memiliki satu sampai lima input di sisi kiri, satu sampai lima output di sisi kanan sesuai varian dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Data 1]] | [[^field|N/A Type]] | Data yang diteruskan ke [[^output|Pass 1]]. Tersedia pada semua varian. |
| [[^input|Data 2]] | [[^field|N/A Type]] | Data yang diteruskan ke [[^output|Pass 2]]. Tersedia mulai Passer 2. |
| [[^input|Data 3]] | [[^field|N/A Type]] | Data yang diteruskan ke [[^output|Pass 3]]. Tersedia mulai Passer 3. |
| [[^input|Data 4]] | [[^field|N/A Type]] | Data yang diteruskan ke [[^output|Pass 4]]. Tersedia mulai Passer 4. |
| [[^input|Data 5]] | [[^field|N/A Type]] | Data yang diteruskan ke [[^output|Pass 5]]. Tersedia pada Passer 5. |

Setiap [[^input|Data]] dapat berupa tipe data apa pun dan harus ditentukan lebih dulu lewat [[#Menentukan Tipe Data Input Data]].

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Pass 1]] | Sama dengan tipe data [[^input|Data 1]] | Meneruskan data [[^input|Data 1]] bila Output ini terhubung ke block lain. |
| [[^output|Pass 2]] | Sama dengan tipe data [[^input|Data 2]] | Meneruskan data [[^input|Data 2]] bila Output ini terhubung ke block lain. |
| [[^output|Pass 3]] | Sama dengan tipe data [[^input|Data 3]] | Meneruskan data [[^input|Data 3]] bila Output ini terhubung ke block lain. |
| [[^output|Pass 4]] | Sama dengan tipe data [[^input|Data 4]] | Meneruskan data [[^input|Data 4]] bila Output ini terhubung ke block lain. |
| [[^output|Pass 5]] | Sama dengan tipe data [[^input|Data 5]] | Meneruskan data [[^input|Data 5]] bila Output ini terhubung ke block lain. |

Aturan output mengalirkan data ke block lain sama seperti [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]]: [[^output|Pass]] yang tidak memiliki koneksi tidak mengeluarkan data, termasuk bila berada di tengah, dan [[^output|Pass]] lain tetap mengeluarkan data. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**note** Data tanpa tujuan
> [[^input|Data]] yang diisi langsung pada block tidak berguna bila [[^output|Pass]] pasangannya tidak terhubung ke block lain, karena data tidak diteruskan ke mana pun.

### Menentukan Tipe Data Input Data

Teks merah [[^field|N/A Type]] pada [[^input|Data]] berarti tipe data belum ditentukan. Tentukan tipe data dengan langkah berikut:

1. Klik kanan pada [[^input|Data]] yang ingin ditentukan.
2. Pilih [[^field|Change Type]].
3. Pilih [[Docs/Tipe Data/Pengenalan|tipe data]] yang sesuai dengan data yang akan dialirkan.

Bila [[^output|Pass]] pasangannya terhubung ke block lain, [[^input|Data]] tidak boleh dibiarkan [[^field|N/A Type]].

## Cara Kerja

1. Isi setiap [[^input|Data]] langsung pada block atau hubungkan dari output block lain.
2. Passer Block diproses setelah setiap [[^input|Data]] yang terhubung dari output block lain berisi data, sesuai [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat eksekusi]]. Dengan begitu block menunggu seluruh aliran yang terhubung ke [[^input|Data]] selesai.
3. Data pada [[^input|Data]] diteruskan tanpa diubah ke [[^output|Pass]] dengan nomor yang sama, hanya bila [[^output|Pass]] tersebut memiliki koneksi.

## Contoh Penggunaan

Contoh berikut memakai Passer 3 dengan [[^input|Data 1]] bertipe [[Docs/Tipe Data/String]] berisi [[^value/string|PSN-001]] (nomor pesanan), [[^input|Data 2]] bertipe [[Docs/Tipe Data/Number]] berisi [[^value/number|150000]] (total), dan [[^input|Data 3]] bertipe [[Docs/Tipe Data/Boolean]] berisi [[^value/boolean/true]].

| Kondisi | Pass 1 | Pass 2 | Pass 3 | Status |
| - | - | - | - | - |
| Ketiga Pass terhubung | [[^value/string|PSN-001]] | [[^value/number|150000]] | [[^value/boolean/true]] | [[^flowstate|Succeed]] |
| Pass 2 tidak terhubung | [[^value/string|PSN-001]] | - | [[^value/boolean/true]] | [[^flowstate|Succeed]] |
| Data 2 dibiarkan [[^field|N/A Type]] dan Pass 2 tidak terhubung | [[^value/string|PSN-001]] | - | [[^value/boolean/true]] | [[^flowstate|Succeed]] |
| Data 2 dibiarkan [[^field|N/A Type]] dan Pass 2 terhubung | - | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Pilih varian sesuai jumlah data.** Gunakan Passer Block dengan jumlah pasangan [[^input|Data]] dan [[^output|Pass]] yang sama dengan kebutuhan agar tidak ada pasangan yang tidak terpakai.
- **Hubungkan [[^output|Pass]] hanya untuk [[^input|Data]] yang dibutuhkan.** [[^input|Data]] yang diisi langsung tetapi [[^output|Pass]]-nya tidak terhubung tidak memberi manfaat.
- **Tentukan tipe data setiap [[^input|Data]] yang [[^output|Pass]]-nya terhubung.** [[^field|N/A Type]] pada pasangan tersebut menghasilkan [[^flowstate|Fatal Error]].
- **Gunakan Passer Block untuk menahan aliran** hingga seluruh aliran yang terhubung ke [[^input|Data]] selesai, lalu lanjutkan ke block berikutnya lewat [[^output|Pass]].

## Batasan dan Catatan

- Passer Block meneruskan data tanpa mengubahnya, dan nomor [[^output|Pass]] selalu sesuai dengan nomor [[^input|Data]].
- [[^input|Data]] bisa menjadi tidak berguna bila [[^output|Pass]] pasangannya tidak memiliki koneksi.
- Bila [[^output|Pass]] memiliki koneksi tetapi [[^input|Data]] pasangannya dibiarkan [[^field|N/A Type]], block berstatus [[^flowstate|Fatal Error]].
- Passer Block tidak berstatus [[^flowstate|Error]].
- Passer Block tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat Flow Block diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Pengenalan|Flow Block Input dan Output]]
- [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Aturan Koneksi]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]]
- [[Docs/Modul Logic/Flow/Flow Activity]]
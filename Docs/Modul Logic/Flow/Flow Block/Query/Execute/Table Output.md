---
    status: draft
    title: Table Output Block
    description: Flow Block untuk menjalankan Query berkaidah Table Output dan mengeluarkan hasilnya berupa Row pada komponen Flow.
    pageDecoration:
      tree:
        priority: 1
---

# Table Output Block

>**note** Table Output Block merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori [[Docs/Modul Logic/Flow/Flow Block/Query/Pengenalan|Flow Block Query]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Table Output Block adalah Flow Block yang menjalankan [[Docs/Tipe Data/Query]] berkaidah [[Docs/Query/Output/Table|Table Output]] dan mengeluarkan hasilnya berupa [[Docs/Tipe Data/Array]] yang berisi [[Docs/Tipe Data/Row]]. Bila hasil Query kosong, block mengeluarkan penanda bahwa hasilnya kosong.

Query yang dijalankan biasanya dibangun lebih dulu dengan [[Docs/Modul Logic/Flow/Flow Block/Query/Condition/Add Table Filter|Add Table Filter Block]].

![[Docs/Modul Logic/Flow/Flow Block/Query/Execute/table-output-block-flow.png|Table Output Block]]

<!--
  * [TODO] Penempatan gambar: potong screenshot menjadi `table-output-block-flow.png`, simpan di folder `Docs/Modul Logic/Flow/Flow Block/Query/Execute/`.
  * [TODO] Tautan asumsi: `Docs/Query/Output/Table` (dari penulis), `Docs/Tipe Data/Array`, dan `Docs/Modul Logic/Flow/Flow Block/Query/Pengenalan`.
-->

## Input dan Output

Table Output Block memiliki satu input di sisi kiri, dua output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Query]] | [[Docs/Tipe Data/Query]] | Query yang dijalankan. Harus menggunakan kaidah [[Docs/Query/Output/Table|Table Output]]. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Rows]] | [[Docs/Tipe Data/Array]] berisi [[Docs/Tipe Data/Row]] | Hasil Query. Keluar bila hasil Query berisi setidaknya satu [[Docs/Tipe Data/Row]]. |
| [[^output|Is Empty]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila hasil Query kosong dan aliran diteruskan. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

<!--
  * [TODO] Tombol [[^button/nolabel/q]] pada input Query (tampil pada screenshot) belum dijelaskan penulis, sehingga belum ditulis di halaman. Mohon jelaskan fungsinya.
  * [TODO] Diasumsikan [[^output|Is Empty]] hanya keluar bernilai true saat hasil kosong dan "-" saat hasil berisi, mengikuti pola output flag block lain. Mohon konfirmasi.
  * [TODO] Perilaku bila [[^input|Query]] tidak berkaidah Table Output belum dijelaskan penulis sehingga belum ditulis di tabel Contoh Penggunaan. Mohon konfirmasi statusnya.
-->

## Cara Kerja

1. Isi [[^input|Query]] langsung pada block atau hubungkan dari output block lain, misalnya [[^output|Query]] dari [[Docs/Modul Logic/Flow/Flow Block/Query/Condition/Add Table Filter|Add Table Filter Block]].
2. Setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat eksekusi]], block menjalankan Query.
3. Bila hasil berisi setidaknya satu [[Docs/Tipe Data/Row]], [[^output|Rows]] mengeluarkan seluruh hasil dan [[^output|Is Empty]] tidak mengeluarkan data.
4. Bila hasil kosong, [[^output|Is Empty]] mengeluarkan [[^value/boolean/true]] dan [[^output|Rows]] tidak mengeluarkan data.

## Contoh Penggunaan

Contoh berikut menjalankan Query berkaidah [[Docs/Query/Output/Table|Table Output]] atas Table pesanan.

| Kondisi | Rows | Is Empty | Status |
| - | - | - | - |
| Query menghasilkan tiga [[Docs/Tipe Data/Row]] | [[Docs/Tipe Data/Array]] berisi tiga [[Docs/Tipe Data/Row]] | - | [[^flowstate|Succeed]] |
| Query menghasilkan satu [[Docs/Tipe Data/Row]] | [[Docs/Tipe Data/Array]] berisi satu [[Docs/Tipe Data/Row]] | - | [[^flowstate|Succeed]] |
| Query tidak menghasilkan [[Docs/Tipe Data/Row]] | - | [[^value/boolean/true]] | [[^flowstate|Succeed]] |
| [[^input|Query]] dibiarkan kosong | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Persempit Query sebelum dijalankan.** Tambahkan filter dengan [[Docs/Modul Logic/Flow/Flow Block/Query/Condition/Add Table Filter|Add Table Filter Block]] agar [[^output|Rows]] hanya berisi [[Docs/Tipe Data/Row]] yang dibutuhkan.
- **Tangani hasil kosong.** Hubungkan block penanganan langsung ke [[^output|Is Empty]] agar Flow dapat memberi tahu pengguna ketika tidak ada [[Docs/Tipe Data/Row]] yang ditemukan.
- **Pastikan [[^input|Query]] berkaidah [[Docs/Query/Output/Table|Table Output]]** sebelum dihubungkan ke block ini.

## Batasan dan Catatan

- [[^output|Rows]] hanya mengeluarkan data bila hasil Query berisi setidaknya satu [[Docs/Tipe Data/Row]].
- [[^output|Is Empty]] hanya mengeluarkan [[^value/boolean/true]] ketika hasil Query kosong.
- [[^input|Query]] yang dibiarkan kosong menghasilkan [[^flowstate|Fatal Error]].
- Table Output Block tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat Flow Block diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Query/Pengenalan|Flow Block Query]]
- [[Docs/Modul Logic/Flow/Flow Block/Query/Condition/Add Table Filter|Query Add Table Filter Block]]
- [[Docs/Query/Output/Table|Table Output]]
- [[Docs/Tipe Data/Row]]
- [[Docs/Modul Logic/Flow/Flow Activity]]
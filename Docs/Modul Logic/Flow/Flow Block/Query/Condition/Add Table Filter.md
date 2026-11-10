---
    status: draft
    title: Add Table Filter Block
    description: Flow Block untuk menambahkan satu filter ke Query berbasis Table pada komponen Flow.
    pageDecoration:
      tree:
        priority: 2
---

# Add Table Filter Block

>**note** Add Table Filter Block merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori [[Docs/Modul Logic/Flow/Flow Block/Query/Pengenalan|Flow Block Query]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Add Table Filter Block adalah Flow Block yang menambahkan satu filter ke [[Docs/Tipe Data/Query]] berbasis [[Docs/Tipe Data/Table]]. Filter dibentuk dari [[^input|Column]], [[^input|Operator]], dan [[^input|Operand]] sebagai pembanding nilai Column, lalu block mengeluarkan Query baru yang sudah memuat filter tersebut.

Block ini hanya membangun Query. Untuk menjalankan Query dan mengambil [[Docs/Tipe Data/Row]], hubungkan [[^output|Query]] ke [[Docs/Modul Logic/Flow/Flow Block/Query/Execute/Table Output|Table Output Block]].

![[Docs/Modul Logic/Flow/Flow Block/Query/Condition/add-table-filter-block-flow.png|Add Table Filter Block]]

<!--
  * [DONE] Penempatan gambar: potong screenshot menjadi `add-table-filter-block-flow.png`, simpan di folder `Docs/Modul Logic/Flow/Flow Block/Query/Condition/`.
  * [DONE] Tautan asumsi: `Docs/Query/Filter/Operator`, `Docs/Query/Filter/Operand` (dari penulis), `Docs/Tipe Data/Pengenalan` (daftar seluruh Tipe Data), dan `Docs/Modul Logic/Flow/Flow Block/Query/Pengenalan`.
-->

## Input dan Output

Add Table Filter Block memiliki lima input di sisi kiri, satu output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Query]] | [[Docs/Tipe Data/Query]] | Query berbasis [[Docs/Tipe Data/Table]] yang akan ditambahkan filter. |
| [[^input|AND]] | [[Docs/Tipe Data/Boolean]] | Menentukan cara filter ini digabungkan: [[^value/boolean/true]] untuk kondisi AND dan [[^value/boolean/false]] untuk OR. |
| [[^input|Column]] | [[Docs/Tipe Data/Column]] | [[Docs/Tipe Data/Column]] yang nilainya dibandingkan. |
| [[^input|Operator]] | [[Docs/Tipe Data/String]] | Simbol operator yang valid. Selengkapnya lihat [[Docs/Query/Filter/Operator]]. |
| [[^input|Operand]] | [[^field|N/A Type]] | Data pembanding dari nilai [[^input|Column]]. Tipe data harus valid, selengkapnya lihat [[Docs/Query/Filter/Operand]]. Beberapa operator tidak memerlukan Operand. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Query]] | [[Docs/Tipe Data/Query]] | Query hasil penambahan filter pada [[^input|Query]] input. Keluar bila filter berhasil ditambahkan. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

<!--
  * [TODO] Tombol [[^button/nolabel/q]] pada input Query (tampil pada screenshot) belum dijelaskan penulis, sehingga belum ditulis di halaman. Mohon jelaskan fungsinya.
    Jawaban: Tombol Q adalah untuk menampilkan konfigurasi Query. Field Query memang memiliki tombol itu.
  * [TODO] Cara [[^input|AND]] menggabungkan filter dengan filter sebelumnya pada Query (termasuk bila filter ini adalah yang pertama) ditulis sebatas arti true sebagai AND dan false sebagai OR sesuai penjelasan penulis. Mohon konfirmasi.
    Jawaban: Sudah betul
-->

### Menentukan Tipe Data Operand

Teks merah [[^field|N/A Type]] pada [[^input|Operand]] berarti tipe data belum ditentukan. Tentukan tipe data dengan langkah berikut:

1. Klik kanan pada [[^input|Operand]].
2. Pilih [[^field|Change Type]].
3. Pilih [[Docs/Tipe Data/Pengenalan|tipe data]] yang sesuai dengan [[^input|Column]] dan [[^input|Operator]].

## Cara Kerja

1. Isi [[^input|Query]] langsung pada block atau hubungkan dari output block lain. [[Docs/Tipe Data/Query]] harus berbasis [[Docs/Tipe Data/Table]].
2. Isi [[^input|AND]], [[^input|Column]], [[^input|Operator]], dan [[^input|Operand]] untuk menentukan filter yang ditambahkan.
3. Setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat eksekusi]], block menambahkan filter ke [[^input|Query]] dan mengeluarkan [[^output|Query]] baru.
4. Hubungkan [[^output|Query]] ke Add Table Filter Block berikutnya untuk menambah filter lain, atau ke [[Docs/Modul Logic/Flow/Flow Block/Query/Execute/Table Output|Table Output Block]] untuk menjalankan Query.

### Aturan Operand

- Operator yang memerlukan Operand mewajibkan [[^input|Operand]] memiliki tipe data. [[^input|Operand]] yang dibiarkan [[^field|N/A Type]] menghasilkan [[^flowstate|Fatal Error]].
- Beberapa operator tidak memerlukan Operand, sehingga [[^input|Operand]] boleh dibiarkan [[^field|N/A Type]].
- [[^input|Operand]] yang bernilai kosong tetapi tipe datanya sudah ditentukan dianggap valid.

## Contoh Penggunaan

Contoh berikut menambahkan filter pada Query berbasis Table pesanan dengan [[^input|Column]] [[^field/column|Total]] bertipe [[Docs/Tipe Data/Number]] dan [[^input|Operator]] [[^value/string|>]].

| Kondisi | Output Query | Status |
| - | - | - |
| [[^input|AND]] [[^value/boolean/true]] dan [[^input|Operand]] [[^value/number|150000]] | Query dengan tambahan filter yang digabung secara AND | [[^flowstate|Succeed]] |
| [[^input|AND]] [[^value/boolean/false]] dan [[^input|Operand]] [[^value/number|150000]] | Query dengan tambahan filter yang digabung secara OR | [[^flowstate|Succeed]] |
| Operator yang tidak memerlukan Operand dan [[^input|Operand]] dibiarkan [[^field|N/A Type]] | Query dengan tambahan filter | [[^flowstate|Succeed]] |
| [[^input|Operand]] bertipe [[Docs/Tipe Data/Number]] dan dibiarkan kosong | Query dengan tambahan filter | [[^flowstate|Succeed]] |
| Operator memerlukan Operand dan [[^input|Operand]] dibiarkan [[^field|N/A Type]] | - | [[^flowstate|Fatal Error]] |
| [[^input|Query]], [[^input|AND]], [[^input|Column]], atau [[^input|Operator]] dibiarkan kosong | - | [[^flowstate|Fatal Error]] |
| Aturan pengisian [[^input|Operator]] atau [[^input|Operand]] tidak sesuai | - | [[^flowstate|Error]] |
| [[^input|Query]] berbasis data selain [[Docs/Tipe Data/Table]] | - | [[^flowstate|Error]] |

Status [[^flowstate|Error]] dan [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

<!--
  * [TODO] Simbol operator pada contoh ([[^value/string|>]]) dan Column Total adalah contoh generik. Mohon sesuaikan dengan simbol operator yang valid di Phoenix.
  * [TODO] Status Error pada block ini ditulis sesuai penjelasan penulis walau block tidak memiliki output Error. Mohon konfirmasi bahwa ini memang Error dan bukan Fatal Error.
-->

## Praktik Terbaik

- **Rangkai beberapa Add Table Filter Block** untuk kondisi bertingkat. Hubungkan [[^output|Query]] ke [[^input|Query]] block berikutnya agar setiap block menambahkan satu filter.
- **Sesuaikan tipe data [[^input|Operand]] dengan [[^input|Column]]** dan [[^input|Operator]] yang dipilih, karena aturan yang tidak sesuai menghasilkan [[^flowstate|Error]].
- **Pastikan [[^input|Query]] berbasis [[Docs/Tipe Data/Table]]** sebelum menambahkan filter.
- **Hubungkan [[^output|Query]] ke [[Docs/Modul Logic/Flow/Flow Block/Query/Execute/Table Output|Table Output Block]]** bila Anda membutuhkan [[Docs/Tipe Data/Row]] hasil filter.

## Batasan dan Catatan

- Satu Add Table Filter Block menambahkan satu filter. Block ini tidak menjalankan Query dan tidak mengeluarkan [[Docs/Tipe Data/Row]].
- [[^input|Query]] harus berbasis [[Docs/Tipe Data/Table]]. Bila tidak, block berstatus [[^flowstate|Error]].
- [[^input|Operand]] boleh dibiarkan [[^field|N/A Type]] hanya bila operator tidak memerlukannya. Bila operator memerlukannya, block berstatus [[^flowstate|Fatal Error]].
- [[^input|Query]], [[^input|AND]], [[^input|Column]], atau [[^input|Operator]] yang dibiarkan kosong menghasilkan [[^flowstate|Fatal Error]].
- Add Table Filter Block tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat Flow Block diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Query/Pengenalan|Flow Block Query]]
- [[Docs/Modul Logic/Flow/Flow Block/Query/Execute/Table Output|Query Table Output Block]]
- [[Docs/Query/Filter/Operator]]
- [[Docs/Query/Filter/Operand]]
- [[Docs/Tipe Data/Query]]
- [[Docs/Modul Logic/Flow/Flow Activity]]
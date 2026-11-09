---
    status: draft
    title: Assign Node Block
    description: Flow Block Data Tree yang menempatkan sebuah Node di bawah Node lain beserta seluruh keturunannya.
    pageDecoration:
      tree:
        priority: 15
---
# Assign Node Block

>**note** Assign Node Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Assign Node Block adalah Flow Block yang menempatkan sebuah [[Docs/Tipe Data/Node]] (Children) di bawah Node lain (Parent). Gunakan block ini untuk memindahkan Node beserta seluruh keturunannya ke posisi baru dalam [[Docs/Tipe Data/Tree]], misalnya memindahkan sebuah kategori ke kategori induk yang lain.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/assign-node-block-flow.png|Assign Node Block pada Blueprint Flow]]
## Input dan Output

Assign Node Block memiliki 3 input di sisi kiri, 4 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Parent]] | [[Docs/Tipe Data/Node]] | Node yang menjadi parent baru. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |
| [[^input|Order]] | [[Docs/Tipe Data/Number]] | Order Children pada Parent yang baru. Minimal [[^value/number|0]] dan tidak boleh sama dengan Order anak lain milik Parent. Bila bernilai negatif atau dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |
| [[^input|Children]] | [[Docs/Tipe Data/Node]] | Node yang ditempatkan di bawah Parent. Harus berada pada Tree yang sama dengan Parent. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Pass Children]] | [[Docs/Tipe Data/Node]] | Meneruskan Node Children yang diinput setelah ditempatkan di bawah Parent. |
| [[^output|Name Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Name Children sudah dipakai anak lain milik Parent. Node tidak dipindahkan. |
| [[^output|Order Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Order sudah dipakai anak lain milik Parent. Node tidak dipindahkan. |
| [[^output|Relation Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Parent adalah Node keturunan Children, atau Children adalah Origin. Node tidak dipindahkan. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**note** Perubahan oleh Flow tidak memicu Flow kembali
>Node yang diubah oleh Assign Node Block tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]], sehingga Flow tidak berjalan kembali karena perubahan dari Flow.

>**warning** Tree dengan Merger Mode atau External Read Only
>Assign Node Block dapat memindahkan Node pada [[Docs/Modul Data/Tree/Apa itu Tree|Tree]] yang [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] atau [[Docs/Modul Data/Tree/Konfigurasi External Read Only|External Read Only]]-nya aktif, termasuk Node hasil *clone*. Periksa Tree tujuan sebelum menjalankan Flow.

## Cara Kerja

1. Isi [[^input|Parent]], [[^input|Order]], dan [[^input|Children]], langsung pada block atau dari output block lain.
2. Block memeriksa bahwa Parent dan Children berada pada Tree yang sama. Bila tidak, block berstatus [[^flowstate|Error]] dan semua output tidak ada.
3. Block memeriksa bahwa Children bukan Origin dan Parent bukan keturunan Children, lalu memeriksa Name dan Order Children terhadap anak Parent yang sudah ada.
4. Bila tidak ada konflik, Children dipindahkan beserta seluruh keturunannya menjadi anak Parent dengan Order yang diinput, dan [[^output|Pass Children]] meneruskan Node tersebut.
5. Bila ada konflik, Node tidak dipindahkan dan hanya output konflik yang sesuai meneruskan aliran.

## Contoh Penggunaan

Tabel berikut memakai Tree Kategori Produk. Node [[^value/node|Elektronik]] memiliki anak [[^value/node|Komputer]] (Order [[^value/number|0]], memiliki anak [[^value/node|Laptop]]) dan [[^value/node|Ponsel]] (Order [[^value/number|1]]), sedangkan Node [[^value/node|Aksesori]] berada langsung di bawah Origin.

| Kondisi | Pass Children | Name Conflict | Order Conflict | Relation Conflict | Status |
| ------- | ------------- | ------------- | -------------- | ----------------- | ------ |
| Parent [[^value/node|Elektronik]], Children [[^value/node|Aksesori]], Order [[^value/number|2]] belum dipakai | [[^value/node|Aksesori]] | - | - | - | [[^flowstate|Succeed]] |
| Order [[^value/number|1]] sudah dipakai anak lain milik Parent | - | - | [[^value/boolean/true]] | - | [[^flowstate|Error]] |
| Name Children sama dengan salah satu anak Parent | - | [[^value/boolean/true]] | - | - | [[^flowstate|Error]] |
| Parent [[^value/node|Laptop]] adalah keturunan Children [[^value/node|Elektronik]] | - | - | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| Children adalah Node Origin | - | - | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| Parent dan Children berada pada Tree yang berbeda | - | - | - | - | [[^flowstate|Error]] |
| [[^input|Order]] bernilai negatif | - | - | - | - | [[^flowstate|Fatal Error]] |
| [[^input|Parent]], [[^input|Order]], atau [[^input|Children]] dibiarkan kosong | - | - | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Error]] dan [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Pastikan Parent dan Children berasal dari Tree yang sama sebelum menjalankan block, misalnya dengan membandingkan output **[[^output|Tree]]** dari [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]].
- Gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]] untuk membuat Node baru, dan Assign Node Block untuk memindahkan Node yang sudah ada.

## Batasan dan Catatan

- [[^input|Order]] bernilai minimal [[^value/number|0]]. Order negatif membuat block berstatus [[^flowstate|Fatal Error]].
- Seluruh keturunan Children ikut berpindah bersama Children.
- Children tidak dapat ditempatkan di bawah Node keturunannya sendiri, dan Origin tidak dapat dijadikan Children.
- Menempatkan Children pada Parent yang sudah menjadi parent-nya tidak menghasilkan Relation Conflict dan tidak mengubah hubungan parent-nya.
- Karena bukan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]], Assign Node Block hanya dieksekusi bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Delete Node|Delete Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]]
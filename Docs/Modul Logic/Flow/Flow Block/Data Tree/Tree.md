---
    status: draft
    title: Tree Block
    description: Flow Block Data Tree yang mengambil atribut Tree, yaitu Name, Description, dan Merger Mode.
    pageDecoration:
      tree:
        priority: 19
---
# Tree Block

>**note** Tree Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Tree Block adalah Flow Block yang menerima sebuah [[Docs/Tipe Data/Tree]] lalu mengeluarkan atribut Tree tersebut, yaitu Name, Description, dan [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]]. Gunakan block ini bila Flow membutuhkan informasi sebuah [[Docs/Modul Data/Tree/Apa itu Tree|Tree]], misalnya untuk menampilkan nama Tree pada pesan atau memeriksa apakah Tree bersifat merger sebelum menambahkan Node.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/tree-block-flow.png|Tree Block pada Blueprint Flow]]
## Input dan Output

Tree Block memiliki 1 input di sisi kiri, 4 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Tree]] | [[Docs/Tipe Data/Tree]] | Pilih Tree atau hubungkan dari output block lain. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Pass]] | [[Docs/Tipe Data/Tree]] | Meneruskan Tree yang diinput. |
| [[^output|Name]] | [[Docs/Tipe Data/String]] | Name Tree. |
| [[^output|Desc]] | [[Docs/Tipe Data/Text]] | Description Tree. Tetap meneruskan aliran bernilai [[^value/empty]] bila Description kosong. |
| [[^output|Merger Mode]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Tree bersifat merger, [[^value/boolean/false]] bila tidak. Selengkapnya lihat [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]]. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Isi [[^input|Tree]] dengan [[Docs/Tipe Data/Tree]] atau hubungkan dari output block lain.
2. Saat dieksekusi, [[^output|Pass]] meneruskan Tree yang diinput, sedangkan [[^output|Name]], [[^output|Desc]], dan [[^output|Merger Mode]] mengeluarkan atribut Tree tersebut.
3. Hubungkan output yang Anda butuhkan ke block berikutnya.

## Contoh Penggunaan

Tabel berikut menunjukkan hasil Tree Block untuk beberapa kondisi input.

| Kondisi | Pass | Name | Desc | Merger Mode | Status |
| ------- | ---- | ---- | ---- | ----------- | ------ |
| Tree terisi, Description terisi, bukan merger | [[^value/tree|Kategori Produk]] | [[^value/string|Kategori Produk]] | [[^value/text|Hierarki kategori produk]] | [[^value/boolean/false]] | [[^flowstate|Succeed]] |
| Tree terisi, Description kosong | [[^value/tree|Kategori Produk]] | [[^value/string|Kategori Produk]] | [[^value/empty]] | [[^value/boolean/false]] | [[^flowstate|Succeed]] |
| Tree terisi dan bersifat merger | [[^value/tree|Kategori Gabungan]] | [[^value/string|Kategori Gabungan]] | [[^value/text|Gabungan beberapa Tree]] | [[^value/boolean/true]] | [[^flowstate|Succeed]] |
| [[^input|Tree]] dibiarkan kosong | - | - | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Hubungkan **[[^output|Pass]]** ke block berikutnya bila Flow masih membutuhkan Tree yang sama, misalnya ke [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]].
- Gunakan **[[^output|Merger Mode]]** bersama [[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If|If Operator Block]] untuk memisahkan alur antara Tree biasa dan Tree merger.

## Batasan dan Catatan

- Tree Block hanya membaca atribut Tree. Untuk atribut [[Docs/Tipe Data/Node]], gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]].
- [[^input|Tree]] yang kosong membuat block berstatus [[^flowstate|Fatal Error]] dan semua output tidak ada.
- Karena bukan Flow Block Event, Tree Block hanya dieksekusi bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]]
- [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]


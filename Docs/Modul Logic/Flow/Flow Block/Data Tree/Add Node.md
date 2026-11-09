---
    status: draft
    title: Add Node Block
    description: Flow Block Data Tree yang menambahkan Node baru sebagai anak dari sebuah Node.
    pageDecoration:
      tree:
        priority: 16
---
# Add Node Block

>**note** Add Node Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Add Node Block adalah Flow Block yang menambahkan [[Docs/Tipe Data/Node]] baru sebagai anak dari Node lain. Gunakan block ini untuk membangun hierarki [[Docs/Tipe Data/Tree]] secara otomatis dari Flow, misalnya menambahkan kategori baru ketika data baru masuk.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/add-node-block-flow.png|Add Node Block pada Blueprint Flow]]
## Input dan Output

Add Node Block memiliki 3 input di sisi kiri, 3 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Parent]] | [[Docs/Tipe Data/Node]] | Node yang akan menjadi parent Node baru. Pilihan memuat semua Node dari semua Tree, atau hubungkan dari output block lain. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |
| [[^input|Order]] | [[Docs/Tipe Data/Number]] | Order Node baru. Minimal [[^value/number|0]], tidak boleh negatif, dan tidak boleh sama dengan Order anak lain milik Parent. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |
| [[^input|Name]] | [[Docs/Tipe Data/String]] | Name Node baru. Tidak boleh sama dengan Name anak lain milik Parent. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|New Node]] | [[Docs/Tipe Data/Node]] | Node baru yang ditambahkan sebagai anak Parent. Keluar bila Node berhasil ditambahkan. |
| [[^output|Name Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Name sudah dipakai anak lain milik Parent. Node baru tidak dibuat. |
| [[^output|Order Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Order sudah dipakai anak lain milik Parent. Node baru tidak dibuat. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**note** Perubahan oleh Flow tidak memicu Flow kembali
>Node yang ditambahkan oleh Add Node Block tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]] meskipun block tersebut memiliki event [[^value/string|create]], sehingga Flow tidak berjalan kembali karena perubahan dari Flow.

## Cara Kerja

1. Pilih [[^input|Parent]], lalu isi [[^input|Order]] dan [[^input|Name]], langsung pada block atau dari output block lain.
2. Block memeriksa [[^input|Name]] lalu [[^input|Order]] terhadap anak Parent yang sudah ada.
3. Bila tidak ada konflik, Node baru dibuat sebagai anak Parent pada Tree yang sama dengan Parent, dan [[^output|New Node]] meneruskan Node tersebut.
4. Bila ada konflik, Node baru tidak dibuat dan hanya [[^output|Name Conflict]] atau [[^output|Order Conflict]] yang meneruskan aliran.

<!--
  * [TODO] Konfirmasi: pemeriksaan diasumsikan berurutan Name lalu Order, dan hanya satu output konflik yang keluar pada satu eksekusi.
    Jawaban: Ya betul
  * [TODO] Konfirmasi: status block bila Order bernilai negatif (diasumsikan Error tanpa output).
    Jawaban: Masuknya Fatal Error (karena tidak ada output jika error)
-->

## Contoh Penggunaan

Tabel berikut memakai Parent [[^value/node|Elektronik]] yang sudah memiliki anak [[^value/node|Komputer]] (Order [[^value/number|0]]) dan [[^value/node|Ponsel]] (Order [[^value/number|1]]).

| Kondisi | New Node | Name Conflict | Order Conflict | Status |
| ------- | -------- | ------------- | -------------- | ------ |
| Name [[^value/string|Kamera]] dan Order [[^value/number|2]] belum dipakai anak lain | [[^value/node|Kamera]] | - | - | [[^flowstate|Succeed]] |
| Name [[^value/string|Ponsel]] sudah dipakai anak lain | - | [[^value/boolean/true]] | - | [[^flowstate|Error]] |
| Order [[^value/number|1]] sudah dipakai anak lain | - | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| [[^input|Parent]], [[^input|Order]], atau [[^input|Name]] dibiarkan kosong | - | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Error]] dan [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Untuk menambahkan Node langsung di bawah Origin, hubungkan output **[[^output|The Origin (Node)]]** dari [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]] ke [[^input|Parent]].
- Periksa Order anak Parent dengan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]] bila Flow perlu menentukan Order yang masih tersedia.

## Batasan dan Catatan

- [[^input|Order]] bernilai minimal [[^value/number|0]].
- Node baru berada pada Tree yang sama dengan Parent dan belum memiliki anak. Untuk memindahkan Node yang sudah ada, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]].
- Karena bukan Flow Block Event, Add Node Block hanya dieksekusi bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Delete Node|Delete Node Block]]


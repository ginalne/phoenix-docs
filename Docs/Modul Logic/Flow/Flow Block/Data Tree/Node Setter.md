---
    status: draft
    title: Node Setter Block
    description: Flow Block Data Tree yang mengubah Name dan Order sebuah Node.
    pageDecoration:
      tree:
        priority: 17
---
# Node Setter Block

>**note** Node Setter Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Node Setter Block adalah Flow Block yang mengubah Name dan Order sebuah [[Docs/Tipe Data/Node]]. Gunakan block ini untuk mengganti nama atau menggeser urutan Node secara otomatis dari Flow.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/node-setter-block-flow.png|Node Setter Block pada Blueprint Flow]]
## Input dan Output

Node Setter Block memiliki 3 input di sisi kiri, 3 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Node yang akan diubah. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |
| [[^input|Order]] | [[Docs/Tipe Data/Number]] | Order baru Node. Minimal [[^value/number|0]], tidak boleh negatif, dan tidak boleh sama dengan Order saudara kandung Node. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |
| [[^input|Name]] | [[Docs/Tipe Data/String]] | Name baru Node. Tidak boleh sama dengan Name saudara kandung Node. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Pass]] | [[Docs/Tipe Data/Node]] | Meneruskan Node yang diinput setelah Name dan Order diubah. |
| [[^output|Name Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Name sudah dipakai saudara kandung Node. Node tidak diubah. |
| [[^output|Order Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Order sudah dipakai saudara kandung Node. Node tidak diubah. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**note** Perubahan oleh Flow tidak memicu Flow kembali
>Node yang diubah oleh Node Setter Block tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]], sehingga Flow tidak berjalan kembali karena perubahan dari Flow.

>**warning** Tree dengan Merger Mode atau External Read Only
>Node Setter Block dapat mengubah Node pada [[Docs/Modul Data/Tree/Apa itu Tree|Tree]] yang [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] atau [[Docs/Modul Data/Tree/Konfigurasi External Read Only|External Read Only]]-nya aktif, termasuk Node hasil *clone*. Periksa Tree tujuan sebelum menjalankan Flow.

## Cara Kerja

1. Isi [[^input|Node]], [[^input|Order]], dan [[^input|Name]], langsung pada block atau dari output block lain.
2. Block memeriksa [[^input|Name]] lalu [[^input|Order]] terhadap saudara kandung Node, yaitu Node lain yang memiliki parent yang sama.
3. Bila tidak ada konflik, Name dan Order Node diganti dan [[^output|Pass]] meneruskan Node tersebut.
4. Bila ada konflik, Node tidak diubah dan hanya [[^output|Name Conflict]] atau [[^output|Order Conflict]] yang meneruskan aliran.

Node Setter Block mengubah **Name dan Order sekaligus**. Bila Anda hanya ingin mengubah salah satunya, isi atribut lainnya dengan nilai Node saat ini, misalnya dari [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]].

<!--
  * [TODO] Konfirmasi: pemeriksaan diasumsikan berurutan Name lalu Order, dan hanya satu output konflik yang keluar pada satu eksekusi. Mohon konfirmasi urutan dan perilaku bila keduanya konflik.
  * [TODO] Konfirmasi: Name dan Order milik Node itu sendiri diasumsikan bukan konflik (seperti Name pada EnumData Setter).
  * [TODO] Konfirmasi: status block bila Order bernilai negatif (diasumsikan Error tanpa output).
  * [TODO] Konfirmasi: apakah Name dan Order Node Origin dapat diubah lewat block ini.
-->

## Contoh Penggunaan

Tabel berikut memakai Node [[^value/node|Ponsel]] (Order [[^value/number|1]]) yang berada di bawah Node [[^value/node|Elektronik]] bersama saudara kandungnya, Node [[^value/node|Komputer]] (Order [[^value/number|0]]).

| Kondisi | Pass | Name Conflict | Order Conflict | Status |
| ------- | ---- | ------------- | -------------- | ------ |
| Node [[^value/node|Ponsel]] diubah dengan Name [[^value/string|Telepon Pintar]] dan Order [[^value/number|2]] | [[^value/node|Telepon Pintar]] | - | - | [[^flowstate|Succeed]] |
| Name [[^value/string|Komputer]] sudah dipakai saudara kandung | - | [[^value/boolean/true]] | - | [[^flowstate|Error]] |
| Order [[^value/number|0]] sudah dipakai saudara kandung | - | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| [[^input|Node]], [[^input|Order]], atau [[^input|Name]] dibiarkan kosong | - | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Error]] dan [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Periksa nilai Name dan Order saudara kandung dengan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]] dan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]] sebelum mengubah Node.
- Hubungkan **[[^output|Pass]]** ke block berikutnya bila Flow masih membutuhkan Node yang sama.

## Batasan dan Catatan

- [[^input|Order]] bernilai minimal [[^value/number|0]].
- [[^input|Name]] dan [[^input|Order]] hanya diperiksa terhadap saudara kandung, yaitu Node lain dengan parent yang sama.
- Karena bukan Flow Block Event, Node Setter Block hanya dieksekusi bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]]
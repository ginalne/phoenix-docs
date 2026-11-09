---
    status: draft
    title: Delete Node Block
    description: Flow Block Data Tree yang menghapus sebuah Node beserta seluruh anaknya.
    pageDecoration:
      tree:
        priority: 14
---
# Delete Node Block

>**note** Delete Node Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Delete Node Block adalah Flow Block yang menghapus sebuah [[Docs/Tipe Data/Node]] beserta seluruh anaknya. Gunakan block ini untuk membersihkan hierarki [[Docs/Tipe Data/Tree]] secara otomatis dari Flow, misalnya menghapus kategori yang sudah tidak dipakai.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/delete-node-block-flow.png|Delete Node Block pada Blueprint Flow]]
## Input dan Output

Delete Node Block memiliki 2 input di sisi kiri, 2 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Node yang akan dihapus. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |
| [[^input|Force]] | [[Docs/Tipe Data/Boolean]] | Isi [[^value/boolean/true]] untuk memaksa penghapusan Node yang sudah digunakan oleh komponen lain. Bila dibiarkan kosong, block berstatus [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Succeed]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Node beserta seluruh anaknya berhasil dihapus dan aliran diteruskan. |
| [[^output|Error]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila penghapusan ditolak dan aliran diteruskan. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**danger** Penghapusan tidak dapat dikembalikan
>Node yang dihapus tidak dapat dikembalikan, dan seluruh anak serta keturunannya ikut terhapus.

>**warning** Hapus paksa
>Bila [[^input|Force]] bernilai [[^value/boolean/true]], Node tetap dihapus walaupun sudah digunakan oleh komponen lain, sehingga relasi dari komponen tersebut dapat terputus.

>**warning** Tree dengan Merger Mode atau External Read Only
>Delete Node Block dapat menghapus Node pada [[Docs/Modul Data/Tree/Apa itu Tree|Tree]] yang [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] atau [[Docs/Modul Data/Tree/Konfigurasi External Read Only|External Read Only]]-nya aktif, termasuk Node hasil *clone*. Periksa Tree tujuan sebelum menjalankan Flow.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
>Node yang diubah oleh Delete Node Block tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]], sehingga Flow tidak berjalan kembali karena perubahan dari Flow.

## Cara Kerja

1. Isi [[^input|Node]] dan [[^input|Force]], langsung pada block atau dari output block lain.
2. Block memeriksa apakah Node atau salah satu anaknya sudah digunakan oleh komponen lain.
3. Bila belum digunakan, Node beserta seluruh anaknya dihapus dan hanya [[^output|Succeed]] yang meneruskan aliran.
4. Bila sudah digunakan dan [[^input|Force]] bernilai [[^value/boolean/false]], penghapusan ditolak, tidak ada Node yang terhapus, dan hanya [[^output|Error]] yang meneruskan aliran.
5. Bila sudah digunakan dan [[^input|Force]] bernilai [[^value/boolean/true]], Node beserta seluruh anaknya dihapus paksa dan hanya [[^output|Succeed]] yang meneruskan aliran.

>**note** Mengelola Error
>Hubungkan output [[^output|Error]] ke block penanganan, misalnya [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]], agar Flow dapat memberi tahu pengguna. Block tersebut hanya dieksekusi bila penghapusan ditolak.

<!--
  * [TODO] Konfirmasi: Node dianggap sudah digunakan bila Node itu atau salah satu anaknya dipakai oleh komponen lain. Apakah definisinya sama dengan Delete Row (dipakai pada Flow atau data lain, atau tercatat di riwayat activity)?
  * [TODO] Konfirmasi: Node Origin diasumsikan tidak dapat dihapus sehingga penghapusannya berstatus Error, apa pun nilai Force.
  * [TODO] Konfirmasi: dampak hapus paksa pada komponen yang memakai Node (diasumsikan relasinya terputus).
-->

## Contoh Penggunaan

Tabel berikut menunjukkan hasil Delete Node Block untuk beberapa kondisi. Pada setiap kondisi yang berhasil, anak Node ikut terhapus.

| Kondisi | Force | Succeed | Error | Status |
| ------- | ----- | ------- | ----- | ------ |
| Node dan anaknya belum digunakan komponen lain | [[^value/boolean/false]] | [[^value/boolean/true]] | - | [[^flowstate|Succeed]] |
| Node atau salah satu anaknya sudah digunakan komponen lain | [[^value/boolean/false]] | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| Node atau salah satu anaknya sudah digunakan komponen lain | [[^value/boolean/true]] | [[^value/boolean/true]] | - | [[^flowstate|Succeed]] |
| [[^input|Node]] atau [[^input|Force]] dibiarkan kosong | - | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Error]] dan [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Periksa anak Node dengan [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]] sebelum menghapus, karena seluruh anaknya ikut terhapus.
- Biarkan [[^input|Force]] bernilai [[^value/boolean/false]] kecuali Anda yakin Node yang sudah digunakan memang harus dihapus, lalu andalkan output [[^output|Error]] untuk mengetahui bahwa Node masih digunakan.

## Batasan dan Catatan

- [[^input|Force]] yang dibiarkan kosong menghasilkan [[^flowstate|Fatal Error]], tidak diperlakukan sebagai [[^value/boolean/false]].
- Node Origin tidak dapat dihapus.
- Karena bukan Flow Block Event, Delete Node Block hanya dieksekusi bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Flow Block Data Tree]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]]
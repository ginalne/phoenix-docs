---
    status: release
    title: Menambahkan Node
    description: Cara menambahkan Node baru sebagai anak dari Node lain pada Tree.
    pageDecoration:
      tree:
        priority: 9
---
# Menambahkan Node

Menambahkan [[Docs/Tipe Data/Node|Node]] berarti membuat Node baru sebagai anak dari Node yang sudah ada di [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]. Tree yang baru dibuat hanya memiliki satu Node bernama Origin, sehingga Node pertama yang Anda tambahkan menjadi anak dari Origin.

## Menambahkan Node Baru

![[Docs/Modul Data/Tree/Node/edit-node.png|Panel Edit untuk menambahkan Node anak]]
1. Buka halaman kerja [[Docs/Modul Data/Tree/Apa itu Tree|Tree]] yang akan diisi.
2. Klik kanan [[Docs/Tipe Data/Node|Node]] yang akan menjadi induk ➜ [[^field/edit|Edit]].
3. Pada bagian [[^field|Children]], klik [[^button/add|Add]].
4. Isi [[^field|Name]] dan [[^field|Order]] untuk Node baru.
5. Klik [[^button|Update]].

Anda dapat klik [[^button/x|Cancel]] untuk membatalkan penambahan Node.

>**success** Node berhasil ditambahkan
> Node baru tampil sebagai anak dari Node induk pada area kerja.

Contoh: untuk menambahkan Node [[^value/node|Laptop]] di bawah Node [[^value/node|Komputer]], klik kanan [[^value/node|Komputer]] ➜ [[^field/edit|Edit]], lalu tambahkan anak dengan [[^field|Name]] [[^value/string|Laptop]] dan [[^field|Order]] [[^value/number|0]].

<!--
  * [DONE] Menu konteks Node (node-menu.png) tidak memiliki Add. Saya mengasumsikan Node ditambahkan lewat Edit pada Node induk ➜ bagian Children ➜ Add. Mohon konfirmasi langkah sebenarnya beserta label field dan tombolnya (Children, Add, Name, Order, Update).
  * [DONE] Letakkan gambar edit-node.png (panel Edit Node) dengan penanda angka: 1) bagian Children, 2) tombol Add, 3) field Name dan Order, 4) tombol Update.
  * [DONE] Nama contoh (Komputer dan Laptop) adalah nama generik. Sesuaikan dengan gambar Anda.
-->

### Aturan Name dan Order

| Field | Aturan |
| ----- | ------ |
| [[^field|Name]] | Harus unik di antara saudara kandung, yaitu [[Docs/Tipe Data/Node|Node]] lain dengan parent yang sama. |
| [[^field|Order]] | Angka minimal [[^value/number|0]] dan harus unik di antara saudara kandung. Selengkapnya lihat [[Docs/Modul Data/Tree/Node/Mengubah Urutan|Mengubah Urutan]]. |

Bila [[^field|Name]] atau [[^field|Order]] bentrok dengan saudara kandung, Node tidak tersimpan dan sistem menampilkan pesan kesalahan.

<!--
  * [TODO] Perilaku saat Name atau Order bentrok saya asumsikan sama dengan Flow (Name Conflict dan Order Conflict): Node tidak tersimpan. Mohon konfirmasi apakah ada pesan khusus atau Order otomatis bergeser.
    Jawaban: Ada pesan Error
-->

## Menambahkan Node dari Tree Lain

Langkah ini hanya tersedia pada Tree dengan [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] aktif. Tree non-merger tidak dapat menambahkan Node dari Tree lain.

1. Klik kanan [[Docs/Tipe Data/Node|Node]] induk di Tree merger ➜ [[^field/edit|Edit]].
2. Pada bagian [[^field|Children]], klik [[^button/add|Add Children]] dan pilih Node dari Tree non-merger yang akan ditambahkan.
3. Tentukan apakah Node hasil *clone* mengikuti perubahan Node asal.
4. Klik [[^button|Update]].

Pengaruh perubahan Node asal pada Node hasil *clone* diatur oleh [[Docs/Modul Data/Tree/Konfigurasi External Read Only|External Read Only]].

<!--
  * [TODO] Langkah clone di atas masih tebakan karena belum ada screenshot. Mohon konfirmasi cara memilih Node dari Tree lain dan label pilihan "mengikuti perubahan Node asal".
    Jawaban : Sudah sesuai
-->

>**note** Hak akses dan Event
> Menambahkan Node memerlukan [[Docs/Modul Developer/Workspace/Data Access#Data yang Diatur pada Setiap Komponen|Data Access]] Add pada Tree: Node bernilai [[^value/boolean/allow]]. Setiap Node baru, termasuk Node hasil *clone*, memicu event [[^value/string|create]] pada [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]].

## Lihat Juga

- [[Docs/Modul Data/Tree/Node/Mengubah Nama|Mengubah Nama Node]]
- [[Docs/Modul Data/Tree/Node/Mengubah Urutan|Mengubah Urutan Node]]
- [[Docs/Modul Data/Tree/Node/Mengimpor|Mengimpor Node]] untuk menambahkan banyak Node sekaligus.
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]] untuk menambahkan Node lewat Flow.
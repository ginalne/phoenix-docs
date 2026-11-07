---
    status: draft
    title: Flow Block Data Table
    description: Pengenalan kelompok Flow Block Data Table, block untuk menambah, membaca, mengubah, dan menghapus Row serta TableData lewat logika Flow.
    pageDecoration:
      tree:
        priority: 10
    tags: flowblock-category
---
# Flow Block Data Table

>**note** Flow Block Data Table merupakan salah satu kelompok [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori Data dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Data Table adalah kelompok [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang dipakai untuk mengakses komponen [[Docs/Modul Data/Table/Apa itu Table|Table]] melalui logika [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]]. Dengan kelompok ini, alur Anda dapat membaca atribut [[Docs/Tipe Data/Table]], [[Docs/Tipe Data/Column]], dan [[Docs/Tipe Data/Row]], membaca atau mengubah [[Docs/Tipe Data/TableData]], serta menambah dan menghapus Row secara otomatis, tanpa membuka halaman kerja Table.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur dan memiliki Control serta output yang mirip, block Data bekerja setelah menerima data dari block sebelumnya sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Setiap block pada kelompok ini juga unik sesuai fungsinya: ada yang membaca atribut Table, Column, atau Row, ada yang membaca dan mengubah TableData, dan ada yang menambah atau menghapus Row. Karena itu Anda memilih block berdasarkan peran yang dibutuhkan di alur, bukan berdasarkan pola input dan output yang seragam.

![[Docs/Modul Logic/Flow/Flow Block/Data Table/data-table-block-flow.png|Tujuh Flow Block Data Table pada Blueprint: Add Row, Delete Row, Table, Table Column, Table Row, TableData Getter, dan TableData Setter]]

Block Data Table umumnya berada di tengah atau di ujung alur. Misalnya, alur dimulai dari perubahan [[Docs/Tipe Data/Row]] pada sebuah Table, membaca [[Docs/Tipe Data/TableData]] dari Row tersebut, mengolahnya, lalu menambahkan Row baru ke Table lain.

>**note** Perubahan data oleh Flow tidak memicu Flow kembali
> Aksi menambahkan, mengubah, atau menghapus [[Docs/Tipe Data/Row]] yang dilakukan oleh block Data Table tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event|Table Row Event Block]]. Perubahan dari sumber lain, seperti pengisian manual di halaman kerja Table, Import, atau Upload, tetap memicu Event.

>**warning** Menghapus Row lewat Flow
> [[Docs/Modul Logic/Flow/Flow Block/Data Table/Delete Row|Delete Row Block]] menghapus [[Docs/Tipe Data/Row]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]], dan Row yang dihapus tidak dapat dikembalikan. [[Docs/Tipe Data/TableData]] pada Row tersebut ikut hilang.

## Jenis Flow Block Data Table

Phoenix menyediakan tujuh Flow Block Data Table. Selengkapnya tentang komponennya lihat [[Docs/Modul Data/Table/Apa itu Table|Table]].

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/Add Row|Add Row Block]] | Menambahkan [[Docs/Tipe Data/Row]] baru ke sebuah [[Docs/Modul Data/Table/Apa itu Table|Table]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/Delete Row|Delete Row Block]] | Menghapus [[Docs/Tipe Data/Row]] dari sebuah [[Docs/Modul Data/Table/Apa itu Table|Table]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table|Table Block]] | Mengambil nilai atribut [[Docs/Modul Data/Table/Apa itu Table|Table]], yaitu [[^field|Name]] dan [[^field|Description]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Column|Table Column Block]] | Mengambil nilai atribut [[Docs/Tipe Data/Column]] pada sebuah [[Docs/Tipe Data/Table]], yaitu [[^field|Name]], [[^field|Description]], [[^field|Header]], dan [[^field|Table]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]] | Mengambil nilai atribut [[Docs/Tipe Data/Row]] pada sebuah [[Docs/Tipe Data/Table]], yaitu [[^field|Index]] dan [[^field|Name]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Getter|TableData Getter Block]] | Mengambil [[Docs/Tipe Data/TableData]] dari sebuah [[Docs/Tipe Data/Row]] pada [[Docs/Tipe Data/Column]] tertentu. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Setter|TableData Setter Block]] | Mengubah satu [[Docs/Tipe Data/TableData]] pada sebuah [[Docs/Tipe Data/Row]] di [[Docs/Tipe Data/Column]] tertentu. |

## Memilih Flow Block Data Table

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menambahkan [[Docs/Tipe Data/Row]] baru ke sebuah Table. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/Add Row|Add Row Block]] |
| Menghapus [[Docs/Tipe Data/Row]] yang tidak dipakai lagi. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/Delete Row|Delete Row Block]] |
| Membaca [[^field|Name]] dan [[^field|Description]] sebuah [[Docs/Modul Data/Table/Apa itu Table|Table]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table|Table Block]] |
| Membaca [[^field|Name]], [[^field|Description]], [[^field|Header]], dan [[^field|Table]] sebuah [[Docs/Tipe Data/Column]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Column|Table Column Block]] |
| Membaca [[^field|Index]] dan [[^field|Name]] sebuah [[Docs/Tipe Data/Row]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]] |
| Membaca isi sel pada Row dan Column tertentu. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Getter|TableData Getter Block]] |
| Mengubah isi satu sel pada Row dan Column tertentu. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Setter|TableData Setter Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Data/Table/Apa itu Table|Table]]
- [[Docs/Modul Data/Table/Mengotomasi|Mengotomasi Table]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]
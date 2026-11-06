---
    status: draft
    title: Flow Block Data Enum
    description: Pengenalan kelompok Flow Block Data Enum, block untuk menambah, membaca, mengubah, dan menghapus EnumData lewat logika Flow.
    pageDecoration:
      tree:
        priority: 10
    tags: flowblock-category
---
# Flow Block Data Enum

>**note** Flow Block Data Enum merupakan salah satu kelompok [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori Data dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Data Enum adalah kelompok [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang dipakai untuk mengakses komponen [[Docs/Modul Data/Enum/Apa itu Enum|Enum]] melalui logika [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]]. Dengan kelompok ini, alur Anda dapat membaca atribut Enum, serta menambahkan, membaca, mengubah, dan menghapus [[Docs/Tipe Data/EnumData]] secara otomatis, tanpa membuka halaman kerja Enum.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur dan memiliki Control serta output yang mirip, block Data bekerja setelah menerima data dari block sebelumnya sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Setiap block pada kelompok ini juga unik sesuai fungsinya: ada yang membaca atribut Enum atau EnumData, ada yang mengambil atau mengubah EnumData, dan ada yang menambah atau menghapus EnumData. Karena itu Anda memilih block berdasarkan peran yang dibutuhkan di alur, bukan berdasarkan pola input dan output yang seragam.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/data-enum-block-flow.png|Tujuh Flow Block Data Enum pada Blueprint: Add EnumData, Delete EnumData, Enum, EnumData, EnumData Getter, EnumData Setter, dan EnumData Value]]

Block Data Enum umumnya berada di tengah atau di ujung alur. Alur menerima pemicu dari block sebelumnya, lalu menambahkan, membaca, atau mengubah [[Docs/Tipe Data/EnumData]] pada [[Docs/Modul Data/Enum/Apa itu Enum|Enum]] yang dituju.

>**note** Perubahan data oleh Flow tidak memicu Flow kembali
> Aksi menambahkan, mengubah, atau menghapus [[Docs/Tipe Data/EnumData]] yang dilakukan oleh block Data Enum tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event|Enum Data Event Block]]. Perubahan dari sumber lain, seperti pengisian manual di halaman kerja Enum, Import, atau Upload, tetap memicu Event.

>**warning** Menambahkan EnumData pada Enum dengan Strict On Selected
> Enum yang memakai [[Docs/Modul Data/Enum/Konfigurasi Tegas|Strict On Selected]] memiliki aturan tambahan untuk EnumData. Pastikan [[Docs/Tipe Data/EnumData]] yang ditambahkan oleh [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Add EnumData|Add EnumData Block]] sesuai dengan konfigurasi tersebut.

>**warning** Menghapus EnumData lewat Flow
> [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData|Delete EnumData Block]] menghapus [[Docs/Tipe Data/EnumData]] dari [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]. Pastikan EnumData yang dihapus tidak lagi dipakai komponen lain, karena komponen yang masih memakainya dapat terdampak.

## Jenis Flow Block Data Enum

Phoenix menyediakan tujuh Flow Block Data Enum. Selengkapnya tentang komponennya lihat [[Docs/Modul Data/Enum/Apa itu Enum|Enum]].

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Add EnumData|Add EnumData Block]] | Menambahkan [[Docs/Tipe Data/EnumData]] baru ke sebuah [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData|Delete EnumData Block]] | Menghapus [[Docs/Tipe Data/EnumData]] dari sebuah [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Enum|Enum Block]] | Mengambil nilai atribut [[Docs/Modul Data/Enum/Apa itu Enum|Enum]], yaitu [[^field|Name]] dan [[^field|Description]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]] | Mengambil atribut [[Docs/Tipe Data/EnumData]], yaitu [[^field|Name]], [[^field|Description]], [[^field|Value]], dan [[^field|Selectable]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]] | Mengambil [[Docs/Tipe Data/EnumData]] dari [[Docs/Tipe Data/Enum]] yang ditunjuk dengan mengisi [[^field|Name]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]] | Mengubah atribut [[Docs/Tipe Data/EnumData]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value|EnumData Value Block]] | Menghasilkan [[^field|Value]] dari [[Docs/Tipe Data/EnumData]] sebagai nilai untuk block lain. |

## Memilih Flow Block Data Enum

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menambahkan [[Docs/Tipe Data/EnumData]] baru ke sebuah Enum. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Add EnumData|Add EnumData Block]] |
| Menghapus [[Docs/Tipe Data/EnumData]] yang tidak dipakai lagi. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData|Delete EnumData Block]] |
| Membaca [[^field|Name]] dan [[^field|Description]] sebuah [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Enum|Enum Block]] |
| Membaca atribut [[Docs/Tipe Data/EnumData]] seperti [[^field|Name]], [[^field|Description]], [[^field|Value]], dan [[^field|Selectable]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]] |
| Mengambil [[Docs/Tipe Data/EnumData]] dari sebuah Enum berdasarkan [[^field|Name]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]] |
| Mengubah atribut [[Docs/Tipe Data/EnumData]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]] |
| Memakai [[^field|Value]] [[Docs/Tipe Data/EnumData]] sebagai nilai pada block lain. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value|EnumData Value Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Modul Data/Enum/Mengotomasi|Mengotomasi Enum]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]
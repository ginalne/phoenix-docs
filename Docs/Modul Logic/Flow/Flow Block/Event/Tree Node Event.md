---
status: release
title: Tree Node Event
description: Flow Block Event yang terpicu ketika Node pada Tree ditambahkan, diperbarui, atau dihapus.
pageDecoration:
  icon: zap
  tree:
    priority: 0
---
# Tree Node Event

>**note** Tree Node Event merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Tree Node Event adalah Flow Block Event yang memulai alur setiap kali [[Docs/Tipe Data/Node]] pada komponen [[Docs/Modul Data/Tree/Apa itu Tree|Tree]] ditambahkan, diperbarui, atau dihapus. Block ini menghasilkan tiga output: [[^output|Node]] yang berubah, [[^output|Event]] yang menjelaskan jenis perubahannya, dan [[^output|Old]] yang berisi nilai sebelum perubahan.

Karena Tree menyimpan data berbentuk hierarki, block ini berguna untuk menjaga struktur di sistem lain, seperti struktur organisasi atau kategori bertingkat, tetap sama dengan di Phoenix.

![[Docs/Modul Logic/Flow/Flow Block/Event/tree-node-event.png|Tree Node Event Block pada Blueprint]]
## Kapan Tree Node Event Terpicu

Tree Node Event terpicu ketika Node pada Tree yang terhubung mengalami salah satu dari tiga peristiwa berikut.

| Peristiwa | Nilai [[^output|Event]] |
| --- | --- |
| Node baru ditambahkan | [[^value/string|create]] |
| Node yang sudah ada diperbarui, termasuk dipindahkan ke induk lain | [[^value/string|update]] |
| Node dihapus | [[^value/string|delete]] |

```mermaid
flowchart LR
    A@{ shape: database, label: "**Tree**<br/>Nama Tree" } -.->|&nbsp;Node ditambah, diubah, atau dihapus&nbsp;| B@{ shape: rounded, label: "**Tree Node Event**" }
    B -->|"&nbsp;**[Node]**&nbsp;"| C@{ shape: processes, label: "Block selanjutnya<br/>menerima data" }
    B -->|"&nbsp;**[String]**&nbsp;<br>Event"| C
    B -->|"&nbsp;**[Object]**&nbsp;<br>Old"| C
```

>**note** Hanya perubahan yang memicu Tree Node Event
> Menyimpan Node tanpa ada perubahan tidak memicu Tree Node Event. Aksi create, update, atau delete pada Node yang dilakukan oleh Flow juga tidak memicu Flow kembali.

>**note** Satu perubahan dapat memicu Event di beberapa Tree
> Jika beberapa Tree Merger mengkloning Node yang saling terhubung dan tidak berstatus read only, perubahan pada satu Node dapat menghasilkan Event pada masing-masing Tree. Selengkapnya lihat [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Konfigurasi Merger Mode]].

## Input, Control dan Output

Tree Node Event tidak memiliki input koneksi. Block ini memiliki satu Control berupa tombol dan tiga output di sisi kanan.

| Bagian | Jenis | Tipe Data | Penjelasan |
| --- | --- | --- | --- |
| [[^button/empty|Trigger]] | Control | - | Memicu Tree Node Event secara manual dari Blueprint. |
| [[^output|Node]] | Output | [[Docs/Tipe Data/Node]] | Node yang ditambahkan, diperbarui, atau dihapus. |
| [[^output|Event]] | Output | [[Docs/Tipe Data/String]] | Jenis peristiwa: [[^value/string|create]], [[^value/string|update]], atau [[^value/string|delete]]. |
| [[^output|Old]] | Output | [[Docs/Tipe Data/Object]] | Nilai Node sebelum perubahan. Isinya bergantung pada nilai [[^output|Event]]. |

### Isi Output Berdasarkan Event

| Nilai [[^output|Event]] | Isi [[^output|Node]] | Isi [[^output|Old]] |
| --- | --- | --- |
| [[^value/string|create]] | Node yang baru ditambahkan. | [[^value/empty]], karena Node belum ada sebelumnya. |
| [[^value/string|update]] | Node dengan nilai terbaru. | Hanya field yang diubah (Name, Order, Parent, atau Children), berisi nilai sebelum perubahan. Jika hanya satu field yang diubah, [[^output|Old]] hanya memuat field itu. |
| [[^value/string|delete]] | Node yang dihapus. | Seluruh field Node: Name, Order, Parent, dan Children. |

Aturan [[^output|Event]] dan [[^output|Old]] yang sama juga berlaku pada [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event#Isi Output Berdasarkan Event|Table Row Event]] dan [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event#Isi Output Berdasarkan Event|Enum Data Event]].

## Menggunakan Tree Node Event

1. Klik kanan pada bagian kosong Blueprint ➜ [[^field/add|Add]] ➜ [[^field|Event]] ➜ [[^field|Tree Node Event]].
2. Buka halaman kerja [[Docs/Modul Data/Tree/Apa itu Tree|Tree]], klik [[^button/event|Event]], lalu hubungkan dengan Tree Node Event. Langkah lengkap ada di [[Docs/Modul Data/Tree/Mengotomasi|Mengotomasi Tree]].
3. Hubungkan output [[^output|Node]], [[^output|Event]], atau [[^output|Old]] ke input block berikutnya. Langkah lengkap ada di [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|Menghubungkan Koneksi]].

>**note** Memakai Event dan Function Access
> Menghubungkan Event dari komponen dibatasi Function Access **Modify Event** di Workspace. Selengkapnya lihat [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].

## Contoh Penggunaan

Contoh berikut memakai Tree struktur kategori dengan Node yang memiliki field Name, Order, Parent, dan Children. Setiap contoh menunjukkan kombinasi output yang diterima block berikutnya.

### Integrasi ketika ada Node baru

Gunakan ketika cabang atau kategori baru yang Anda tambahkan perlu langsung dibuat juga di sistem lain.

| Peristiwa | Output [[^output|Node]] | Output [[^output|Event]] | Output [[^output|Old]] |
| --- | --- | --- | --- |
| Node baru ditambahkan di bawah Node induk | Node dengan Name [[^value/string|Perangkat Mobile]] | [[^value/string|create]] | [[^value/empty]] |

Kombinasi yang berguna: [[^output|Node]] untuk mengirim data cabang baru, [[^output|Event]] untuk memastikan hanya [[^value/string|create]] yang diteruskan.

### Otomasi ketika Node diperbarui

Gunakan ketika perubahan pada Node, seperti penggantian nama, perubahan urutan, atau pemindahan ke induk lain, perlu ditindaklanjuti.

| Peristiwa | Output [[^output|Node]] | Output [[^output|Event]] | Output [[^output|Old]] |
| --- | --- | --- | --- |
| Hanya Name diubah dari [[^value/string|Perangkat Mobile]] menjadi [[^value/string|Gawai]] | Node dengan Name [[^value/string|Gawai]] | [[^value/string|update]] | [[^value/object|{ "Name": "Perangkat Mobile" }]] |
| Name dan Order diubah bersamaan | Node dengan Name dan Order terbaru | [[^value/string|update]] | [[^value/object|{ "Name": "Perangkat Mobile", "Order": 2 }]] |
| Node dipindahkan ke induk lain | Node dengan Parent terbaru | [[^value/string|update]] | [[^value/object|{ "Parent": "Elektronik" }]] |

Kombinasi yang berguna: bandingkan [[^output|Old]] dengan [[^output|Node]] untuk mengetahui field mana yang berubah, misalnya hanya meneruskan jika Name berubah.

>**note** Memindahkan Node hanya memicu update pada Node yang dipindahkan
> Anak dari Node yang dipindahkan tidak menghasilkan Event, karena Parent mereka tidak berubah.

### Otomasi ketika Node dihapus

Gunakan ketika Node yang dihapus perlu dicatat atau dihapus juga di sistem lain.

| Peristiwa | Output [[^output|Node]] | Output [[^output|Event]] | Output [[^output|Old]] |
| --- | --- | --- | --- |
| Node tanpa anak dihapus | Node yang dihapus | [[^value/string|delete]] | Seluruh field: Name, Order, Parent, dan Children (kosong) |
| Node yang memiliki anak dihapus | Node yang dihapus | [[^value/string|delete]] | Seluruh field: Name, Order, Parent, dan Children lengkap |

Kombinasi yang berguna: [[^output|Old]] menyimpan seluruh isi Node yang dihapus, sehingga Anda masih dapat mengirim data Node tersebut walaupun sudah tidak ada di Tree.

>**note** Menghapus Node yang memiliki anak hanya menghasilkan satu Event delete
> Event delete hanya untuk Node yang dihapus. Daftar anaknya tersedia lengkap pada field Children di [[^output|Old]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]]
- [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]
- [[Docs/Modul Data/Tree/Mengotomasi|Mengotomasi Tree]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]

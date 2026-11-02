---
    status: release
    title: Tree Node Event
    description: Flow Block Event yang terpicu ketika Node pada Tree ditambahkan, diperbarui, atau dihapus.
    pageDecoration:
      tree:
        priority: 0
---
# Tree Node Event

>**note** Tree Node Event merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Tree Node Event adalah Flow Block Event yang memulai alur setiap kali [[Docs/Tipe Data/Node]] pada komponen [[Docs/Modul Data/Tree/Apa itu Tree|Tree]] ditambahkan, diperbarui, atau dihapus. Block ini menghasilkan tiga output: `Node` yang berubah, `Event` yang menjelaskan jenis perubahannya, dan `Old` yang berisi nilai sebelum perubahan.

Karena Tree menyimpan data berbentuk hierarki, block ini berguna untuk menjaga struktur di sistem lain, seperti struktur organisasi atau kategori bertingkat, tetap sama dengan di Phoenix.

![[Docs/Modul Logic/Flow/Flow Block/Event/tree-node-event.png|Tree Node Event Block pada Blueprint]]

<!--
  * [TODO] Letakkan potongan gambar Tree Node Event dari screenshot (file `tree-node-event.png`). Anotasi yang disarankan: nomor 1 pada judul, nomor 2 pada tombol Trigger, nomor 3 pada output Node, Event, dan Old.
-->

## Kapan Tree Node Event Terpicu

Tree Node Event terpicu ketika Node pada Tree yang terhubung mengalami salah satu dari tiga peristiwa berikut.

| Peristiwa | Nilai `Event` |
| --- | --- |
| Node baru ditambahkan | `create` |
| Node yang sudah ada diperbarui | `update` |
| Node dihapus | `delete` |

```mermaid
flowchart LR
    A@{ shape: database, label: "**Tree**<br/>Nama Tree" } -.->|&nbsp;Node ditambah, diubah, atau dihapus&nbsp;| B@{ shape: rounded, label: "**Tree Node Event**" }
    B -->|"&nbsp;**[Node]**&nbsp;"| C@{ shape: processes, label: "Block selanjutnya<br/>menerima data" }
    B -->|"&nbsp;**[String]**&nbsp;<br>Event"| C
    B -->|"&nbsp;**[Object]**&nbsp;<br>Old"| C
```

## Input, Control dan Output

Tree Node Event tidak memiliki input koneksi. Block ini memiliki satu control dan tiga output.

| Bagian | Jenis | Tipe Data | Penjelasan |
| --- | --- | --- | --- |
| [[^button/empty\|Trigger]] | Control | - | Memicu Tree Node Event secara manual dari Blueprint. |
| [[^output|Node]] | Output | [[Docs/Tipe Data/Node]] | Node yang ditambahkan, diperbarui, atau dihapus. |
| [[^output|Event]] | Output | [[Docs/Tipe Data/String]] | Jenis peristiwa: `create`, `update`, atau `delete`. |
| [[^output|Old]] | Output | [[Docs/Tipe Data/Object]] | Nilai Node sebelum perubahan. Isinya bergantung pada nilai `Event`. |

### Isi Output Berdasarkan Event

| Nilai `Event` | Isi `Node` | Isi `Old` |
| --- | --- | --- |
| [[^value/string|create]] | Node yang baru ditambahkan. | `Empty`, karena Node belum ada sebelumnya. |
| [[^value/string|update]] | Node dengan nilai terbaru. | Hanya field yang diubah (Name, Order, atau Children), berisi nilai sebelum perubahan. Jika tidak ada perubahan, `Empty`. |
| [[^value/string|delete]] | Node yang dihapus. | Seluruh field Node yang dihapus. |

Aturan `Event` dan `Old` yang sama juga berlaku pada [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan#Output Event dan Old|Table Row Event dan Enum Data Event]].

## Menggunakan Tree Node Event

1. Klik kanan pada bagian kosong Blueprint ➜ [[^field/add|Add]] ➜ [[^field|Event]] ➜ [[^field|Tree Node Event]].
2. Buka halaman kerja [[Docs/Modul Data/Tree/Apa itu Tree|Tree]], klik [[^button/event|Event]], lalu hubungkan dengan Tree Node Event. Langkah lengkap ada di [[Docs/Modul Data/Tree/Mengotomasi|Mengotomasi Tree]].
3. Hubungkan output `Node`, `Event`, atau `Old` ke input block berikutnya. Langkah lengkap ada di [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|Menghubungkan Koneksi]].

>**note** Memakai Event dan Function Access
> Menghubungkan Event dari komponen dibatasi Function Access **Modify Event** di Workspace. Selengkapnya lihat [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].

## Contoh Penggunaan

Contoh berikut memakai Tree struktur kategori dengan Node yang memiliki field Name, Order, dan Children. Setiap contoh menunjukkan kombinasi output yang diterima block berikutnya.

### Integrasi ketika ada Node baru

Gunakan ketika cabang atau kategori baru yang Anda tambahkan perlu langsung dibuat juga di sistem lain.

| Peristiwa | Output `Node` | Output `Event` | Output `Old` |
| --- | --- | --- | --- |
| Node baru ditambahkan di bawah Node induk | Node dengan Name `Perangkat Mobile` | `[[^value/string|create]]` | `[[^value/empty]]` |

Kombinasi yang berguna: `Node` untuk mengirim data cabang baru, `Event` untuk memastikan hanya `create` yang diteruskan.

### Otomasi ketika Node diperbarui

Gunakan ketika perubahan pada Node, seperti penggantian nama atau perubahan urutan, perlu ditindaklanjuti.

| Peristiwa | Output `Node` | Output `Event` | Output `Old` |
| --- | --- | --- | --- |
| Hanya Name diubah dari `Perangkat Mobile` menjadi `Gawai` | Node dengan Name `Gawai` | `update` | Hanya Name: `Perangkat Mobile` |
| Name dan Order diubah bersamaan | Node dengan Name dan Order terbaru | `update` | Name dan Order dengan nilai sebelumnya |
| Disimpan tanpa ada perubahan | Node yang sama | `update` | `Empty` |

Kombinasi yang berguna: bandingkan `Old` dengan `Node` untuk mengetahui field mana yang berubah, misalnya hanya meneruskan jika Name berubah.

### Otomasi ketika Node dihapus

Gunakan ketika Node yang dihapus perlu dicatat atau dihapus juga di sistem lain.

| Peristiwa | Output `Node` | Output `Event` | Output `Old` |
| --- | --- | --- | --- |
| Node dihapus | Node yang dihapus | `delete` | Seluruh field: Name, Order, dan Children |

Kombinasi yang berguna: `Old` menyimpan seluruh isi Node yang dihapus, sehingga Anda masih dapat mengirim data Node tersebut walaupun sudah tidak ada di Tree.

<!--
  * [DONE] Nama Tree dan Node pada contoh (Perangkat Mobile, Gawai) adalah penamaan generik buatan Claude. Sesuaikan bila perlu.
  * [TODO] Konfirmasi field Node yang dapat muncul di `Old`. Draf ini mengasumsikan Name, Order, dan Children berdasarkan atribut External Read Only pada Tree.
    Jawaban: Betul
  * [TODO] Konfirmasi apakah memindahkan Node ke induk lain dihitung sebagai `update`, dan apakah menghapus Node yang memiliki Children menghasilkan satu atau beberapa peristiwa `delete`.
    Jawaban: 
  * [TODO] Konfirmasi apakah Node hasil clone pada Tree Merger juga memicu Tree Node Event.
  * [TODO] Konfirmasi path `Docs/Modul Data/Tree/Event` dan nama tombol Event pada langkah 2.
-->

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]]
- [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]
- [[Docs/Modul Data/Tree/Event|Event Tree]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]

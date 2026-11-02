---
    status: release
    title: Enum Data Event
    description: Flow Block Event yang terpicu ketika EnumData pada Enum ditambahkan, diperbarui, atau dihapus.
    pageDecoration:
      tree:
        priority: 3
---
# Enum Data Event

>**note** Enum Data Event merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Enum Data Event adalah Flow Block Event yang memulai alur setiap kali [[Docs/Tipe Data/EnumData]] pada komponen [[Docs/Modul Data/Enum/Apa itu Enum|Enum]] ditambahkan, diperbarui, atau dihapus. Block ini menghasilkan tiga output: `EnumData` yang berubah, `Event` yang menjelaskan jenis perubahannya, dan `Old` yang berisi nilai sebelum perubahan.

Karena Enum menyimpan data master seperti pilihan, menu, dan kategori, block ini berguna untuk menjaga sistem lain tetap selaras ketika daftar pilihan berubah.

![[Docs/Modul Logic/Flow/Flow Block/Event/enum-data-event.png|Enum Data Event Block pada Blueprint]]

<!--
  * [DONE] Letakkan potongan gambar Enum Data Event dari screenshot (file `enum-data-event.png`). Anotasi yang disarankan: nomor 1 pada judul, nomor 2 pada tombol Trigger, nomor 3 pada output EnumData, Event, dan Old.
  * [TODO] Screenshot yang diberikan hanya menampilkan output EnumData pada block ini. Draf mengikuti informasi penulis bahwa block ini juga memiliki output Event dan Old. Perbarui gambar bila sudah tersedia.
    Jawaban: Oke
-->

## Kapan Enum Data Event Terpicu

Enum Data Event terpicu ketika EnumData pada Enum yang terhubung mengalami salah satu dari tiga peristiwa berikut.

| Peristiwa | Nilai `Event` |
| --- | --- |
| EnumData baru ditambahkan | `create` |
| EnumData yang sudah ada diperbarui | `update` |
| EnumData dihapus | `delete` |

```mermaid
flowchart LR
    A@{ shape: database, label: "**Enum**<br/>Nama Enum" } -.->|&nbsp;EnumData ditambah, diubah, atau dihapus&nbsp;| B@{ shape: rounded, label: "**Enum Data Event**" }
    B -->|"&nbsp;**[EnumData]**&nbsp;"| C@{ shape: processes, label: "Block selanjutnya<br/>menerima data" }
    B -->|"&nbsp;**[String]**&nbsp;<br>Event"| C
    B -->|"&nbsp;**[Object]**&nbsp;<br>Old"| C
```

## Input, Control dan Output

Enum Data Event tidak memiliki input koneksi. Block ini memiliki tiga output di sisi kanan.

| Bagian | Jenis | Tipe Data | Penjelasan |
| --- | --- | --- | --- |
| [[^button/empty\|Trigger]] | Control | - | Memicu Enum Data Event secara manual dari Blueprint. |
| `EnumData` | Output | [[Docs/Tipe Data/EnumData]] | EnumData yang ditambahkan, diperbarui, atau dihapus. |
| `Event` | Output | [[Docs/Tipe Data/String]] | Jenis peristiwa: `create`, `update`, atau `delete`. |
| `Old` | Output | [[Docs/Tipe Data/Object]] | Nilai EnumData sebelum perubahan. Isinya bergantung pada nilai `Event`. |

### Isi Output Berdasarkan Event

| Nilai `Event` | Isi `EnumData` | Isi `Old` |
| --- | --- | --- |
| `create` | EnumData yang baru ditambahkan. | `Empty`, karena EnumData belum ada sebelumnya. |
| `update` | EnumData dengan nilai terbaru. | Hanya field yang diubah (Name, Description, Value, atau Selectable), berisi nilai sebelum perubahan. Jika tidak ada perubahan, `Empty`. |
| `delete` | EnumData yang dihapus. | Seluruh field: Name, Description, Value, dan Selectable. |

Aturan `Event` dan `Old` yang sama juga berlaku pada [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan#Output Event dan Old|Table Row Event dan Tree Node Event]].

## Menggunakan Enum Data Event

1. Klik kanan pada bagian kosong Blueprint ➜ [[^field/add|Add]] ➜ [[^field|Event]] ➜ [[^field|Enum Data Event]].
2. Buka halaman kerja [[Docs/Modul Data/Enum/Apa itu Enum|Enum]], klik [[^button/event|Event]], lalu hubungkan dengan Enum Data Event. Langkah lengkap ada di [[Docs/Modul Data/Enum/Event|Event Enum]] dan [[Docs/Event/Menghubungkan Event|Menghubungkan Event]].
3. Hubungkan output `EnumData`, `Event`, atau `Old` ke input block berikutnya. Langkah lengkap ada di [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|Menghubungkan Koneksi]].

>**note** Memakai Event dan Function Access
> Menghubungkan Event dari komponen dibatasi Function Access **Modify Event** di Workspace. Selengkapnya lihat [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].

## Contoh Penggunaan

Contoh berikut memakai Enum kategori dengan EnumData yang memiliki field Name, Description, Value, dan Selectable. Setiap contoh menunjukkan kombinasi output yang diterima block berikutnya.

### Integrasi ketika ada EnumData baru

Gunakan ketika pilihan baru yang Anda tambahkan perlu dikirim ke sistem lain agar daftar pilihannya sama.

| Peristiwa | Output `EnumData` | Output `Event` | Output `Old` |
| --- | --- | --- | --- |
| Pilihan baru ditambahkan | EnumData dengan Name `Elektronik`, Selectable `Yes` | `create` | `Empty` |

Kombinasi yang berguna: `EnumData` untuk mengirim pilihan baru beserta Value-nya, `Event` untuk memastikan hanya `create` yang diteruskan.

### Otomasi ketika EnumData diperbarui

Gunakan ketika perubahan pilihan perlu ditindaklanjuti, misalnya pilihan yang tidak lagi dapat dipilih.

| Peristiwa | Output `EnumData` | Output `Event` | Output `Old` |
| --- | --- | --- | --- |
| Hanya Selectable diubah dari `Yes` menjadi `No` | EnumData dengan Selectable `No` | `update` | Hanya Selectable: `Yes` |
| Name dan Description diubah bersamaan | EnumData dengan Name dan Description terbaru | `update` | Name dan Description dengan nilai sebelumnya |
| Disimpan tanpa ada perubahan | EnumData yang sama | `update` | `Empty` |

Kombinasi yang berguna: bandingkan `Old` dengan `EnumData` untuk mengetahui field mana yang berubah, misalnya hanya meneruskan jika Selectable berubah.

### Otomasi ketika EnumData dihapus

Gunakan ketika pilihan yang dihapus perlu dicatat atau dihapus juga di sistem lain.

| Peristiwa | Output `EnumData` | Output `Event` | Output `Old` |
| --- | --- | --- | --- |
| Pilihan dihapus | EnumData yang dihapus | `delete` | Seluruh field: Name, Description, Value, dan Selectable |

Kombinasi yang berguna: `Old` menyimpan seluruh isi EnumData yang dihapus, sehingga Anda masih dapat mengirim Name dan Value pilihan tersebut.

<!--
  * [TODO] Nama Enum dan nilai pada contoh (kategori, Elektronik) adalah penamaan generik buatan Claude. Sesuaikan bila perlu.
  * [TODO] Konfirmasi field EnumData yang dapat muncul di `Old` (Name, Description, Value, Selectable) dan apakah perubahan Selectable juga memicu `update`.
  * [TODO] Konfirmasi apakah `EnumData` pada `delete` berisi EnumData terakhir sebelum dihapus.
  * [TODO] Konfirmasi path `Docs/Modul Data/Enum/Event` dan nama tombol Event pada langkah 2.
-->

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Modul Data/Enum/Event|Event Enum]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]

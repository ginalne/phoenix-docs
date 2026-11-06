---
      status: release
      title: Table Row Event
      description: Flow Block Event yang terpicu ketika Row pada Table ditambahkan, diperbarui, atau dihapus.
      pageDecoration:
        icon: zap
        tree:
          priority: 0
---
# Table Row Event

>**note** Table Row Event merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Table Row Event adalah Flow Block Event yang memulai alur setiap kali [[Docs/Tipe Data/Row]] pada komponen [[Docs/Modul Data/Table/Apa itu Table|Table]] ditambahkan, diperbarui, atau dihapus. Block ini menghasilkan tiga output: [[^output|Row]] yang berubah, [[^output|Event]] yang menjelaskan jenis perubahannya, dan [[^output|Old]] yang berisi nilai sebelum perubahan.

Dengan satu block ini, Anda dapat mengintegrasikan Row baru ke sistem lain, mengotomasi tindakan saat Row diperbarui, dan menindaklanjuti Row yang dihapus.

![[Docs/Modul Logic/Flow/Flow Block/Event/table-row-event.png|Table Row Event Block pada Blueprint]]
## Kapan Table Row Event Terpicu

Table Row Event terpicu ketika Row pada Table yang terhubung mengalami salah satu dari tiga peristiwa berikut.

| Peristiwa | Nilai [[^output|Event]] |
| --- | --- |
| Row baru ditambahkan | [[^value/string|create]] |
| Row yang sudah ada diperbarui | [[^value/string|update]] |
| Row dihapus | [[^value/string|delete]] |

```mermaid
flowchart LR
    A@{ shape: database, label: "**Table**<br/>Nama Table" } -.->|&nbsp;Row ditambah, diubah, atau dihapus&nbsp;| B@{ shape: rounded, label: "**Table Row Event**" }
    B -->|"&nbsp;**[Row]**&nbsp;"| C@{ shape: processes, label: "Block selanjutnya<br/>menerima data" }
    B -->|"&nbsp;**[String]**&nbsp;<br>Event"| C
    B -->|"&nbsp;**[Object]**&nbsp;<br>Old"| C
```

>**note** Hanya perubahan yang memicu Table Row Event
> Menyimpan Row tanpa ada perubahan tidak memicu Table Row Event. Aksi create, update, atau delete pada Row yang dilakukan oleh Flow juga tidak memicu Flow kembali, sedangkan Import atau Upload tetap memicu [[^value/string|create]].

## Control dan Output

Table Row Event tidak memiliki input koneksi. Block ini memiliki satu Control berupa tombol dan tiga output di sisi kanan.

| Bagian | Jenis | Tipe Data | Penjelasan |
| --- | --- | --- | --- |
| [[^button/empty|Trigger]] | Control | - | Memicu Table Row Event secara manual dari Blueprint. |
| [[^output|Row]] | Output | [[Docs/Tipe Data/Row]] | Row yang ditambahkan, diperbarui, atau dihapus. |
| [[^output|Event]] | Output | [[Docs/Tipe Data/String]] | Jenis peristiwa: [[^value/string|create]], [[^value/string|update]], atau [[^value/string|delete]]. |
| [[^output|Old]] | Output | [[Docs/Tipe Data/Object]] | Nilai Row sebelum perubahan. Isinya bergantung pada nilai [[^output|Event]]. |

### Isi Output Berdasarkan Event

| Nilai [[^output|Event]] | Isi [[^output|Row]] | Isi [[^output|Old]] |
| --- | --- | --- |
| [[^value/string|create]] | Row yang baru ditambahkan. | [[^value/empty]], karena Row belum ada sebelumnya. |
| [[^value/string|update]] | Row dengan nilai terbaru. | Hanya [[Docs/Tipe Data/Column]] yang diubah, berisi nilai sebelum perubahan. Jika hanya satu Column yang diubah, [[^output|Old]] hanya memuat Column itu. |
| [[^value/string|delete]] | Row yang dihapus. | Seluruh Column dari Row yang dihapus. |

Aturan [[^output|Event]] dan [[^output|Old]] yang sama juga berlaku pada [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event#Isi Output Berdasarkan Event|Enum Data Event]] dan [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event#Isi Output Berdasarkan Event|Tree Node Event]].

## Menggunakan Table Row Event

1. Klik kanan pada bagian kosong Blueprint ➜ [[^field/add|Add]] ➜ [[^field|Event]] ➜ [[^field|Table Row Event]].
2. Buka halaman kerja [[Docs/Modul Data/Table/Apa itu Table|Table]], klik [[^button/event|Event]], lalu hubungkan dengan Table Row Event. Langkah lengkap ada di [[Docs/Modul Data/Table/Mengotomasi|Mengotomasi Table]] dan [[Docs/Event/Menghubungkan Event|Menghubungkan Event]].
3. Hubungkan output [[^output|Row]], [[^output|Event]], atau [[^output|Old]] ke input block berikutnya. Langkah lengkap ada di [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|Menghubungkan Koneksi]].

>**note** Memakai Event dan Function Access
> Menghubungkan Event dari komponen dibatasi Function Access **Modify Event** di Workspace. Selengkapnya lihat [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].

## Contoh Penggunaan

Contoh berikut memakai Table pesanan dengan Column Nomor Pesanan, Status, dan Total. Setiap contoh menunjukkan kombinasi output yang diterima block berikutnya, sehingga Anda dapat memilih output mana yang Anda butuhkan.

### Integrasi ketika ada Row baru

Gunakan ketika setiap pesanan baru perlu langsung dikirim ke sistem lain, misalnya sistem gudang atau pemberitahuan.

| Peristiwa | Output [[^output|Row]] | Output [[^output|Event]] | Output [[^output|Old]] |
| --- | --- | --- | --- |
| Pesanan baru ditambahkan lewat halaman kerja Table | Row dengan Nomor Pesanan [[^value/string|SO-0001]], Status [[^value/enumdata|Menunggu]], Total [[^value/number|150000]] | [[^value/string|create]] | [[^value/empty]] |
| Pesanan baru masuk lewat Import atau Upload | Row baru dengan bentuk yang sama | [[^value/string|create]] | [[^value/empty]] |

Kombinasi yang berguna: [[^output|Row]] untuk mengirim seluruh isi pesanan, [[^output|Event]] untuk memastikan hanya [[^value/string|create]] yang diteruskan.

### Otomasi ketika Row diperbarui

Gunakan ketika perubahan pada pesanan, misalnya perubahan [[^field/column|Status]], perlu ditindaklanjuti, seperti memberi tahu pelanggan.

| Peristiwa | Output [[^output|Row]] | Output [[^output|Event]] | Output [[^output|Old]] |
| --- | --- | --- | --- |
| Hanya [[^field/column|Status]] diubah dari [[^value/enumdata|Menunggu]] menjadi [[^value/enumdata|Diproses]] | Row dengan Status [[^value/enumdata|Diproses]] | [[^value/string|update]] | [[^value/object|{ "Status": "Menunggu" }]] |
| [[^field/column|Status]] dan [[^field/column|Total]] diubah bersamaan, Total dari [[^value/number|150000]] menjadi [[^value/number|175000]] | Row dengan Status dan Total terbaru | [[^value/string|update]] | [[^value/object|{ "Status": "Menunggu", "Total": 150000 }]] |

Kombinasi yang berguna: bandingkan [[^output|Old]] dengan [[^output|Row]] untuk mengetahui apa yang berubah dan nilai sebelumnya, misalnya hanya meneruskan jika Status berpindah ke nilai tertentu.

### Otomasi ketika Row dihapus

Gunakan ketika penghapusan pesanan perlu dicatat atau dibatalkan di sistem lain.

| Peristiwa | Output [[^output|Row]] | Output [[^output|Event]] | Output [[^output|Old]] |
| --- | --- | --- | --- |
| Pesanan dihapus lewat kolom Action | Row yang dihapus, dengan nilai terakhir sebelum dihapus | [[^value/string|delete]] | [[^value/object|{ "Nomor Pesanan": "SO-0001", "Status": "Diproses", "Total": 175000 }]] |

Kombinasi yang berguna: [[^output|Old]] menyimpan seluruh isi Row yang dihapus, sehingga Anda masih dapat mengirim data pesanan yang sudah tidak ada di Table.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]]
- [[Docs/Modul Data/Table/Apa itu Table|Table]]
- [[Docs/Modul Data/Table/Mengotomasi|Mengotomasi Table]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]

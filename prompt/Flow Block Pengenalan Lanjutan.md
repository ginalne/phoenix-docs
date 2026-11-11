---
  pageDecoration:
    tree:
      priority: -15
  tags:
    meta
    prompt
---
2026-11-07 00:00

/phoenix-docs-silverbullet /phoenix-docs-knowledge 

Tolong saya membuat 6 halaman pengenalan untuk kategori flow block. Berikut saya buat daftar halaman dengan masing-masing jenis flow block nya dan penjelasan singkatnya. Berbeda dengan kategori Event yang flow block nya memiliki kemiripan control dan output, kategori ini memiliki flow block yang unik-unik sesuai fungsi nya.

1. [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Pengenalan|I/O]] (Branch, Passer)
    Kategori ini berfungsi untuk membantu pengelolaan aliran data dalam flow.
2. [[Docs/Modul Logic/Flow/Flow Block/Query/Pengenalan|Query]] (Condition, Execute)
    Kategori ini berfungsi untuk membangun dan menjalankan Query menggunakan flow.
3. [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Operator]] (Number : Increment. String : Concatenate, Implode, Pad Left, Pad Right. Table : TableRow Parse. Object : Assign, Merge, Parse, Stringify. Boolean : If. Tree : Node Parse)
   Kategori ini berfungsi untuk pengolahan data dalam flow, seperti aritmatika, pengolahan teks, konversi maupun translasi data. Masing-masing blok dikelompokan berdasarkan tipe data input utamanya.
4. [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan|Modular]] (API: HTTP Request, AI: OpenAI 4)
    Kategori ini berfungsi untuk mengeksekusi proses yang kompleks, seperti memanggil permintaan HTTP ataupun menghubungi provider jasa tertentu.
5. [[Docs/Modul Logic/Flow/Flow Block/Chrono/Pengenalan|Chrono]] (Delay)
   Kategori ini befungsi untuk mengelola aliran berdasarkan waktu, sehingga proses aliran dapat memiliki waktu yang lebih lama.
6. [[Docs/Modul Logic/Flow/Flow Block/Error/Pengenalan|Error]] (Error Message)
   Kategori ini berfungsi untuk mengelola atau menangani error, atau sekadar mengatur bagaimana error ditampilkan.

Mungkin bisa buat halaman-halaman ini untuk pengenalan menuju ke masing-masing flow block yang kategori miliki. Struktur halaman mungkin bisa mengikuti struktur pengenalan event (jika relevan) yang juga sudah saya lampirkan. Perlu diingat kalau penjelasan singkat permasing-masing kategori ini bukan susunan kata yang absolut, mohon untuk dicerna dengan melihat nama flow block yang sudah ada agar penjelasan dapat lebih holistik dan mewadahi flow block didalamnya.

---
    status: release
    title: Flow Block Event
    description: Pengenalan kategori Flow Block Event, block yang menjadi titik awal alur di Blueprint Flow.
    pageDecoration:
      tree:
        priority: 6
    tags: flowblock-category
---
# Flow Block Event

>**note** Flow Block Event merupakan salah satu kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Event adalah kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang menjadi **titik awal** sebuah alur di Blueprint. Setiap alur di [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] dimulai dari satu atau beberapa block Event, lalu hasilnya diteruskan ke block kategori lain untuk diolah, disimpan, atau dikirim ke sistem lain.

Berbeda dengan kategori lain yang bekerja setelah menerima data dari block sebelumnya, block Event menunggu peristiwa dari luar Flow, misalnya perubahan [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]], jadwal dari [[Docs/Modul Interface/Timeline/Apa itu Timeline|Timeline]], atau tombol yang ditekan. Ketika peristiwa itu terjadi, block Event menghasilkan output yang menjadi bahan awal bagi seluruh alur di sebelah kanannya.

![[Docs/Modul Logic/Flow/Flow Block/Event/event-block-flow.png|Lima Flow Block Event pada Blueprint: Pulser, Enum Data Event, Table Row Event, Tree Node Event, dan Variable Event]]
Block Event tidak memiliki input koneksi, hanya output di sisi kanan. Karena itu block Event tidak dapat dihubungkan dari block lain dan tidak terkena syarat eksekusi yang berlaku pada block non-Event. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

>**note** Perubahan data oleh Flow tidak memicu Flow kembali
> Aksi create, update, atau delete pada data apa pun yang dilakukan oleh Flow tidak memicu Flow kembali. Perubahan dari sumber lain, seperti pengisian manual, Import, atau Upload, tetap memicu Event.

## Jenis Flow Block Event

Phoenix menyediakan lima Flow Block Event. Empat di antaranya terhubung dengan komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]], [[Docs/Modul Data/Enum/Apa itu Enum|Enum]], [[Docs/Modul Data/Table/Apa itu Table|Table]], dan [[Docs/Modul Data/Tree/Apa itu Tree|Tree]], sedangkan Pulser dipicu secara langsung.

| Block | Terpicu ketika | Output |
| --- | --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser Event Block]] | Tombol [[^button/empty|Trigger]] ditekan, jadwal [[Docs/Modul Interface/Timeline/Timeline Event/Pengenalan|Timeline Event]] tiba, atau [[Docs/Modul Interface/Canvas/Widget/Basic/Button|Widget Button]] pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]] ditekan. | [[^output|Result]] |
| [[Docs/Modul Logic/Flow/Flow Block/Event/Variable Event|Variable Event Block]] | Value pada Variable Data berubah atau Variable Data dihapus. | [[^output|Variable]], [[^output|Event]], [[^output|Old]] |
| [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event|Enum Data Event Block]] | [[Docs/Tipe Data/EnumData]] pada [[Docs/Modul Data/Enum/Apa itu Enum|Enum]] ditambahkan, diperbarui, atau dihapus. | [[^output|EnumData]], [[^output|Event]], [[^output|Old]] |
| [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event|Table Row Event Block]] | [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]] ditambahkan, diperbarui, atau dihapus. | [[^output|Row]], [[^output|Event]], [[^output|Old]] |
| [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]] | [[Docs/Tipe Data/Node]] pada [[Docs/Modul Data/Tree/Apa itu Tree|Tree]] ditambahkan, diperbarui, atau dihapus. | [[^output|Node]], [[^output|Event]], [[^output|Old]] |

## Memilih Flow Block Event

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menjalankan alur secara manual, terjadwal, atau lewat tombol di Canvas. | [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser Event Block]] |
| Bereaksi ketika Value [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] berubah atau Variable Data dihapus. | [[Docs/Modul Logic/Flow/Flow Block/Event/Variable Event|Variable Event Block]] |
| Bereaksi ketika pilihan pada [[Docs/Modul Data/Enum/Apa itu Enum|Enum]] berubah. | [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event|Enum Data Event Block]] |
| Bereaksi ketika [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]] bertambah, berubah, atau terhapus. | [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event|Table Row Event Block]] |
| Bereaksi ketika [[Docs/Tipe Data/Node]] pada [[Docs/Modul Data/Tree/Apa itu Tree|Tree]] bertambah, berubah, atau terhapus. | [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Dasar/Apa itu Event|Event]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]

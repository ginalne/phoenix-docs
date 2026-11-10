---
    status: release
    title: Flow Block Chrono
    description: Pengenalan kategori Flow Block Chrono, block yang mengelola aliran berdasarkan waktu di Blueprint Flow.
    pageDecoration:
      tree:
        priority: 15
    tags: flowblock-category
---
# Flow Block Chrono

>**note** Flow Block Chrono merupakan salah satu kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Chrono adalah kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang digunakan untuk **mengelola aliran berdasarkan waktu**, sehingga proses dalam alur dapat berjalan dalam rentang waktu yang lebih lama. Dengan block Chrono, sebuah alur tidak harus selesai seketika, tetapi dapat menunggu terlebih dahulu sebelum melanjutkan ke block berikutnya.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur, block Chrono bekerja setelah menerima data dari block sebelumnya, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Block Chrono juga berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser Event Block]] yang memulai alur pada waktu tertentu lewat [[Docs/Modul Interface/Timeline/Timeline Event/Pengenalan|Timeline Event]]: Pulser menentukan kapan alur dimulai, sedangkan block Chrono mengatur jeda di tengah alur yang sedang berjalan.

![[Docs/Modul Logic/Flow/Flow Block/Chrono/chrono-block-flow.png|Satu Flow Block Chrono pada Blueprint: Delay]]

## Jenis Flow Block Chrono

Phoenix menyediakan satu Flow Block Chrono.

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Chrono/Delay|Delay Chrono Block]] | Menunda aliran dengan waktu yang dapat ditentukan. Selama penundaan, block berstatus [[^flowstate|Waiting]]. |

## Memilih Flow Block Chrono

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menunda sebagian alur selama waktu tertentu setelah alur berjalan. | [[Docs/Modul Logic/Flow/Flow Block/Chrono/Delay|Delay Chrono Block]] |
| Memulai alur pada jadwal tertentu. | [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser Event Block]] dengan [[Docs/Modul Interface/Timeline/Timeline Event/Pengenalan|Timeline Event]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]

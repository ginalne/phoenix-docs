---
    status: release
    title: Apa itu Flow?
    description: 
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="0 -960 960 960">
    <path d="M357-291q-46 51-102.5 50.5T156-273q-42-32-57-85.5T120-470l64-103q-19-20-29.5-44.99Q144-642.98 144-672q0-60 42-102t102-42q60 0 102 42t42 102q0 60-42 102t-102 42q-10.67 0-21.33-2-10.67-2-21.67-5l-64 103q-19 30-10.5 57.5T201-330q22 17 50.5 17t52.5-26l299-330q46-51 102-51t98 32q42 32 57.5 85.5T840-490l-64 103q19 20 29.5 44.99Q816-317.02 816-288q0 60-42 102t-102 42q-60 0-102-42t-42-102q0-60 42-102t102-42q11.08 0 21.54 2 10.46 2 21.46 5l64-103q19-30 10.5-58T759-631q-22-17-51-16.5T656-621L357-291Zm-18-330.21q21-21.21 21-51T338.79-723q-21.21-21-51-21T237-722.79q-21 21.21-21 51T237.21-621q21.21 21 51 21T339-621.21Zm384 384q21-21.21 21-51T722.79-339q-21.21-21-51-21T621-338.79q-21 21.21-21 51T621.21-237q21.21 21 51 21T723-237.21ZM288-672Zm384 384Z"/>
  </svg>'
      tree:
        priority:  4
---

# Apa itu Flow?

>**note** _Flow_ merupakan salah satu komponen dalam modul [[Docs/Modul Logic/Pengenalan|Logic]] di Phoenix.

_Flow_ adalah komponen yang dapat digunakan untuk mengatur logika dan proses pengelolaan data dengan pendekatan alur komposit, yaitu menyusun logika dengan menghubungkan blok demi blok. Setiap blok yang Anda bangun dapat dihubungkan dan dimonitor, sehingga setiap [[Docs/Event/Apa itu Event|Event]] yang terikat dapat menghasilkan keluaran dan otomasi yang tepat.

## Mengapa Menggunakan Flow?

* **Logika tersusun secara visual.** Anda merangkai Flow Block pada blueprint sehingga alur proses mudah dibaca dan dipahami.
* **Otomasi berbasis Event.** Flow Block Event memicu proses, lalu hasilnya mengalir ke block berikutnya melalui koneksi.
* **Mudah diuji.** Anda dapat menjalankan proses secara manual dari antarmuka Flow tanpa menunggu pemicu yang sebenarnya.
* **Proses dapat dipantau.** Setiap proses yang berjalan tercatat dan dapat dilihat melalui [[Docs/Modul Logic/Flow/Flow Activity|Activity]].
* **Terhubung dengan data Phoenix.** Flow Block tersedia untuk terhubung dengan [[Docs/Modul Data/Variable/Apa itu Variable|Variable]], [[Docs/Modul Data/Enum/Apa itu Enum|Enum]], [[Docs/Modul Data/Table/Apa itu Table|Table]], dan [[Docs/Modul Data/Tree/Apa itu Tree|Tree]].
* **Terhubung dengan sistem lain.** Flow Block [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan|Modular]] seperti HTTP Request dan OpenAI 4 memungkinkan data Phoenix dikirim ke aplikasi lain atau diolah oleh AI.

## Konsep Utama

| Istilah | Penjelasan |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] | Unit terkecil penyusun Flow. Setiap block memiliki fungsi tertentu dan dapat dihubungkan dengan block lain. |
| [[#Antarmuka Flow|Blueprint]] | Area kerja tempat Anda menambahkan, menata, dan menghubungkan Flow Block. Posisi kursor (x, y) dan *scale* tampil di sudut kiri bawah halaman. |
| [[Docs/Modul Logic/Flow/Flow Block/Pengenalan#Antarmuka Flow Block|Input dan Output]] | Titik penghubung pada Flow Block. Output berada di sisi kanan block, input berada di sisi kiri block. |
| [[Docs/Modul Logic/Flow/Flow Block/Pengenalan#Antarmuka Flow Block|Koneksi]] | Garis penghubung dari output sebuah block ke input block lain. Koneksi menentukan arah aliran proses. |
| [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] | Flow Block pemicu proses, misalnya Pulser dan Variable Event. Block ini juga memiliki tombol untuk eksekusi manual. Selengkapnya lihat [[Docs/Event/Apa itu Event|Event]]. |
| [[Docs/Modul Logic/Flow/Flow Activity]] | Tampilan pemantauan proses yang sedang atau sudah berjalan di dalam Flow. |

## Cara Kerja

Penjelasan cara kerja Flow lihat selengkap nya di [[Docs/Modul Interface/Flow/Cara Kerja|Cara Kerja Flow]].

## Mengelola Kanban

Berikut adalah halaman yang menjelaskan cara untuk mengelola Kanban:
1. [[Docs/Modul Interface/Kanban/Membuat Baru]] Kanban dalam halaman kerja.
2. [[Docs/Modul Interface/Kanban/Mengubah]] Atribut Kanban seperti [[^field|Name]], [[^field|Description]], atau [[^field|Table - Column]].
3. [[Docs/Modul Interface/Kanban/Menghapus]] Kanban.
4. [[Docs/Modul Interface/Kanban/Mengatur Templat]] Kartu dalam Kanban.

## Membangun Logika Flow

Membangun proses logika Flow dilakukan dengan cara pengelolaan Flow Block dengan aspek sebagai berikut:

* [[Docs/Modul Logic/Flow/Flow Block/Pengenalan#Menambahkan Flow Block|Menambahkan Flow Block]]
* [[Docs/Modul Logic/Flow/Flow Block/Pengenalan#Konfigurasi Flow Block|Mengatur Konfigurasi Flow Block]]
* [[Docs/Modul Logic/Flow/Flow Block/Pengenalan#Menghubungkan Koneksi|Menghubungkan Koneksi]]
* [[#Menjalankan Flow Secara Manual]]
* [[#Memantau Proses]]
* [[#Menghubungkan Block Event dari Komponen]]

## Menjalankan Flow Secara Manual

Anda dapat mengeksekusi proses secara manual melalui antarmuka Flow dengan menekan tombol pada Flow Block Event, misalnya [[^button/empty|Trigger]] pada Pulser.

1. Buka halaman kerja Flow
2. Cari [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang akan dijalankan
3. Klik tombol [[^button/empty|Trigger]] pada block tersebut

Setelah dijalankan, Anda dapat melihat prosesnya pada [[#Memantau Proses]].

## Menghubungkan Block Event dari Komponen
Flow Block Event yang sudah dibuat dapat langsung dihubungkan melalui tombol [[^button/event|Event]] pada masing-masing komponen. Selengkapnya lihat [[Docs/Event/Menghubungkan Event]].

## Memantau Proses
1. Pada halaman kerja Flow, klik menu [[^button/activity|Activity]] atau tombol di sebelah kanan [[^button/refresh|Refresh]] (mode desktop)
2. Panel [[Docs/Modul Logic/Flow/Flow Activity]] akan terbuka
3. Klik [[^button/refresh|Refresh List]] untuk memuat ulang daftar, atau gunakan [[^field|Search Activity]] untuk mencari proses

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Activity]].

>**note** Info
>Jika belum ada proses yang berjalan, panel menampilkan keterangan [[^field|No Activity]]



## Praktik Terbaik

- **Mulai dari [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]].** Tentukan pemicu terlebih dahulu, baru tambahkan block pemrosesan.
- **Uji secara manual dahulu.** Gunakan tombol pada Flow Block Event sebelum mengandalkan pemicu otomatis (lihat [[#Menjalankan Flow Secara Manual]]).
- **Cek [[Docs/Modul Logic/Flow/Flow Activity|Activity]] setelah menjalankan.** Pastikan proses berjalan sesuai harapan.
- **Tata block dari kiri ke kanan.** Output berada di kanan dan input di kiri, sehingga alur lebih mudah dibaca.
- **Beri nama dan deskripsi Flow yang jelas.** Anggota lain dapat memahami tujuan Flow tanpa membuka isinya.

## Batasan dan Catatan

- Koneksi dibuat dari **output** ke **input** (lihat [[Docs/Modul Logic/Flow/Flow Block/Pengenalan#Menghubungkan Koneksi]]).
- Tombol [[^button/edit|Edit]] hanya mengubah atribut Flow ([[^field|Directory]], [[^field|Name]], dan [[^field|Description]]), bukan Flow Block pada blueprint. Pengaturan Flow Block dijelaskan di [[Docs/Modul Logic/Flow/Flow Block/Pengenalan#Konfigurasi Flow Block|Konfigurasi Flow Block]].
- Kolom [[^field|Search]] pada bilah navigasi hanya mencari Flow Block. Untuk mencari proses, gunakan [[^field|Search Activity]] pada [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]].
- Mengubah posisi dan skala panning hanya memengaruhi tampilan blueprint, bukan logika Flow.
- Informasi total activity, done, waiting, dan failure pada tombol [[^button/submission|Submission]] hanya terlihat pada mode desktop.
- Menghapus Flow menghilangkan Flow Block dan riwayat Activity, serta memutus Flow Block Action yang sudah digunakan komponen (lihat [[#Menghapus Flow]]).
- Daftar Flow Block yang tersedia mengikuti menu [[^field/add|Add]] pada blueprint (lihat [[Docs/Modul Logic/Flow/Flow Block/Pengenalan]]).
- Akses ke Flow mengikuti hak akses komponen yang diatur melalui [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].

## TL:DR

- _Flow_ mengatur logika dan proses data dengan menghubungkan [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada blueprint secara visual.
- Antarmuka Flow terdiri dari bilah navigasi dan blueprint yang bisa digeser, diperbesar, dan dibuka konteks menunya (lihat [[#Interaksi Antarmuka Flow]]).
- Bangun logika dengan menambahkan, mengatur, dan menghubungkan Flow Block (lihat [[#Membangun Logika Flow]]).
- Jalankan manual dengan tombol pada [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]], atau hubungkan Event dari komponen lewat tombol [[^button/event|Event]].
- Pantau proses lewat [[^button/activity|Activity]] pada [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]].
- Hati-hati saat menghapus Flow, karena Flow Block, riwayat Activity, dan koneksi ke komponen ikut terdampak.


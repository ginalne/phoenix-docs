---
    status: release
    title: "FAQ : Flow"
    description: Pertanyaan yang sering diajukan pada komponen Flow
    pageDecoration:
      tree:
        priority: -10
---
# FAQ : Flow

Berikut adalah pertanyaan yang Sering Diajukan pada komponen Flow:

>**faq**
>**Apa bedanya Flow dengan Event?**
>[[Docs/Event/Apa itu Event|Event]] adalah pemicu proses. Flow adalah tempat Anda menyusun dan menghubungkan Flow Block, agar pemicu tersebut menghasilkan keluaran dan otomasi.
>**Bagaimana menjalankan Flow tanpa menunggu Event?**
>Klik tombol pada Flow Block Event di antarmuka Flow, misalnya [[^button/empty|Trigger]] pada block.
>**Mengapa Activity List kosong?**
>Panel menampilkan [[^field|No Activity]] bila belum ada proses yang berjalan atau tercatat.
>**Bagaimana menambahkan Flow Block?**
>Klik kanan pada blueprint, pilih [[^field/add|Add]], lalu pilih kategori dan Flow Block yang diinginkan. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Pengenalan#Menambahkan Flow Block|Menambahkan Flow Block]].
>**Bagaimana menghubungkan dua Flow Block?**
>Klik dan tahan titik output pada block asal, seret ke titik input block tujuan, lalu lepaskan. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Pengenalan#Menghubungkan Koneksi|Menghubungkan Koneksi]].
>**Apakah Flow dapat mengirim data ke sistem lain?**
>Bisa. Gunakan Flow Block [[Docs/Modul Logic/Flow/Flow Block/Modular/HTTP |Modular]] seperti HTTP Request. Lihat [[#Contoh Penggunaan]] untuk gambaran alurnya.
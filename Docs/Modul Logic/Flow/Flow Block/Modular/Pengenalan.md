---
    status: release
    title: Flow Block Modular
    description: Pengenalan kategori Flow Block Modular, block yang menjalankan proses kompleks seperti permintaan HTTP dan layanan AI di Blueprint Flow.
    pageDecoration:
      tree:
        priority: 14
    tags: flowblock-category
---
# Flow Block Modular

>**note** Flow Block Modular merupakan salah satu kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Modular adalah kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang digunakan untuk **mengeksekusi proses yang kompleks**, seperti memanggil permintaan HTTP atau menghubungi provider jasa tertentu. Dengan block Modular, Flow dapat terhubung ke sistem dan layanan di luar Phoenix, lalu hasilnya diteruskan ke block lain untuk diolah atau disimpan.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur, block Modular bekerja setelah menerima data dari block sebelumnya, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Berbeda pula dengan [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] yang mengolah data di dalam Flow, block Modular bekerja dengan sistem atau layanan di luar Flow. Block Modular dikelompokkan berdasarkan jenis layanannya, yaitu API dan AI.

![[Docs/Modul Logic/Flow/Flow Block/Modular/modular-block-flow.png|Dua Flow Block Modular pada Blueprint: HTTP Request dan OpenAI 4]]

Block Modular umumnya ditempatkan di tengah atau di ujung alur. Data dari block sebelumnya dikirim ke layanan yang dituju, kemudian respons layanan diteruskan ke block berikutnya, misalnya untuk diurai oleh [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] lalu disimpan ke [[Docs/Modul Data/Table/Apa itu Table|Table]].

## Jenis Flow Block Modular

Phoenix menyediakan dua Flow Block Modular. Setiap block memiliki fungsi yang unik, sehingga input dan output-nya berbeda-beda.

| Grup | Block | Fungsi |
| --- | --- | --- |
| API | [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]] | Mengirim permintaan HTTP dengan metode apa pun, seperti GET, POST, dan PUT. Respons berupa [[Docs/Tipe Data/Object]] atau [[Docs/Tipe Data/String]] sesuai `Response Type`, dan respons `application/json` menjadi [[Docs/Tipe Data/Object]]. |
| AI | [[Docs/Modul Logic/Flow/Flow Block/Modular/AI/OpenAI 4|OpenAI 4 AI Block]] | Menghubungkan Flow dengan layanan OpenAI (versi 4) agar kecerdasan buatan dapat dimanfaatkan di dalam alur. |

## Memilih Flow Block Modular

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Berkomunikasi dengan sistem atau layanan lain lewat permintaan HTTP. | [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]] |
| Memanfaatkan layanan OpenAI di dalam alur. | [[Docs/Modul Logic/Flow/Flow Block/Modular/AI/OpenAI 4|OpenAI 4 AI Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]

---
    status: release
    title: Modul Logic
    description: 
    pageDecoration:
      tree:
        priority: 4
---
# Modul Logic

_Logic_ merupakan salah satu modul dalam Phoenix. Modul ini berfungsi sebagai tempat Anda membangun logika, aturan, dan otomasi yang berjalan di atas [[Docs/Modul Data/Pengenalan|Data]] yang sudah dibangun, sehingga proses pengelolaan data dapat berjalan otomatis, konsisten, dan tidak perlu dikerjakan secara manual.

Modul Logic mengatur apa yang terjadi pada data tersebut: bagaimana data diproses, kapan sebuah tindakan dijalankan, dan hasil apa yang dihasilkan.

Berikut adalah komponen yang tersedia dalam modul ini:

1. [[#Flow]]

## Flow

Flow merupakan komponen yang dapat digunakan untuk mengatur logika dan proses pengelolaan data dengan pendekatan aliran komposisi. Setiap blok yang dibangun dapat dihubungkan dan dimonitor agar setiap [[Docs/Event/Apa itu Event|Event]] yang terikat dapat menghasilkan keluaran dan otomasi yang tepat.

Lihat selengkapnya [[Docs/Modul Logic/Flow/Apa itu Flow]].


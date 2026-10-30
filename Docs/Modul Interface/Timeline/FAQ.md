---
    status: release
    title: "FAQ : Timeline"
    description: Pertanyaan yang sering diajukan pada komponen Timeline
    pageDecoration:
      tree:
        priority: -10
---
# FAQ : Timeline

Berikut adalah pertanyaan yang sering diajukan pada komponen Timeline:

> **faq**
> **Apa bedanya Timeline Event dan Timeline Data?**
> [[#Mengelola Timeline Event|Timeline Event]] memicu Flow Block [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]] pada waktu tertentu, sedangkan [[#Mengelola Timeline Data|Timeline Data]] menampilkan Row dari data sumber di sumbu waktu.
> **Mengapa field End dan Interval tidak muncul?**
> Keduanya hanya tampil ketika [[^field|Repeat]] aktif. Aktifkan [[^field|Repeat]] pada Timeline Event untuk mengisinya.
> **Bagaimana menghentikan jadwal Timeline Event tanpa menghapusnya?**
> Matikan [[^field|Active]] pada Timeline Event. Jadwal berhenti dan Timeline Event tetap ada.
> **Apakah menghapus Timeline Event ikut menghapus Pulser?**
> Tidak. [[^field|Delete Event]] hanya menghapus Timeline Event, sedangkan Pulser tetap ada di Flow.
> **Mengapa Timeline Data menampilkan Error?**
> Query belum memenuhi kaidah Timeline Output, misalnya belum menampilkan paling sedikit dua Column. Klik [[^button/q]], lalu periksa bagian [[Docs/Tipe Data/Query#Show or Hide|Show]].
> **Apakah menggeser blok mengubah data sumber?**
> Ya, bila Timeline Data `editable` dan [[Docs/Modul Developer/Workspace/Data Access]] data sumber mengizinkan. Jika salah satu tidak terpenuhi, blok tidak dapat digeser.
> **Bagaimana menambah Row dengan rentang waktu tertentu?**
> Lakukan Select pada rentang waktu yang diinginkan, lalu pilih [[^field|Add Row]]. Isian Start dan End terisi otomatis.
> **Bagaimana melihat rentang waktu yang lebih detail?**
> Putar *wheel* mouse, atau klik kanan ➜ [[^field|Zoom]] lalu pilih tingkat satuan waktu, misalnya [[^field|Date - Hour]]
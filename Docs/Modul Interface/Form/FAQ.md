---
    status: release
    title: "FAQ : Form"
    description: Pertanyaan yang Sering Diajukan pada komponen Form
    pageDecoration:
      tree:
        priority: -10
---
# FAQ : Form

Berikut adalah pertanyaan yang Sering Diajukan pada komponen Form:

> **faq**
> **Apa bedanya tombol Edit dan toggle mode?**
> Tombol [[^button/edit|Edit]] mengubah atribut Form ([[^field|Name]] dan [[^field|Description]]), sedangkan toggle [[^field|mode]] berpindah antara [[^mode/view]] dan [[^mode/edit]] untuk menyusun isi Form.
> **Mengapa saya tidak bisa beralih ke Edit Mode?**
> Beralih ke Edit Mode membutuhkan [[^field|Data Access]] di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] yang mengizinkan perubahan Form. Hubungi pengelola Workspace Anda.
> **Apakah saya harus menekan Save setiap kali mengubah Form?**
> Tidak harus. Perubahan tersimpan otomatis setelah sekitar 3 detik, dan Anda juga dapat menekan [[^button/save|Save]] secara manual.
> **Apakah satu orang hanya bisa mengirim Form sekali?**
> Hanya bila [[^field|Single Submission]] aktif, dan pembatasannya berlaku per perangkat.
> **Apa yang terjadi pada data jika Form dihapus?**
> Templat (Page, Elemen, dan Binding) serta riwayat Submission terhapus, tetapi data yang sudah tersimpan di [[Docs/Modul Data/Table/Apa itu Table|Table]] tidak langsung terhapus. Tautan Publish juga menjadi tidak valid.
> **Kapan Form dapat disubmit?**
> Form hanya dapat disubmit setelah pengisi mencapai Page terakhir pada [[#Mengelola Page Form|Form Flow]].
> **Di mana penjelasan setiap Elemen?**
> Setiap Elemen punya halaman sendiri, misalnya [[Docs/Modul Interface/Form/Elemen Form/Layout/Card]] dan [[Docs/Modul Interface/Form/Elemen Form/Input/Basic]]. Lihat daftarnya di [[#Memahami Elemen]].
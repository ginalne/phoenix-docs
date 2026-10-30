---
    status: release
    title: "FAQ : Table View"
    description: Pertanyaan yang sering diajukan pada komponen Table View
    pageDecoration:
      tree:
        priority: -10
---
# FAQ : Canvas

Berikut adalah pertanyaan yang sering diajukan pada komponen Canvas:

> **faq**
> **Apa bedanya tombol Edit dengan mode Edit?**
> Tombol [[^button/edit|Edit]] mengubah atribut Canvas (Name dan Description), lalu disimpan dengan [[^button|Update]]. Mode [[^value/radio|Edit]] pada toggle [[^field|mode]] dipakai untuk menyusun isi Canvas seperti Layout dan widget.
> **Mengapa saya tidak dapat berpindah ke Edit Mode?**
> Berpindah ke Edit Mode memerlukan salah satu Data Access Canvas (Add, Update, atau Delete) bernilai [[^value/boolean/allow]] pada [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]]. Jika ketiganya [[^value/boolean/disallow]], Canvas hanya dapat dilihat. Hubungi pengelola Workspace Anda untuk memeriksanya.
> **Apakah saya harus menekan Save?**
> [[^button/save|Save]] aktif ketika ada perubahan. Anda dapat menekannya secara manual atau menunggu sekitar 3 detik hingga tersimpan otomatis.
> **Apakah menghapus Canvas menghapus data sumber?**
> Tidak. Menghapus Canvas hanya menghapus template dan propertinya, termasuk [[Docs/Tipe Data/Query]] pada widget. Namun tautan yang sudah dibagikan melalui [[#Mempublikasikan Canvas|Publish]] menjadi tidak valid.
> **Apakah widget dapat dipakai untuk mengubah data sumber?**
> Tidak. Widget bersifat lite: Query diatur melalui [[^button/q]] pada Edit Mode, tetapi data hasil [[Docs/Tipe Data/Query|Query]] tidak dapat dimanipulasi dari Canvas. Untuk mengelola data, gunakan [[Docs/Modul Data/Table/Apa itu Table|Table]] atau [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]].
> **Untuk apa Binding pada Canvas?**
> [[#Binding Canvas|Binding]] adalah parameter yang dapat dipakai dalam Query widget. Dengan Binding, satu desain Canvas dapat menampilkan informasi berbeda, misalnya dari satu pesanan ke pesanan lain, tanpa membuat Canvas baru.
> **Apa itu Template Canvas?**
> [[#Template Canvas|Template]] adalah gabungan banyak widget yang sudah didesain dan siap dipakai. Tambahkan melalui perintah `/template` pada Edit Mode.
> **Apakah Canvas yang dipublikasikan dapat dibuka siapa saja?**
> Ya. Tautan [[^field|Link]] dengan Status [[^value/radio|Active]] dapat dibuka publik dalam View Mode, termasuk menekan widget Button. Pastikan Flow yang dipicu aman dijalankan publik.
> **Apa yang dapat dilakukan widget Button?**
> Widget [[#Widget Canvas|Button]] dapat memicu [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] melalui Flow Block [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]], atau membuka komponen apa pun.
---
    status: release
    title: Widget Button
    description: Widget Button menambahkan tombol pada Canvas yang dapat menjalankan aksi, memicu Flow, atau membuka komponen lain.
    pageDecoration:
      tree:
        priority: 0
---
# Widget Button

>**note** Widget Button merupakan salah satu widget pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Daftar widget lainnya ada di [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget Canvas]].

Widget Button adalah [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk menambahkan tombol di dalam [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]]. Aksi tombol didefinisikan melalui field [[^field|Action]] pada Header Toolbar, dan tombol dapat berfungsi sebagai pemicu [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] atau membuka komponen lain.

## Menambahkan Widget Button

Ketik `/button` dalam [[^field|Type something here to add...]] untuk menampilkan variasi lalu pilih salah satunya. Langkah lengkapnya ada di [[Docs/Modul Interface/Canvas/Widget/Menambahkan|Menambahkan Widget]].

## Antarmuka Widget Button

![[Docs/Modul Interface/Form/Widget/Button/interface-widget-button.png]]
Pada [[^mode/edit|Edit]], klik kiri widget untuk menampilkan [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar]] di atas widget, [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]] di bawah widget.

### Header Toolbar

| Elemen | Fungsi |
| --- | --- |
| Ikon Button (paling kiri) | Menandai jenis widget. |
| Ikon pegangan ⋮⋮ | Memindahkan widget ke posisi atau Layout lain. |
| [[^field\|Action]] | Mendefinisikan aksi tombol dengan Tipe Data [[Docs/Tipe Data/Action]]. Aksi dapat berupa aksi terhadap Row Table, membuka halaman, atau membuka popup Interface. |
| [[^button/delete\|Remove]] | Menghapus widget dari Canvas. Lihat [[#Menghapus Widget Button]]. |

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* pada widget dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Layout Panel]].

### Fungsi Button

| Fungsi | Penjelasan |
| --- | --- |
| Memicu Flow | Menekan tombol menjalankan [[Docs/Modul Logic/Flow/Apa itu Flow\|Flow]] melalui Flow Block [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser\|Pulser]]. |
| Membuka komponen | Menekan tombol membuka komponen apa pun. Tombol dapat membuka [[Docs/Modul Interface/Canvas/Apa itu Canvas\|Canvas]] dengan [[Docs/Modul Interface/Canvas/Apa itu Canvas#Binding Canvas\|Binding]] sebagai parameter. |

>**warning** Button pada Canvas yang dipublikasikan dapat ditekan publik
> Jika Canvas dipublikasikan dengan Status [[^value/radio|Active]], siapa pun yang memiliki tautan dapat menekan widget Button. Pastikan Flow atau komponen yang dipicu aman dijalankan oleh publik.

## Menghapus Widget Button

Langkah menghapus Widget Button sama dengan menghapus widget lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan
> Menghapus widget akan menghapus semua konfigurasi yang ada, termasuk aksi tombol yang sudah didefinisikan. Flow dan komponen yang dipicu tetap aman. Setelah terhapus, aksi tidak bisa dikembalikan.

## Praktik Terbaik

- **Berhati-hati dengan Canvas publik.** Siapa pun yang memiliki tautan dapat menekan Button, jadi pastikan [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]] dan Flow yang dipicu aman dijalankan publik.
- **Gunakan satu tombol untuk satu tujuan.** Tombol yang jelas fungsinya memudahkan pembaca memahami hasil dari menekannya.
- **Atur [[^field|min.]] tinggi dan lebar.** Beri ruang cukup agar tombol mudah ditekan dan tidak terpotong oleh widget lain pada Canvas.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Di mana aksi tombol diatur?**
> Pada field [[^field|Action]] di [[Docs/Modul Interface/Canvas/Widget/Mengonfigurasi#Header Toolbar|Header Toolbar]], dengan Tipe Data [[Docs/Tipe Data/Action]].
> **Apa yang dapat dilakukan widget Button?**
> Widget Button dapat menjalankan aksi yang didefinisikan pada [[^field|Action]], memicu [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]], atau membuka komponen lain.
> **Flow Block apa yang menerima pemicu dari Button?**
> Flow Block Event yang menerima pemicu dari Button adalah [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]].
> **Komponen apa saja yang dapat dibuka oleh Button?**
> Semua komponen. Tombol juga dapat membuka Canvas dengan [[Docs/Modul Interface/Canvas/Apa itu Canvas#Binding Canvas|Binding]] sebagai parameter.
> **Apakah Button dapat ditekan oleh publik?**
> Ya, bila Canvas dipublikasikan dengan Status [[^value/radio|Active]]. Pastikan Flow atau komponen yang dipicu aman dijalankan publik.
> **Apakah menghapus widget menghapus Flow yang dipicunya?**
> Tidak. Menghapus widget hanya menghapus tampilan dan konfigurasinya. Flow dan komponen yang dipicu tetap aman.


---
    status: draft
    pageDecoration:
      icon: x
      tree:
        priority: 10
    tags:
      draft
---
# Apa itu Flow Block

Flow Block adalah unit terkecil penyusun Flow, dan setiap block memiliki fungsi (masukan, proses dan keluaran yang berbeda-beda) dan dapat dihubungkan dengan block lain.

Pengkategorian Flow Block berfungsi agar memudahkan pencarian block. Selengkapnya bisa klik tautan per masing-masing kategori atau isinya.

| Kategori | Jenis Flow Block |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Event]] | Enum Data Event, Pulser, Table Row Event, Tree Node Event, Variable Event |
| [[Docs/Modul Logic/Flow/Flow Block/Data/Pengenalan|Data]] | Variable, Enum, Table, dan Tree beserta block pengelolaan datanya (misalnya Add Variable, Variable Getter, Add Row, Add Node) |
| [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Pengenalan|I/O]] | Branch, Passer |
| [[Docs/Modul Logic/Flow/Flow Block/Query/Pengenalan|Query]] | Condition, Execute |
| [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Operator]] | Number (Increment), String (Concatenate, Implode, Pad Left, Pad Right), Table (TableRow Parse), Object (Assign, Merge, Parse, Stringify), Boolean (If), Tree (Node Parse) |
| [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan|Modular]] | API (HTTP Request), AI (OpenAI 4) |
| [[Docs/Modul Logic/Flow/Flow Block/Misc/Pengenalan|Misc]] | Chrono (Delay), Error (Error Message) |


Berikut adalah cara mengelola Flow Block didalam Flow:
1. [[Docs/Modul Logic/Flow/Flow Block/Menambahkan]]
2. [[Docs/Modul Logic/Flow/Flow Block/Menghapus]]
3. [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi]]
4. [[Docs/Modul Logic/Flow/Flow Block/Menghapus Koneksi]]

## TL:DR
- Tambahkan block lewat klik kanan pada blueprint > [[^field/add|Add]].
- Hubungkan block dengan menahan klik pada output, lalu lepaskan di input. Hapus hubungan dengan melepas pada bagian kosong.
- Jalankan manual dengan tombol pada Block Event, lalu pantau lewat [[^button/activity|Activity]].

## FAQ : Pertanyaan yang Sering Diajukan

>**faq**
>**Bagaimana menambahkan Flow Block?**
>Klik kanan pada blueprint, pilih [[^field/add|Add]], lalu pilih kategori dan Flow Block yang diinginkan.
>**Bagaimana menghubungkan dua Flow Block?**
>Klik dan tahan titik output pada block asal, seret ke titik input block tujuan, lalu lepaskan.


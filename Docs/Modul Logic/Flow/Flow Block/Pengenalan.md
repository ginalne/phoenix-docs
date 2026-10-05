---
    status: draft
    pageDecoration:
      icon: x
      tree:
        priority: 0
    tags:
      draft
---
## Menambahkan Flow Block

![[Docs/Modul Logic/Flow/Flow Block/add-flow-block.png]]
1. Buka halaman kerja Flow
2. Klik kanan pada blueprint > [[^field/add|Add]]
3. Pilih kategori Flow Block, misalnya [[^field/event|Event]]
4. Pilih Flow Block, misalnya [[^field/event|Pulser]]
   
## Kategori Flow Block

Pengkategorian Flow Block berfungsi agar memudahkan pencarian block.  Selengkapnya bisa klik tautan per masing-masing kategori atau isinya:

| Kategori | Isi |
| --- | --- |
| **Event** | Enum Data Event, Pulser, Table Row Event, Tree Node Event, Variable Event |
| **Data** | Variable, Enum, Table, dan Tree beserta block pengelolaan datanya (misalnya Add Variable, Variable Getter, Add Row, Add Node) |
| **I/O** | Branch, Passer |
| **Query** | Condition, Execute |
| **Operator** | Number (Increment), String (Concatenate, Implode, Pad Left, Pad Right), Table (TableRow Parse), Object (Assign, Merge, Parse, Stringify), Boolean (If), Tree (Node Parse) |
| **Modular** | API (HTTP Request), AI (OpenAI 4) |
| **Misc.** | Chrono (Delay), Error (Error Message) |

## Menghapus Flow Block

![[Docs/Modul Logic/Flow/Flow Block/delete-flow-block.png]]
1. Klik kanan pada Flow Block yang akan dihapus
2. Klik  [[^field/delete|Delete]]
3. Konfirmasi dengan [[^button|Remove]]

Flow Block akan terhapus pada blueprint.

>**Warning** Hati-hati
>Menghapus Flow Block akan menghilangkan koneksi yang sudah terhubung, jika yang dihapus adalah kategori Event, maka hubungan komponen yang sudah dikonfigurasi akan hilang.

## Menghubungkan Flow Block
```excalidraw
url:Docs/Modul Logic/Flow/Flow Block/connecting-flow-block.excalidraw
height:312px
```
1. Arahkan kursor ke titik output pada Flow Block asal, misalnya Result pada Pulser
2. Klik dan tahan (*hold press*) titik output tersebut
3. Seret ke titik input pada Flow Block tujuan
4. Lepaskan (*release*) tombol di atas titik input

Garis koneksi akan muncul di antara kedua block.

## Menghapus Koneksi Flow Block
```excalidraw
url:Docs/Modul Logic/Flow/Flow Block/remove-connection-block-flow.excalidraw
height:500px
```
1. Arahkan kursor ke titik output pada Flow Block asal
2. Klik dan tahan (*hold press*) titik output tersebut
3. Seret ke titik input ke tempat kosong
4. Lepaskan (*release*) tombol
5. Konfirmasi dengan [[^button|Remove]]

Garis koneksi akan terhapus di antara kedua block.

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

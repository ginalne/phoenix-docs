---
    status: draft
    title: Error Message Block
    description: Flow Block untuk membuat error baru dengan pesan yang ditentukan dan menghentikan aliran pada komponen Flow.
    pageDecoration:
      tree:
        priority: 1
---

# Error Message Block

>**note** Error Message Block merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori [[Docs/Modul Logic/Flow/Flow Block/Error/Pengenalan|Flow Block Error]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Error Message Block adalah Flow Block yang membuat error baru dengan pesan yang Anda tentukan. Saat dieksekusi, block menghentikan aliran pada Activity yang sedang berjalan dan menampilkan pesan error di [[Docs/Modul Logic/Flow/Flow Activity]]. Perubahan yang sudah dilakukan block sebelumnya yang berhasil tereksekusi tidak dapat dikembalikan.

Block ini berguna untuk memberi pesan yang jelas kepada pengguna, misalnya mengganti kegagalan dari block lain dengan pesan yang lebih mudah dipahami.

![[Docs/Modul Logic/Flow/Flow Block/Error/error-message-block-flow.png|Error Message Block]]

## Input dan Output

Error Message Block memiliki satu input di sisi kiri, tidak memiliki output dan tidak memiliki Control. Input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Message]] | [[Docs/Tipe Data/Text]] | Pesan error yang akan tampil di [[Docs/Modul Logic/Flow/Flow Activity]]. Bila dibiarkan kosong, block berstatus [[^flowstate/Fatal Error]]. |

Block ini tidak memiliki output, sehingga tidak meneruskan aliran ke block lain. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**warning** Aliran dihentikan
> Saat dieksekusi, Error Message Block menghentikan aliran pada Activity yang sedang berjalan. Perubahan yang sudah dilakukan block sebelumnya yang berhasil tereksekusi tidak dapat dikembalikan. Activity lain tidak terpengaruh. Gunakan hanya pada alur yang memang harus berhenti, misalnya ketika data tidak memenuhi syarat.

## Cara Kerja

1. Isi [[^input|Message]] dengan pesan error, langsung pada block atau dari output block lain.
2. Setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat eksekusi]], block membuat error baru dengan pesan tersebut.
3. Aliran pada Activity yang sedang berjalan dihentikan dan pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity]]. Perubahan yang sudah dilakukan block sebelumnya yang berhasil tereksekusi tidak dapat dikembalikan.

## Contoh Penggunaan

| Kondisi | Hasil | Status |
| - | - | - |
| [[^input|Message]] berisi [[^value/text|Stok tidak mencukupi]] dan block dieksekusi | Aliran dihentikan dan pesan [[^value/text|Stok tidak mencukupi]] tampil di [[Docs/Modul Logic/Flow/Flow Activity]]. Perubahan dari block sebelumnya tidak dikembalikan | [[^flowstate/Abort]] |
| [[^input|Message]] dibiarkan kosong | - | [[^flowstate/Fatal Error]] |

Status [[^flowstate/Abort]] menghentikan aliran dan menampilkan pesan error di [[Docs/Modul Logic/Flow/Flow Activity]], tanpa mengembalikan perubahan yang sudah dilakukan block sebelumnya. Status [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Tulis pesan yang menjelaskan penyebab dan langkah selanjutnya**, karena [[^input|Message]] menjadi pesan yang dibaca pengguna di [[Docs/Modul Logic/Flow/Flow Activity]].
- **Hubungkan ke output [[^output|Error]] block lain**, misalnya [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]], untuk menggantikan kegagalan dengan pesan yang lebih jelas.
- **Gunakan hanya pada alur yang harus berhenti**, karena block ini menghentikan aliran, sedangkan perubahan yang sudah dilakukan block sebelumnya tidak dapat dikembalikan.

## Batasan dan Catatan

- Error Message Block tidak memiliki output, sehingga tidak ada block yang dapat dihubungkan setelahnya.
- Saat dieksekusi, block menghentikan aliran pada Activity yang sedang berjalan. Perubahan yang sudah dilakukan block sebelumnya yang berhasil tereksekusi tidak dapat dikembalikan.
- [[^input|Message]] yang dibiarkan kosong menghasilkan [[^flowstate/Fatal Error]].
- Pesan error hanya terlihat di [[Docs/Modul Logic/Flow/Flow Activity]].
- Error Message Block tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat Flow Block diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Error/Pengenalan|Flow Block Error]]
- [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Modular/AI/OpenAI 4|OpenAI 4 AI Block]]
- [[Docs/Modul Logic/Flow/Flow Activity]]
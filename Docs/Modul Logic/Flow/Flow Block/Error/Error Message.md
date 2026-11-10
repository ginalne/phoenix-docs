---
    status: release
    title: Error Message Block
    description: Flow Block untuk membuat error baru dengan pesan yang ditentukan dan menghentikan aliran pada komponen Flow.
    pageDecoration:
      tree:
        priority: 1
---
# Error Message Block

>**note** Error Message Block merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori [[Docs/Modul Logic/Flow/Flow Block/Error/Pengenalan|Flow Block Error]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Error Message Block adalah Flow Block yang membuat error baru dengan pesan yang Anda tentukan. Saat dieksekusi, block menghentikan seluruh aliran dan pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

Block ini berguna untuk memberi pesan yang jelas kepada pengguna, misalnya mengganti kegagalan dari block lain dengan pesan yang lebih mudah dipahami.

![[Docs/Modul Logic/Flow/Flow Block/Error/error-message-block-flow.png|Error Message Block]]

<!--
  * [DONE] Penempatan gambar: potong screenshot menjadi `error-message-block-flow.png`, simpan di folder `Docs/Modul Logic/Flow/Flow Block/Error/`.
-->

## Input dan Output

Error Message Block memiliki satu input di sisi kiri, tidak memiliki output dan tidak memiliki Control. Input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Message]] | [[Docs/Tipe Data/Text]] | Pesan error yang akan tampil di [[Docs/Modul Logic/Flow/Flow Activity]]. |

Block ini tidak memiliki output, sehingga tidak meneruskan aliran ke block lain. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**warning** Aliran dihentikan
> Saat dieksekusi, Error Message Block menghentikan seluruh aliran. Gunakan hanya pada alur yang memang harus berhenti, misalnya ketika data tidak memenuhi syarat.

<!--
  * [TODO] Status Activity akibat block ini ditulis [[^flowstate|Fatal Error]] karena block tidak memiliki output (prinsip: kasus tanpa output menjadi Fatal Error). Penjelasan penulis hanya menyebut "memengaruhi status Error atau Fatal Error". Mohon konfirmasi.
    Jawaban: Sepertinya kita perlu Status baru yaitu “Abort” bukan “Fatal Error”
  * [TODO] Cakupan "seluruh aliran" (hanya Activity yang sedang berjalan atau juga Activity lain pada Flow yang sama) dan dampak pada perubahan data yang sudah dilakukan block sebelumnya belum dijelaskan penulis. Mohon jelaskan untuk melengkapi callout warning.
    Jawaban: Hanya di activity yang sedang berjalan. Dampak perubahan data yang sudah dilakukan block sebelumnya adalah Rollback.
  * [TODO] Perilaku bila [[^input|Message]] dibiarkan kosong belum dijelaskan penulis, sehingga belum ditulis.
    Jawaban: Jadikan Fatal Error bila kosong.
-->

## Cara Kerja

1. Isi [[^input|Message]] dengan pesan error, langsung pada block atau dari output block lain.
2. Setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat eksekusi]], block membuat error baru dengan pesan tersebut.
3. Seluruh aliran dihentikan, dan pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Contoh Penggunaan

| Kondisi | Hasil | Status |
| - | - | - |
| [[^input|Message]] berisi [[^value/text|Stok tidak mencukupi]] dan block dieksekusi | Aliran dihentikan dan pesan [[^value/text|Stok tidak mencukupi]] tampil di [[Docs/Modul Logic/Flow/Flow Activity]] | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Tulis pesan yang menjelaskan penyebab dan langkah selanjutnya**, karena [[^input|Message]] menjadi pesan yang dibaca pengguna di [[Docs/Modul Logic/Flow/Flow Activity]].
- **Hubungkan ke output [[^output|Error]] block lain**, misalnya [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]], untuk menggantikan kegagalan dengan pesan yang lebih jelas.
- **Gunakan hanya pada alur yang harus berhenti**, karena block ini menghentikan seluruh aliran.

## Batasan dan Catatan

- Error Message Block tidak memiliki output, sehingga tidak ada block yang dapat dihubungkan setelahnya.
- Saat dieksekusi, block menghentikan seluruh aliran.
- Pesan error hanya terlihat di [[Docs/Modul Logic/Flow/Flow Activity]].
- Error Message Block tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat Flow Block diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Error/Pengenalan|Flow Block Error]]
- [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Modular/AI/OpenAI 4|OpenAI 4 AI Block]]
- [[Docs/Modul Logic/Flow/Flow Activity]]
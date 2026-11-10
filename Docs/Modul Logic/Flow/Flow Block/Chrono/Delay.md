---
    status: release
    title: Delay Block
    description: Flow Block untuk menunda aliran selama waktu yang ditentukan pada komponen Flow.
    pageDecoration:
      tree:
        priority: 1
---
# Delay Block

>**note** Delay Block merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori [[Docs/Modul Logic/Flow/Flow Block/Chrono/Pengenalan|Flow Block Chrono]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Delay Block adalah Flow Block yang menunda aliran selama waktu yang ditentukan. Setelah waktu tunggu selesai, block mengeluarkan [[^output|Finish]] sehingga block berikutnya dapat dilanjutkan.

![[Docs/Modul Logic/Flow/Flow Block/Chrono/delay-block-flow.png|Delay Block]]

<!--
  * [DONE] Penempatan gambar: potong screenshot menjadi `delay-block-flow.png`, simpan di folder `Docs/Modul Logic/Flow/Flow Block/Chrono/`.
-->

## Input dan Output

Delay Block memiliki satu input di sisi kiri, satu output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Duration]] | [[Docs/Tipe Data/Number]] | Lama waktu tunggu dalam satuan detik. Wajib diisi. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Finish]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila waktu tunggu sudah selesai dan aliran diteruskan. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

<!--
  * [TODO] Batas waktu maksimum, penggunaan angka pecahan (misalnya 0.5), serta perilaku bila [[^input|Duration]] bernilai 0 atau negatif belum dijelaskan penulis, sehingga belum ditulis.
    Jawaban: Iya, isi harus lebih dari 0.
-->

## Cara Kerja

1. Isi [[^input|Duration]] dalam satuan detik, langsung pada block atau dari output block lain.
2. Setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat eksekusi]], block mulai menunggu. Selama menunggu, status pada [[Docs/Modul Logic/Flow/Flow Activity]] terlihat [[^flowstate|Waiting]].
3. Setelah waktu tunggu selesai, [[^output|Finish]] mengeluarkan [[^value/boolean/true]] dan aliran dilanjutkan ke block yang terhubung.

## Contoh Penggunaan

Contoh berikut memakai [[^input|Duration]] [[^value/number|5]].

| Kondisi | Finish | Status |
| - | - | - |
| Selama 5 detik menunggu | - | [[^flowstate|Waiting]] |
| Setelah 5 detik berlalu | [[^value/boolean/true]] | [[^flowstate|Succeed]] |
| [[^input|Duration]] dibiarkan kosong | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Isi [[^input|Duration]] dalam detik.** Pastikan nilainya sudah dikonversi ke detik sebelum diisi.
- **Pantau status [[^flowstate|Waiting]] pada [[Docs/Modul Logic/Flow/Flow Activity]]** untuk memastikan Delay Block sedang menunggu dan belum selesai.
- **Gunakan Delay Block untuk menjeda aliran** sebelum block yang perlu menunggu waktu tertentu, misalnya sebelum memanggil sistem lain lewat [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]].

## Batasan dan Catatan

- [[^input|Duration]] yang dibiarkan kosong menghasilkan [[^flowstate|Fatal Error]].
- Satuan [[^input|Duration]] adalah detik.
- Selama menunggu, [[^output|Finish]] belum keluar sehingga block yang terhubung ke [[^output|Finish]] belum dieksekusi.
- Delay Block tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat Flow Block diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Chrono/Pengenalan|Flow Block Chrono]]
- [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]]
- [[Docs/Modul Logic/Flow/Flow Activity]]
---
    status: draft
    title: HTTP Request Block
    description: Flow Block untuk mengirim permintaan HTTP ke sistem lain dan menerima responsnya pada komponen Flow.
    pageDecoration:
      tree:
        priority: 2
---

# HTTP Request Block

>**note** HTTP Request Block merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan|Flow Block Modular]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

HTTP Request Block adalah Flow Block yang mengirim permintaan HTTP ke sistem lain dan menerima responsnya sebagai data yang dapat diproses block berikutnya. Block ini mendukung seluruh metode HTTP, sehingga Flow dapat terhubung dengan layanan atau API di luar Phoenix.

![[Docs/Modul Logic/Flow/Flow Block/Modular/API/http-request-block-flow.png|HTTP Request Block]]

<!--
  * [DONE] Penempatan gambar: potong screenshot menjadi `http-request-block-flow.png`, simpan di folder `Docs/Modul Logic/Flow/Flow Block/Modular/API/`.
-->

## Input dan Output

HTTP Request Block memiliki empat input di sisi kiri, dua output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Method]] | [[Docs/Tipe Data/String]] | Metode HTTP yang valid, misalnya [[^value/string|GET]] atau [[^value/string|POST]]. Wajib diisi. |
| [[^input|Endpoint]] | [[Docs/Tipe Data/String]] | Alamat tujuan permintaan. Wajib diisi. |
| [[^input|Header]] | [[Docs/Tipe Data/Object]] | Header yang dikirim bersama permintaan. Boleh dibiarkan kosong. |
| [[^input|Payload]] | [[Docs/Tipe Data/Object]] | Data yang dikirim bersama permintaan. Boleh dibiarkan kosong. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Success]] | [[Docs/Tipe Data/Object]] atau [[Docs/Tipe Data/Text]] | Respons permintaan. Bertipe [[Docs/Tipe Data/Object]] bila hasilnya JSON dan [[Docs/Tipe Data/Text]] bila hasilnya HTML. Keluar bila permintaan berhasil. |
| [[^output|Error]] | [[Docs/Tipe Data/Object]] | Respons error dari permintaan. Keluar bila permintaan menghasilkan respons error. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**note** Mengelola Error
> Hubungkan output [[^output|Error]] ke block penanganan agar Flow dapat memberi tahu pengguna, misalnya [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]]. Block tersebut hanya dieksekusi bila kegagalan terjadi.

>**warning** Permintaan ke sistem lain
> HTTP Request Block mengirim data ke sistem di luar Phoenix. Permintaan yang mengubah data di sistem tujuan, misalnya [[^value/string|POST]] atau [[^value/string|DELETE]], tidak dapat dibatalkan dari Phoenix. Hindari mengisi [[^input|Header]] atau [[^input|Payload]] dengan nilai rahasia seperti token secara langsung. Simpan nilai tersebut pada [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] dan hubungkan lewat [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]].

<!--
  * [TODO] Isi Object pada output [[^output|Error]] belum dijelaskan penulis (misalnya kode status atau pesan). Mohon jelaskan.
    Jawaban: Isi Error object pada HTTP Request adalah: status dan body (apakah ini cukup? atau menurut ada tambahan agar sistem saya perbaiki)
  * [TODO] Apa yang dihitung sebagai "respons error" (kode status tertentu, kegagalan koneksi, atau keduanya) belum dijelaskan penulis.
    Jawaban: sesuai dengan hasil status code pada request. jika kegagalan koneksi sudah termasuk. (dalam kodingan saya pakai try catch, jadi segala error direspon ke output ini)
  * [TODO] Perilaku bila respons bukan JSON atau HTML belum dijelaskan penulis, sehingga belum ditulis.
    Jawaban: Itu hanya contoh, jika ada bentuk lain mohon lengkapi apakah itu object JSON atau bukan.
  * [TODO] Diasumsikan [[^input|Header]] dan [[^input|Payload]] boleh dibiarkan kosong karena Fatal Error hanya disebut untuk [[^input|Method]] dan [[^input|Endpoint]]. Mohon konfirmasi.
    Jawaban: Iya boleh dibiarkan kosong, tapi akan Error jika request gagal.
  * [TODO] Isi callout warning (kerahasiaan nilai di Header atau Payload dan permintaan yang tidak dapat dibatalkan) adalah draf. Mohon konfirmasi, terutama apakah isi Header terlihat oleh pengguna yang dapat membuka Flow.
    Jawaban: Sudah oke
-->

## Cara Kerja

1. Isi [[^input|Method]] dan [[^input|Endpoint]], lalu isi [[^input|Header]] dan [[^input|Payload]] bila diperlukan. Setiap input dapat diisi langsung atau dihubungkan dari output block lain.
2. Setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat eksekusi]], block mengirim permintaan ke [[^input|Endpoint]] dengan [[^input|Method]] yang dipilih.
3. Bila permintaan berhasil, [[^output|Success]] mengeluarkan respons sebagai [[Docs/Tipe Data/Object]] (JSON) atau [[Docs/Tipe Data/Text]] (HTML).
4. Bila permintaan menghasilkan respons error, [[^output|Error]] mengeluarkan respons tersebut sebagai [[Docs/Tipe Data/Object]].

## Contoh Penggunaan

Contoh berikut mengirim permintaan ke [[^input|Endpoint]] [[^value/string|https://api.example.com/pesanan]].

| Kondisi | Success | Error | Status |
| - | - | - | - |
| [[^input|Method]] [[^value/string|GET]] dan respons berupa JSON | [[Docs/Tipe Data/Object]] berisi respons | - | [[^flowstate|Succeed]] |
| [[^input|Method]] [[^value/string|POST]] dengan [[^input|Payload]] [[^value/object|{ "nomor": "PSN-001" }]] dan respons berupa JSON | [[Docs/Tipe Data/Object]] berisi respons | - | [[^flowstate|Succeed]] |
| Respons berupa HTML | [[Docs/Tipe Data/Text]] berisi HTML | - | [[^flowstate|Succeed]] |
| Permintaan menghasilkan respons error | - | [[Docs/Tipe Data/Object]] berisi respons error | [[^flowstate|Error]] |
| [[^input|Method]] dibiarkan kosong | - | - | [[^flowstate|Fatal Error]] |
| [[^input|Endpoint]] dibiarkan kosong | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Error]] dan [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Tangani output [[^output|Error]].** Hubungkan block penanganan ke [[^output|Error]] agar kegagalan permintaan tidak berlalu tanpa pemberitahuan.
- **Simpan nilai rahasia pada [[Docs/Modul Data/Variable/Apa itu Variable|Variable]].** Ambil nilainya dengan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]] lalu hubungkan ke [[^input|Header]] atau [[^input|Payload]].
- **Isi [[^input|Payload]] hanya bila metode yang dipakai membawa data**, misalnya [[^value/string|POST]].
- **Pilih [[^input|Method]] sesuai tujuan permintaan** dan pastikan [[^input|Endpoint]] sudah benar sebelum menjalankan Flow, karena permintaan ke sistem lain dapat mengubah data di sana.

## Batasan dan Catatan

- [[^input|Method]] atau [[^input|Endpoint]] yang dibiarkan kosong menghasilkan [[^flowstate|Fatal Error]].
- [[^output|Success]] dan [[^output|Error]] tidak keluar bersamaan. Hanya satu yang meneruskan aliran sesuai hasil permintaan.
- Tipe data [[^output|Success]] mengikuti hasil permintaan: [[Docs/Tipe Data/Object]] bila JSON dan [[Docs/Tipe Data/Text]] bila HTML.
- HTTP Request Block tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat Flow Block diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan|Flow Block Modular]]
- [[Docs/Modul Logic/Flow/Flow Block/Modular/AI/OpenAI 4|OpenAI 4 AI Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]
- [[Docs/Modul Logic/Flow/Flow Activity]]
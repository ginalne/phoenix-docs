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

## Input dan Output

HTTP Request Block memiliki empat input di sisi kiri, dua output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Method]] | [[Docs/Tipe Data/String]] | Metode HTTP yang valid, misalnya [[^value/string|GET]] atau [[^value/string|POST]]. Wajib diisi. |
| [[^input|Endpoint]] | [[Docs/Tipe Data/String]] | Alamat tujuan permintaan. Wajib diisi. |
| [[^input|Header]] | [[Docs/Tipe Data/Object]] | Header yang dikirim bersama permintaan. Boleh dibiarkan kosong. |
| [[^input|Payload]] | [[Docs/Tipe Data/Object]] | Data yang dikirim bersama permintaan. Boleh dibiarkan kosong. |

[[^input|Header]] dan [[^input|Payload]] boleh dibiarkan kosong. Namun bila permintaan gagal, hasilnya tetap keluar lewat [[^output|Error]].

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Success]] | [[Docs/Tipe Data/Object]], [[Docs/Tipe Data/Text]], atau [[Docs/Tipe Data/File]] | Respons permintaan. Bertipe [[Docs/Tipe Data/Object]] bila hasilnya JSON, [[Docs/Tipe Data/File]] bila hasilnya berupa file, dan [[Docs/Tipe Data/Text]] untuk bentuk lain, misalnya HTML. Keluar bila permintaan berhasil. |
| [[^output|Error]] | [[Docs/Tipe Data/Object]] | Berisi `status` dan `body` dari respons. Keluar bila status code selain 2xx atau koneksi gagal. Bila koneksi gagal, `status` bernilai [[^value/number|0]] dan `body` berisi pesan default berbahasa Inggris [[^value/string|Failed to connect to the endpoint.]] |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**note** Mengelola Error
> Hubungkan output [[^output|Error]] ke block penanganan agar Flow dapat memberi tahu pengguna, misalnya [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]]. Block tersebut hanya dieksekusi bila kegagalan terjadi.

>**warning** Permintaan ke sistem lain
> HTTP Request Block mengirim data ke sistem di luar Phoenix. Permintaan yang mengubah data di sistem tujuan, misalnya [[^value/string|POST]] atau [[^value/string|DELETE]], tidak dapat dibatalkan dari Phoenix. Hindari mengisi [[^input|Header]] atau [[^input|Payload]] dengan nilai rahasia seperti token secara langsung. Simpan nilai tersebut pada [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] dan hubungkan lewat [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]].

## Cara Kerja

1. Isi [[^input|Method]] dan [[^input|Endpoint]], lalu isi [[^input|Header]] dan [[^input|Payload]] bila diperlukan. Setiap input dapat diisi langsung atau dihubungkan dari output block lain.
2. Setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat eksekusi]], block mengirim permintaan ke [[^input|Endpoint]] dengan [[^input|Method]] yang dipilih.
3. Bila permintaan berhasil (status code 2xx), [[^output|Success]] mengeluarkan respons sebagai [[Docs/Tipe Data/Object]] bila JSON, [[Docs/Tipe Data/File]] bila berupa file, atau [[Docs/Tipe Data/Text]] untuk bentuk lain seperti HTML.
4. Bila status code selain 2xx atau koneksi gagal, [[^output|Error]] mengeluarkan [[Docs/Tipe Data/Object]] berisi `status` dan `body`.

## Contoh Penggunaan

Contoh berikut mengirim permintaan ke [[^input|Endpoint]] [[^value/string|https://api.example.com/pesanan]].

| Kondisi | Success | Error | Status |
| - | - | - | - |
| [[^input|Method]] [[^value/string|GET]] dan respons berupa JSON | [[Docs/Tipe Data/Object]] berisi respons | - | [[^flowstate|Succeed]] |
| [[^input|Method]] [[^value/string|POST]] dengan [[^input|Payload]] [[^value/object|{ "nomor": "PSN-001" }]] dan respons berupa JSON | [[Docs/Tipe Data/Object]] berisi respons | - | [[^flowstate|Succeed]] |
| Respons berupa HTML | [[Docs/Tipe Data/Text]] berisi HTML | - | [[^flowstate|Succeed]] |
| Respons berupa file | [[Docs/Tipe Data/File]] | - | [[^flowstate|Succeed]] |
| Status code selain 2xx | - | [[Docs/Tipe Data/Object]] berisi `status` dan `body` | [[^flowstate|Error]] |
| Koneksi ke [[^input|Endpoint]] gagal | - | [[Docs/Tipe Data/Object]] berisi `status` [[^value/number|0]] dan `body` pesan default | [[^flowstate|Error]] |
| [[^input|Method]] dibiarkan kosong | - | - | [[^flowstate|Fatal Error]] |
| [[^input|Endpoint]] dibiarkan kosong | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Error]] dan [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Tangani output [[^output|Error]].** Hubungkan block penanganan ke [[^output|Error]] agar kegagalan permintaan tidak berlalu tanpa pemberitahuan.
- **Simpan nilai rahasia pada [[Docs/Modul Data/Variable/Apa itu Variable|Variable]].** Ambil nilainya dengan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]] lalu hubungkan ke [[^input|Header]] atau [[^input|Payload]].
- **Isi [[^input|Payload]] hanya bila metode yang dipakai membawa data**, misalnya [[^value/string|POST]].
- **Pilih [[^input|Method]] sesuai tujuan permintaan** dan pastikan [[^input|Endpoint]] sudah benar sebelum menjalankan Flow, karena permintaan ke sistem lain dapat mengubah data di sana.

## Batasan dan Catatan

- [[^input|Method]] atau [[^input|Endpoint]] yang dibiarkan kosong menghasilkan [[^flowstate|Fatal Error]]. [[^input|Header]] dan [[^input|Payload]] boleh kosong.
- [[^output|Success]] dan [[^output|Error]] tidak keluar bersamaan. Hanya satu yang meneruskan aliran sesuai hasil permintaan.
- Tipe data [[^output|Success]] mengikuti hasil permintaan: [[Docs/Tipe Data/Object]] bila JSON, [[Docs/Tipe Data/File]] bila berupa file, dan [[Docs/Tipe Data/Text]] untuk bentuk lain seperti HTML.
- Seluruh kegagalan permintaan keluar lewat [[^output|Error]]: status code selain 2xx dan kegagalan koneksi.
- HTTP Request Block tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat Flow Block diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan|Flow Block Modular]]
- [[Docs/Modul Logic/Flow/Flow Block/Modular/AI/OpenAI 4|OpenAI 4 AI Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]
- [[Docs/Modul Logic/Flow/Flow Activity]]
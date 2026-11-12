---
    status: release
    title: OpenAI 4 Block
    description: Flow Block untuk mengirim permintaan ke OpenAI dan menerima hasilnya berupa teks atau fungsi pada komponen Flow.
    pageDecoration:
      tree:
        priority: 1
---

# OpenAI 4 Block

>**note** OpenAI 4 Block merupakan salah satu [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan|Flow Block Modular]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

OpenAI 4 Block adalah Flow Block yang mengirim permintaan ke OpenAI dan menerima hasilnya sebagai [[Docs/Tipe Data/Text]] atau sebagai Function yang dapat diproses block berikutnya. Block ini memungkinkan Flow memanfaatkan AI di tengah alur, misalnya untuk menjawab atau mengolah teks dari data yang sedang diproses.

![[Docs/Modul Logic/Flow/Flow Block/Modular/AI/openai-4-block-flow.png|OpenAI 4 Block]]

## Input dan Output

OpenAI 4 Block memiliki delapan input di sisi kiri, tiga output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|API Key]] | [[Docs/Tipe Data/String]] | Kunci akses ke OpenAI. Wajib diisi. |
| [[^input|Model]] | [[Docs/Tipe Data/String]] | Model OpenAI yang dipakai. Wajib diisi. |
| [[^input|Input]] | [[Docs/Tipe Data/Text]] | Teks yang dikirim ke OpenAI. Boleh dibiarkan kosong bila [[^input|Messages]] diisi. |
| [[^input|Messages]] | [[Docs/Tipe Data/Object]] | Messages untuk permintaan ke OpenAI. Boleh dibiarkan kosong bila [[^input|Input]] diisi. |
| [[^input|Tools]] | [[Docs/Tipe Data/Object]] | Tools yang tersedia bagi OpenAI. Diperlukan agar output [[^output|Function]] dapat keluar. Boleh dibiarkan kosong. |
| [[^input|Tool Choice]] | [[Docs/Tipe Data/Object]] | Pengaturan pemilihan Tools. Boleh dibiarkan kosong. |
| [[^input|Max Output]] | [[Docs/Tipe Data/Number]] | Batas keluaran dari OpenAI. Wajib diisi. |
| [[^input|Temperature]] | [[Docs/Tipe Data/Number]] | Pengaturan Temperature untuk permintaan. Wajib diisi. |

Bila [[^input|Input]] dan [[^input|Messages]] sama-sama kosong, OpenAI mengembalikan error dan hasilnya keluar lewat [[^output|Error]].

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Text]] | [[Docs/Tipe Data/Text]] | Jawaban OpenAI berupa teks. Keluar bila hasilnya berupa teks. |
| [[^output|Function]] | [[Docs/Tipe Data/Object]] (JSON) | Hasil berupa Function. Keluar bila [[^input|Tools]] diisi dan hasilnya berupa Function. |
| [[^output|Error]] | [[Docs/Tipe Data/Object]] | Respons error dari OpenAI. Keluar bila OpenAI mengembalikan respons error. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**note** Mengelola Error
> Hubungkan output [[^output|Error]] ke block penanganan agar Flow dapat memberi tahu pengguna, misalnya [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]]. Block tersebut hanya dieksekusi bila kegagalan terjadi.

>**warning** Kerahasiaan API Key
> [[^input|API Key]] memberi akses ke akun OpenAI Anda dan pemakaiannya mengikuti ketentuan akun tersebut. Hindari mengisi [[^input|API Key]] langsung pada block. Simpan pada [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] dan hubungkan lewat [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]].

## Cara Kerja

1. Isi [[^input|API Key]], [[^input|Model]], [[^input|Max Output]], dan [[^input|Temperature]]. Isi juga [[^input|Input]], [[^input|Messages]], [[^input|Tools]], dan [[^input|Tool Choice]] sesuai kebutuhan. Setiap input dapat diisi langsung atau dihubungkan dari output block lain.
2. Setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat eksekusi]], block mengirim permintaan ke OpenAI.
3. Bila hasilnya berupa teks, [[^output|Text]] mengeluarkan jawaban tersebut.
4. Bila [[^input|Tools]] diisi dan hasilnya berupa Function, [[^output|Function]] mengeluarkan Function tersebut sebagai [[Docs/Tipe Data/Object]] (JSON).
5. Bila OpenAI mengembalikan respons error, [[^output|Error]] mengeluarkan respons tersebut.

## Contoh Penggunaan

| Kondisi | Text | Function | Error | Status |
| - | - | - | - | - |
| Seluruh input wajib terisi dan hasilnya berupa teks | [[Docs/Tipe Data/Text]] berisi jawaban | - | - | [[^flowstate/Succeed]] |
| [[^input|Tools]] diisi dan hasilnya berupa Function | - | [[Docs/Tipe Data/Object]] (JSON) berisi Function | - | [[^flowstate/Succeed]] |
| OpenAI mengembalikan respons error | - | - | [[Docs/Tipe Data/Object]] berisi respons error | [[^flowstate/Error]] |
| [[^input|Input]] dan [[^input|Messages]] sama-sama kosong | - | - | [[Docs/Tipe Data/Object]] berisi respons error | [[^flowstate/Error]] |
| [[^input|API Key]] atau [[^input|Model]] dibiarkan kosong | - | - | - | [[^flowstate/Fatal Error]] |
| [[^input|Max Output]] atau [[^input|Temperature]] dibiarkan kosong | - | - | - | [[^flowstate/Fatal Error]] |

Status [[^flowstate/Error]] dan [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Simpan [[^input|API Key]] pada [[Docs/Modul Data/Variable/Apa itu Variable|Variable]].** Ambil nilainya dengan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]] agar nilainya tidak terlihat oleh anggota tanpa akses.
- **Isi [[^input|Input]] atau [[^input|Messages]].** Bila keduanya kosong, OpenAI mengembalikan error lewat [[^output|Error]].
- **Tangani output [[^output|Error]].** Hubungkan block penanganan agar kegagalan dari OpenAI tidak berlalu tanpa pemberitahuan.
- **Isi [[^input|Tools]] hanya bila Anda membutuhkan output [[^output|Function]].** Tanpa [[^input|Tools]], hasil berupa Function tidak akan keluar.
- **Pastikan [[^input|API Key]], [[^input|Model]], [[^input|Max Output]], dan [[^input|Temperature]] selalu terisi** agar block tidak berstatus [[^flowstate/Fatal Error]].

## Batasan dan Catatan

- [[^flowstate/Fatal Error]] hanya terjadi bila [[^input|API Key]], [[^input|Model]], [[^input|Max Output]], atau [[^input|Temperature]] dibiarkan kosong.
- [[^output|Text]], [[^output|Function]], dan [[^output|Error]] tidak keluar bersamaan. Hanya satu yang meneruskan aliran sesuai hasil permintaan.
- [[^output|Function]] hanya dapat keluar bila [[^input|Tools]] diisi.
- [[^output|Error]] hanya keluar bila OpenAI mengembalikan respons error, termasuk ketika [[^input|Input]] dan [[^input|Messages]] sama-sama kosong.
- OpenAI 4 Block tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|syarat Flow Block diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan|Flow Block Modular]]
- [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]
- [[Docs/Modul Logic/Flow/Flow Activity]]
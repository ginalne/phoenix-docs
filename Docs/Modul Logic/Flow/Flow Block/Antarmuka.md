---
    status: release
    title: "Antarmuka Flow Block"
    description: 
    pageDecoration:
      tree:
        priority: 7
---
# Antarmuka Flow Block

![[Docs/Modul Logic/Flow/Flow Block/flow-block-anatomy.png]]
Bagian-bagian Flow Block ditempatkan pada posisi berikut:

| Bagian | Posisi pada block |
| --- | --- |
| [[#Trigger]] | Di sebelah kiri judul block |
| [[#Control]] | Di badan block |
| [[#Input]] | Di sisi kiri, di bawah judul block |
| [[#Output]] | Di sisi kanan block |

Tidak semua jenis Flow Block memiliki keempat bagian ini. Variasinya dijelaskan di [[#Variasi Antar Jenis Flow Block]].

## Trigger

[[#Trigger]] adalah Input yang berada di sebelah kiri judul block. Fungsinya sebagai syarat agar block dijalankan.

- Trigger dapat menerima koneksi dari banyak [[#Output]] sekaligus. Syarat terpenuhi bila setidaknya satu koneksi sudah berisi data, artinya block sebelumnya sudah tereksekusi.
- Trigger yang tidak memiliki koneksi dianggap selalu aktif.

> **note** Trigger dan tombol Trigger
> Trigger adalah bagian dari Flow Block yang menjadi syarat eksekusi. Tombol [[^button/empty|Trigger]] pada [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]] adalah [[#Control]] dan tidak sama dengan Trigger ini.

## Input

[[#Input]] adalah masukan data ke block untuk diproses lebih lanjut.

- Input yang tidak terhubung menampilkan field isian sehingga nilainya dapat diisi langsung. Field ini hilang ketika Input terhubung dari [[#Output]] block lain.
- Bila satu Input menerima banyak koneksi, seluruh data dari koneksi tersebut dibaca sebagai [[Docs/Tipe Data/Array]] dalam proses block.
- Bila salah satu koneksi bersifat rekursif, yaitu ketika ditelusuri mundur akan kembali ke block yang sama, Input dibaca sebagai satu data dari aliran terakhir dan koneksi lainnya diabaikan.
- Block dapat berjalan walaupun Input-nya dibiarkan kosong bergantung pada aturan block itu sendiri. Jika Input wajib diisi, kondisi kosong menghasilkan error pada [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]].

## Control

[[#Control]] adalah antarmuka interaktif di badan block yang dapat dioperasikan langsung di Blueprint. Control dapat memengaruhi proses yang terjadi pada Flow Block, atau memicu [[Docs/Modul Logic/Flow/Flow Activity|Activity]] baru.

- Saat ini Control yang tersedia berupa tombol [[^button/empty|Trigger]], misalnya pada [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]] untuk menjalankan Flow secara manual.
- Tidak semua Flow Block memiliki Control.

## Output

[[#Output]] adalah keluaran block yang dapat dihubungkan ke [[#Input]] atau [[#Trigger]] block lain.

- Setiap Output hanya dapat terhubung dengan satu Input atau Trigger block lain. Aturan lengkapnya ada di [[#Aturan Koneksi]].
- Tipe data Output dapat bervariasi, dan kecocokannya dengan Input diperiksa saat Flow berjalan.

Tidak semua Output akan menghasilkan nilai yang meneruskan aliran Flow ke block lain. Contohnya [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Add Variable|Add Variable Block]] yang tidak akan meneruskan aliran ke output [[^output|Name Conflict]] jika [[Docs/Tipe Data/Variable]] berhasil dibuat, artinya apapun Block lain yang menerima/terhubung dengan output ini tidak akan tereksekusi dalam Flow.

## Variasi Antar Jenis Flow Block

Setiap jenis Flow Block memiliki variasi [[#Trigger]], [[#Input]], [[#Control]], dan [[#Output]] masing-masing. Ada jenis yang tidak memiliki Control, Input, atau Output. Contohnya Flow Block Event yang tidak memiliki Trigger maupun Input.

Pada halaman setiap jenis Flow Block, hanya variasi yang khas bagi block itu yang dijelaskan. Prinsip umum pada halaman ini, yaitu [[#Aturan Koneksi]] dan [[#Syarat Flow Block Diproses]], tidak diulang di sana.


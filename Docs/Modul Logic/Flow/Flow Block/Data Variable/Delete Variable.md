---
status: draft
title: Delete Variable
description: Flow Block untuk menghapus Variable Data yang ditunjuk, dengan opsi hapus paksa.
pageDecoration:
  icon: zap
  tree:
    priority: 2
---
# Delete Variable

>**note** Delete Variable merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Delete Variable adalah [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] untuk menghapus [[Docs/Modul Data/Variable/Apa itu Variable|Variable Data]] dari dalam Flow. Block ini memiliki dua input di sisi kiri dan dua output di sisi kanan yang memberi tahu Anda apakah penghapusan berhasil.

![[Docs/Modul Logic/Flow/Flow Block/Data Variable/delete-variable-block-flow.png|Flow Block Delete Variable dengan dua input dan dua output]]

>**danger** Penghapusan tidak dapat dikembalikan
> Variable Data yang dihapus lewat Delete Variable tidak dapat dikembalikan. Pastikan [[^field|Variable]] menunjuk Variable Data yang benar sebelum Flow dijalankan.

## Input dan Output

Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Variable]] | [[Docs/Tipe Data/Variable]] | Variable Data yang akan dihapus. Isi dengan Name Variable Data (alias) atau hubungkan dari output block lain, misalnya [[^output|Variable]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]. |
| [[^field|Force]] | [[Docs/Tipe Data/Boolean]] | Isi [[^value/boolean/true]] bila Variable Data harus dihapus secara paksa, termasuk bila sudah memiliki relasi dan histori. Bila tidak diisi, tampil [[^value/empty]] dan penghapusan berjalan tanpa paksaan. |

### Output

| Output | Tipe Data | Fungsi |
| ------ | --------- | ------ |
| [[^output|Succeed]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila Variable Data berhasil dihapus. Bernilai [[^value/empty]] bila gagal. |
| [[^output|Error]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila penghapusan gagal. Bernilai [[^value/empty]] bila berhasil. |

## Cara Kerja

1. Block menerima Variable Data dari [[^field|Variable]] dan nilai [[^field|Force]].
2. Jika [[^field|Force]] tidak aktif, block menghapus Variable Data hanya bila tidak ada relasi dan histori yang terdampak.
3. Jika [[^field|Force]] bernilai [[^value/boolean/true]], block menghapus Variable Data apa pun kondisi relasi dan historinya.
4. Block mengirim hasilnya lewat [[^output|Succeed]] dan [[^output|Error]]. Salah satunya bernilai [[^value/boolean/true]], sedangkan yang lain bernilai [[^value/empty]].

>**warning** Hapus paksa berdampak pada relasi dan histori
> Bila [[^field|Force]] bernilai [[^value/boolean/true]], Variable Data dihapus meskipun sudah dipakai. Relasi dengan komponen lain yang merujuk Variable Data tersebut terputus, dan histori yang sudah ada ikut terdampak. Aktifkan [[^field|Force]] hanya bila Anda memahami dampak ini.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Penghapusan lewat Delete Variable tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Variable Event|Variable Event Block]] dengan event [[^value/string|delete]], sehingga tidak ada Flow yang berjalan karena penghapusan ini.

## Contoh Penggunaan

| Kondisi | [[^field|Force]] | [[^output|Succeed]] | [[^output|Error]] |
| ------- | ---------------- | ------------------- | ----------------- |
| Variable Data valid dan tidak memiliki relasi maupun histori | [[^value/empty]] | [[^value/boolean/true]] | [[^value/empty]] |
| Variable Data valid, tetapi memiliki relasi atau histori | [[^value/empty]] | [[^value/empty]] | [[^value/boolean/true]] |
| Variable Data valid, memiliki relasi atau histori | [[^value/boolean/true]] | [[^value/boolean/true]] | [[^value/empty]] |
| [[^field|Variable]] kosong atau tidak valid | [[^value/empty]] atau [[^value/boolean/true]] | [[^value/empty]] | [[^value/boolean/true]] |

Hubungkan [[^output|Error]] ke block yang menangani kegagalan, misalnya [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]], agar Flow dapat memberi tahu pengguna bahwa Variable Data gagal dihapus.

## Praktik Terbaik

- **Ambil Variable Data dengan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]** terlebih dahulu, lalu hubungkan [[^output|Variable]] ke [[^field|Variable]] agar Anda yakin menghapus Variable Data yang tepat.
- **Biarkan [[^field|Force]] kosong secara bawaan.** Aktifkan hanya untuk kasus yang memang membutuhkan hapus paksa.
- **Periksa [[^output|Succeed]] dan [[^output|Error]]** sebelum melanjutkan alur yang bergantung pada hilangnya Variable Data.

## Batasan dan Catatan

- Delete Variable adalah block non-Event, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- [[^field|Force]] tidak dapat mengembalikan relasi dan histori yang terputus setelah penghapusan.
- Satu eksekusi menghapus satu Variable Data.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]]
- [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]
- [[Docs/Tipe Data/Variable]]

<!--
  * [TODO] Letakkan screenshot block Delete Variable sebagai `delete-variable-block-flow.png` di folder `Docs/Modul Logic/Flow/Flow Block/Data Variable/`. Anotasi yang disarankan: nomor 1 dan 2 untuk input Variable dan Force, nomor 3 dan 4 untuk output Succeed dan Error.
  * [TODO] Konfirmasi perilaku Force: (a) Force kosong dianggap false, (b) tanpa Force penghapusan gagal bila Variable Data memiliki relasi atau histori, (c) apa persisnya yang dimaksud "relasi" dan "histori" (misalnya Flow Block yang merujuk, riwayat Variable Event), dan apa yang terjadi pada keduanya saat hapus paksa.
  * [TODO] Konfirmasi output Error: saya tulis bertipe Boolean dengan nilai true saat gagal, mengikuti kalimat "begitu sebaliknya". Bila Error ternyata membawa pesan kesalahan, tipe datanya perlu diganti.
  * [TODO] Baris tabel Contoh Penggunaan untuk Force kosong pada Variable Data yang memiliki relasi atau histori, serta baris Variable kosong atau tidak valid, adalah asumsi saya.
  * [TODO] Callout danger tentang penghapusan yang tidak dapat dikembalikan saya ambil dari halaman komponen Variable. Konfirmasi bahwa berlaku sama untuk penghapusan lewat Flow.
-->

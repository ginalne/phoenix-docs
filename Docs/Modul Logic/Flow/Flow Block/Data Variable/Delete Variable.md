---
    status: draft
    title: Delete Variable
    description: Flow Block untuk menghapus Variable Data yang ditunjuk, dengan opsi hapus paksa.
    pageDecoration:
      icon: trash
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
| [[^field|Variable]] | [[Docs/Tipe Data/Variable]] | Variable Data yang akan dihapus. Isi dengan Variable Data atau hubungkan dari output block lain, misalnya [[^output|Variable]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]. |
| [[^field|Force]] | [[Docs/Tipe Data/Boolean]] | Isi [[^value/boolean/true]] bila Variable Data yang sudah digunakan tetap harus dihapus (hapus paksa). Bila tidak diisi, tampil [[^value/empty]] dan penghapusan berjalan tanpa paksaan. |

### Output

| Output | Tipe Data | Fungsi |
| ------ | --------- | ------ |
| [[^output|Succeed]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila Variable Data berhasil dihapus. Bernilai [[^value/boolean/false]] bila gagal. |
| [[^output|Error]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila penghapusan gagal. Bernilai [[^value/boolean/false]] bila berhasil. |

## Cara Kerja

1. Block menerima Variable Data dari [[^field|Variable]] dan nilai [[^field|Force]].
2. Jika [[^field|Force]] tidak aktif, block hanya menghapus Variable Data yang belum digunakan.
3. Jika [[^field|Force]] bernilai [[^value/boolean/true]], block menghapus Variable Data meskipun sudah digunakan.
4. Block mengirim hasilnya lewat [[^output|Succeed]] dan [[^output|Error]]. Salah satunya bernilai [[^value/boolean/true]], sedangkan yang lain bernilai [[^value/boolean/false]].

Variable Data dianggap sudah digunakan bila sedang dipakai pada Flow atau data lain, atau bila riwayat [[Docs/Modul Logic/Flow/Flow Activity|activity]] mencatat bahwa Variable Data tersebut pernah dipakai.

>**warning** Hapus paksa berdampak pada Variable Data yang sudah digunakan
> Bila [[^field|Force]] bernilai [[^value/boolean/true]], Variable Data dihapus meskipun masih dipakai pada Flow atau data lain. Flow atau data lain yang memakai Variable Data tersebut terdampak, begitu juga riwayat activity yang mencatat penggunaannya. Aktifkan [[^field|Force]] hanya bila Anda memahami dampak ini.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Penghapusan lewat Delete Variable tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Variable Event|Variable Event Block]] dengan event [[^value/string|delete]], sehingga tidak ada Flow yang berjalan karena penghapusan ini.

## Contoh Penggunaan

| Kondisi | [[^field|Force]] | [[^output|Succeed]] | [[^output|Error]] |
| ------- | ---------------- | ------------------- | ----------------- |
| Variable Data belum digunakan | [[^value/empty]] | [[^value/boolean/true]] | [[^value/boolean/false]] |
| Variable Data sudah digunakan | [[^value/empty]] | [[^value/boolean/false]] | [[^value/boolean/true]] |
| Variable Data sudah digunakan | [[^value/boolean/true]] | [[^value/boolean/true]] | [[^value/boolean/false]] |
| [[^field|Variable]] dibiarkan kosong | Berapa pun | [[^value/boolean/false]] | [[^value/boolean/true]] |

Hubungkan [[^output|Error]] ke block yang menangani kegagalan, misalnya [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]], agar Flow dapat memberi tahu pengguna bahwa Variable Data gagal dihapus.

## Praktik Terbaik

- **Ambil Variable Data dengan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]** terlebih dahulu, lalu hubungkan [[^output|Variable]] ke [[^field|Variable]] agar Anda yakin menghapus Variable Data yang tepat.
- **Biarkan [[^field|Force]] kosong secara bawaan.** Aktifkan hanya untuk kasus yang memang membutuhkan hapus paksa.
- **Periksa [[^output|Succeed]] dan [[^output|Error]]** sebelum melanjutkan alur yang bergantung pada hilangnya Variable Data.

## Batasan dan Catatan

- Delete Variable adalah block non-Event, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- Hapus paksa tidak dapat dibatalkan, termasuk dampaknya pada Flow, data lain, dan riwayat activity.
- Satu eksekusi menghapus satu Variable Data.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]]
- [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]
- [[Docs/Tipe Data/Variable]]


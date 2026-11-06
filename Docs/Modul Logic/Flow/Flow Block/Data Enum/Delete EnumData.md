---
    status: draft
    title: Delete EnumData
    description: Flow Block untuk menghapus EnumData dari sebuah Enum, dengan opsi hapus paksa.
    pageDecoration:
      icon: trash
      tree:
        priority: 6
---

# Delete EnumData

>**note** Delete EnumData merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]] di Phoenix.

Delete EnumData adalah Flow Block yang menghapus [[Docs/Tipe Data/EnumData]] yang Anda tentukan saat Flow berjalan. Bila EnumData sudah digunakan, penghapusan hanya berhasil jika [[^field|Force]] bernilai [[^value/boolean/true]]. Hasilnya dilaporkan lewat output [[^output|Succeed]] dan [[^output|Error]].

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/delete-enumdata-block-flow.png|Flow Block Delete EnumData dengan dua input dan dua output]]

<!--
  * [DONE] Letakkan gambar `delete-enumdata-block-flow.png` (potongan block Delete EnumData dari Blueprint). Anotasi yang disarankan: (1) input EnumData, (2) input Force, (3) output Succeed, (4) output Error.
-->

## Input dan Output

Delete EnumData memiliki dua input di sisi kiri dan dua output di sisi kanan. Block ini tidak memiliki Control.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|EnumData]] | [[Docs/Tipe Data/EnumData]] | EnumData target yang akan dihapus. Isi dengan EnumData atau hubungkan dari output block lain, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]. |
| [[^field|Force]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] untuk menghapus paksa EnumData yang sudah digunakan. [[^value/boolean/false]] hanya menghapus EnumData yang belum digunakan. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|Succeed]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila EnumData berhasil dihapus, tidak ada output bila gagal dihapus. |
| [[^output|Error]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila penghapusan gagal, tidak ada output bila berhasil. |

## Cara Kerja

EnumData dianggap sudah digunakan bila sedang dipakai pada Flow atau data lain, atau tercatat di riwayat activity. Saat dieksekusi, Delete EnumData bekerja sebagai berikut:

1. Bila EnumData belum digunakan, EnumData langsung dihapus, apa pun nilai [[^field|Force]].
2. Bila EnumData sudah digunakan dan [[^field|Force]] bernilai [[^value/boolean/false]], EnumData tidak dihapus.
3. Bila EnumData sudah digunakan dan [[^field|Force]] bernilai [[^value/boolean/true]], EnumData dihapus paksa.
4. Setelah penghapusan berhasil, [[^output|Succeed]] bernilai [[^value/boolean/true]] dan [[^output|Error]] bernilai [[^value/boolean/false]]. Bila gagal, nilainya sebaliknya.

>**danger** Penghapusan tidak dapat dikembalikan
> EnumData yang sudah dihapus tidak dapat dipulihkan. Pastikan target pada input [[^field|EnumData]] sudah benar sebelum menjalankan Flow.

>**warning** Hapus paksa berdampak pada data yang sudah menggunakan EnumData
> Saat [[^field|Force]] bernilai [[^value/boolean/true]], EnumData tetap dihapus walaupun sudah digunakan. Relasi dan riwayat yang sudah ada akan terdampak. Gunakan hanya bila Anda memahami data yang memakai EnumData tersebut.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> EnumData yang dihapus oleh Delete EnumData tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event|Enum Data Event Block]] dengan Event [[^value/string|delete]].

<!--
  * [DONE] Konfirmasi dampak hapus paksa: apa yang terjadi pada relasi (field atau data yang memakai EnumData) dan riwayat activity. Isi callout warning di atas masih draf mengikuti penjelasan penulis.
  * [DONE] Konfirmasi dampak penghapusan EnumData yang masih dipakai komponen lain bila Force bernilai false (diasumsikan tidak dihapus).
  * [DONE] Konfirmasi apakah callout "tidak memicu Flow kembali" berlaku untuk semua Flow atau hanya Flow yang sama.
-->

## Contoh Penggunaan

Contoh berikut memakai EnumData [[^value/enumdata|Menunggu]] pada Enum status pesanan.

| Kondisi | [[^output|Succeed]] | [[^output|Error]] | Status | Hasil |
| ------- | ------------------- | ----------------- | ----- | ----- |
| EnumData belum digunakan, [[^field|Force]] bernilai [[^value/boolean/false]] | [[^value/boolean/true]] | - | [[^flowstate/Succeed]]  | EnumData dihapus. |
| EnumData belum digunakan, [[^field|Force]] bernilai [[^value/boolean/true]] | [[^value/boolean/true]] | - | [[^flowstate/Succeed]] | EnumData dihapus. |
| EnumData sudah digunakan, [[^field|Force]] bernilai [[^value/boolean/false]] | - | [[^value/boolean/true]] | [[^flowstate/Error]] | EnumData tidak dihapus. |
| EnumData sudah digunakan, [[^field|Force]] bernilai [[^value/boolean/true]] | [[^value/boolean/true]] | - | [[^flowstate/Succeed]] | EnumData dihapus paksa. |
| [[^field|Force]] dibiarkan kosong | | | | Mengikuti contoh pada baris [[^field|Force]] bernilai [[^value/boolean/false]] |
| [[^field|EnumData]] dibiarkan kosong | - | [[^value/boolean/true]] | [[^flowstate/Error]] | Tidak ada yang dihapus. |

Status [[^flowstate/Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].
<!--
  * [DONE] Konfirmasi perilaku Force yang dibiarkan kosong (screenshot menampilkan "(Empty)"), diasumsikan sama dengan false.
  * [TODO] Konfirmasi perilaku EnumData yang dibiarkan kosong: apakah output Succeed false dan Error true, atau terjadi error yang dilaporkan di Flow Activity.
    Jawaban: Ya tetap ada  tampil error di Flow Activity
  * [DONE] Nama contoh (Enum status pesanan dan EnumData Menunggu) bersifat generik. Sesuaikan bila perlu.
-->

## Praktik Terbaik

- **Biarkan [[^field|Force]] bernilai [[^value/boolean/false]] sebagai pilihan awal.** Aktifkan [[^value/boolean/true]] hanya untuk EnumData yang memang sudah Anda pastikan aman dihapus.
- **Periksa [[^output|Succeed]] dan [[^output|Error]] setelah penghapusan.** Hubungkan keduanya ke [[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If|If Operator Block]] agar Flow dapat bercabang saat penghapusan gagal.
- **Ambil target lewat [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]].** Cara ini menghindari salah memilih EnumData saat nama diketahui tetapi EnumData-nya belum.

## Batasan dan Catatan

- Delete EnumData adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Satu eksekusi hanya menghapus satu EnumData.
- Output [[^output|Succeed]] dan [[^output|Error]] selalu bernilai [[^value/boolean/true]] atau [[^value/boolean/false]], tidak pernah [[^value/empty]].
- EnumData yang dihapus tidak dapat dikembalikan, baik dengan maupun tanpa [[^field|Force]].

<!--
  * [DONE] Halaman baru yang ditautkan dan perlu dibuat: `Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter`, `Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event`, `Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If`, dan `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`.
-->

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Add EnumData|Add EnumData Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Tipe Data/EnumData]]
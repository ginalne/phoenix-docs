---
    status: release
    title: "Elemen dalam Form"
    description: 
    pageDecoration:
      tree:
        priority: 6
---
# Elemen dalam Form

Elemen adalah satu objek penyusun isi Form. Setiap bagian yang Anda lihat di Form, mulai dari judul, kolom isian, hingga tabel, adalah sebuah Elemen. Anda menyusun Form dengan menambahkan Elemen, mengaturnya, lalu mengikatnya ke data lewat [[Docs/Modul Interface/Form/Elemen Form/Binding]].

Elemen dikelompokkan dalam tiga kategori:

| Kategori | Fungsi | Elemen |
| --- | --- | --- |
| [[#Elemen Layout|Layout]] | Menjadi templat tempat Elemen lain diletakkan. | [[Docs/Modul Interface/Form/Layout/Card/Penjelasan|Card]], [[Docs/Modul Interface/Form/Layout/Full/Penjelasan|Full]], [[Docs/Modul Interface/Form/Layout/Split/Penjelasan|Split]], [[Docs/Modul Interface/Form/Layout/Accordion/Penjelasan|Accordion]] |
| [[#Elemen Display|Display]] | Menampilkan informasi. | [[Docs/Modul Interface/Form/Display/Text/Penjelasan|Text]], [[Docs/Modul Interface/Form/Display/Table/Penjelasan|Table]], [[Docs/Modul Interface/Form/Display/Tooltip/Penjelasan|Tooltip]], [[Docs/Modul Interface/Form/Display/Qr/Penjelasan|Qr]], [[Docs/Modul Interface/Form/Display/Chrono/Penjelasan|Chrono]] |
| [[#Elemen Input|Input]] | Mengisi atau menampilkan informasi yang berlaku pada Binding. | [[Docs/Modul Interface/Form/Input/Basic/Penjelasan|Basic]], [[Docs/Modul Interface/Form/Input/Quiz/Penjelasan|Quiz]], [[Docs/Modul Interface/Form/Input/Table/Penjelasan|Table]], [[Docs/Modul Interface/Form/Input/List/Penjelasan|List]] |

Penjelasan keunikan masing-masing Elemen ada di halaman Elemen tersebut.

## Mengelola Elemen

Berikut adalah halaman yang menjelaskan cara untuk mengelolanya:
1. [[Docs/Modul Interface/Form/Elemen Form/Menambahkan]] Elemen.
3. [[Docs/Modul Interface/Form/Elemen Form/Menghapus]] Elemen.
2. [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi]] properti dan atirbut dalam Elemen seperti [[^field|Binding]], [[^field|State]], [[^field|Validators]],[[^field|Attributes]].
3. [[Docs/Modul Interface/Form/Elemen Form/Binding|Memahami Binding]] dalam Elemen.
4. [[Docs/Modul Interface/Form/State|Memahami State]] dalam Elemen.
4. [[Docs/Modul Interface/Form/Validator|Memahami Validator]] dalam Elemen.

## Menu Konteks Elemen

Klik kanan pada Elemen untuk membuka menu konteks.

| Menu | Fungsi |
| --- | --- |
| [[^field/copy|Copy Layout Style]] | Menyalin konfigurasi *styling* Elemen. |
| [[^field/paste|Paste Layout Style]] | Menerapkan salinan konfigurasi *styling* Elemen. |
| [[^field/up|Move Back]] | Memindahkan posisi dengan Elemen sebelumnya (tidak berpengaruh jika Elemen berada di barisan pertama). |
| [[^field/down|Move Next]] | Memindahkan posisi dengan Elemen setelahnya (tidak berpengaruh jika Elemen berada di barisan akhir). |

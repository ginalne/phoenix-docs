---
    status: release
    title: Input Quiz (Elemen Input)
    description: Input Quiz adalah Elemen Input pada Form untuk mengisi satu Column dengan memilih satu jawaban dari opsi yang dibuat, ditampilkan sebagai radio button.
    pageDecoration:
      tree:
        priority: 0
---
# Form Input : Input Quiz

>**note** Input Quiz merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Input|Elemen Input]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Input Quiz adalah Elemen Input yang dapat digunakan untuk mengisi satu [[Docs/Tipe Data/Column]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]] dengan memilih satu jawaban dari beberapa opsi. Opsi tampil sebagai radio button, sehingga pengisi hanya dapat memilih satu jawaban.

Setiap opsi memiliki teks jawaban dan value. Value dari opsi yang dipilih itulah yang disimpan ke Column. Anda mengatur opsi langsung di halaman kerja tanpa menulis logika tambahan.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara menghapus Elemen ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Input Quiz.

## Menambahkan Input Quiz

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]]
2. Klik [[^field|Type something here to add...]] pada Layout
3. Pilih Input Quiz dari daftar, atau ketik untuk mencarinya
4. Pilih [[^field|Column]] pada [[^field|Binding]]
5. Tambahkan opsi. Lihat [[#Mengelola Opsi]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengelola Opsi

Opsi diatur langsung pada Input Quiz di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]]. Setiap baris opsi berisi teks jawaban dan value.

| Aksi | Cara |
| --- | --- |
| Menambah opsi | Klik tombol [[^button/add|Add Option]]. |
| Mengisi jawaban | Isi teks jawaban pada baris opsi. Teks ini yang dilihat pengisi. |
| Mengikat opsi ke value | Isi value pada baris opsi. Value bebas diisi, asalkan sesuai [[^field|Format Type]]. |
| Menghapus opsi | Klik tombol [[^button/delete|Delete]] pada baris opsi. |

## Mengonfigurasi Input Quiz

Klik kiri Input Quiz di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]], [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Layout Panel]]. Label Column (berikon kolom) juga tampil di atas Input Quiz sebagai informasi Binding.

### Header Toolbar

![[Docs/Modul Interface/Form/Elemen Form/Input/toolbar-form-quiz.png]]
Selain tombol [[^button/delete|Remove]], Header Toolbar Input Quiz memiliki pengaturan teks untuk Label: ukuran font, *bold*, *italic*, *underline*, serta rata kiri, tengah, dan kanan. Pengaturan ini berlaku pada teks Label yang sedang dipilih.

### Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/Input/properties-form-quiz.png]]
#### Binding

| Bagian | Fungsi |
| --- | --- |
| [[^field|Table]] | Table sumber data dari Layout. |
| [[^field|Column]] | Column tempat value opsi yang dipilih disimpan. |

#### State

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan Input Quiz. |
| [[^field|Enable]] | Mengaktifkan Binding. Jika [[^value/boolean/false]], Binding tidak aktif dan isian tidak berpengaruh ke Row. |
| [[^field|Readonly]] | Jika [[^value/boolean/true]], isi Input Quiz tidak dapat diubah oleh pengisi. |

#### Validator

| Validator | Fungsi |
| --- | --- |
| [[^field|Required]] | Pengisi wajib mengisi field ini agar dapat mengirim Form. |

>**note** Kapan Required tidak berlaku
> [[^field|Required]] tidak berlaku jika [[^field|Visible]] atau [[^field|Enable]] bernilai [[^value/boolean/false]].

Saat ini [[^field|Required]] adalah satu-satunya validator.

#### Attributes

| Atribut | Fungsi |
| --- | --- |
| [[^field|Label]] | Teks judul Quiz yang tampil di atas pilihan. |
| [[^field|Format Type]] | Format hasil isian yang diharapkan, misalnya `String` untuk teks. Value setiap opsi mengikuti format ini. |
| [[^field|Default Value]] | Opsi yang sudah terpilih saat pengisi baru (publik) membuka Form. Dipilih dari daftar jawaban opsi yang sudah dibuat. |

#### Parent

Menampilkan Layout tempat Input Quiz berada.

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* Input Quiz dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Layout Panel]].

## Menghapus Input Quiz

Langkah menghapus Input Quiz sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Input Quiz
> Menghapus Input Quiz akan menghapus Quiz beserta seluruh opsinya. Aksi tidak bisa dikembalikan.
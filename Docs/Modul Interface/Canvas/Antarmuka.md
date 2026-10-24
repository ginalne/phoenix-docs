---
    status: release
    title: "Antarmuka Canvas"
    description: Penjelasan antarmuka di halaman kerja komponen Canvas
    pageDecoration:
      tree:
        priority: 0
    tags:
      draft
---
# Antarmuka Canvas

![[Docs/Modul Interface/Canvas/interface-canvas.png]]
Halaman kerja Canvas terdiri dari bilah navigasi di bagian atas dan area kerja di bagian bawah. Bilah navigasi memuat judul Canvas (ikon Canvas dan Header Name) di sisi kiri serta tombol aksi di sisi kanan. Area kerja menampilkan isi Canvas, atau pesan Canvas kosong bila belum ada Layout dan widget. Tidak ada perbedaan signifikan antara tampilan desktop dan mobile.

### Bilah navigasi Canvas terdiri dari:

| Tombol                              | Fungsi                                                                                                                                         |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| [[^button/edit|Edit]]              | Mengubah atribut Canvas (Name dan Description), lalu klik [[^button|Update]]. Lihat [[#Mengubah Canvas]].                                      |
| [[^button/publish|Publish]]        | Membuka konfigurasi publikasi Canvas. Lihat [[#Mempublikasikan Canvas]].                                                                       |
| [[^field|mode]]                    | Toggle untuk berpindah antara [[^value/radio|View]] dan [[^value/radio|Edit]]. Lihat [[#Mode View dan Edit]].                                |
| [[^button/save|Save]]              | Menyimpan perubahan. Aktif ketika ada perubahan. Lihat [[#Menyimpan Perubahan]].                                                               |
| [[^button/refresh|Refresh]]        | Memuat ulang tampilan. Lihat [[#Menyegarkan Canvas]].                                                                                          |

### Mode View dan Edit

Canvas memiliki dua mode yang dapat dipilih melalui toggle [[^field|mode]]:

| Mode                          | Fungsi                                                                                                                                                   |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[^value/radio|View]]        | Mode read only. Isi Canvas hanya dapat dilihat dan tidak dapat diubah. Canvas kosong menampilkan [[^field|Read Only]].                                  |
| [[^value/radio|Edit]]        | Mode untuk menyusun dan mengubah isi Canvas. Canvas kosong menampilkan [[^field|Type something here to add...]] untuk menambahkan Layout atau widget. |

Pindah ke Edit Mode dapat dilakukan jika salah satu Data Access Canvas (Add, Update, atau Delete) pada [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] bernilai [[^value/boolean/allow]]. Jika semuanya [[^value/boolean/disallow]], toggle tidak dapat dipindahkan dan Canvas tetap berada di View Mode. Lihat [[#Hak Akses Canvas]].

![[Docs/Modul Interface/Canvas/edit-canvas.png]]

### Menyimpan Perubahan

Tombol [[^button/save|Save]] aktif ketika ada perubahan pada Canvas. Anda dapat menyimpan secara manual dengan klik [[^button/save|Save]], atau menunggu sekitar 3 detik hingga perubahan tersimpan otomatis (*auto save*).

### Interaksi Antarmuka Canvas

| Fungsi                                                      | Aksi                                                                                                               |
| ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Berpindah mode                                              | Klik toggle [[^field|mode]] pada bilah navigasi.                                                                  |
| Menambahkan Layout atau widget                              | Pada Edit Mode, klik [[^field|Type something here to add...]], ketik perintah berawalan `/`, lalu pilih dari dropdown. |
| Memfokuskan widget                                          | Pada Edit Mode, klik kiri widget.                                                                                  |
| Menampilkan [[#Header Toolbar dan Design Toolbar|header toolbar dan design toolbar]] | Klik kiri (*select*) widget. Setiap aksi select pada widget menampilkan keduanya.        |
| Memindahkan widget                                          | Gunakan ikon pegangan ⋮⋮ pada header toolbar untuk memindahkan widget ke posisi atau Layout lain.                  |
| Menghapus widget                                            | Klik [[^button/delete|Remove]] pada header toolbar.                                                               |
| Menyimpan perubahan                                         | Klik [[^button/save|Save]] atau tunggu sekitar 3 detik.                                                           |

## Membangun Canvas

### Menambahkan Layout dan Widget

1. Pindah ke Edit Mode melalui toggle [[^field|mode]]
2. Klik [[^field|Type something here to add...]]
3. Ketik perintah berawalan `/` untuk mencari yang ingin ditambahkan
4. Pilih Layout, Template, atau widget dari dropdown

Perintah yang ditampilkan sebagai contoh pada Canvas kosong:

| Perintah    | Fungsi                          |
| ----------- | ------------------------------- |
| `/layout`   | Mencari Layout                  |
| `/widget`   | Mencari Widget                  |
| `/chart`    | Mencari chart                   |
| `/template` | Mencari Template                |
| `/t`        | Tambah Title                    |
| `/s`        | Tambah Subtitle                 |
| `/p`        | Tambah Paragraph                |
| `/vertical` | Tambah Layout mode Vertical     |
| `/horizontal` | Tambah Layout mode Horizontal |
| `/text`     | Tambah Teks Kosong              |
| `/table`    | Tamabh Tabel Kosong             |

### Header Toolbar dan Design Toolbar

Pada Edit Mode, klik kiri layout atau widget untuk memfokuskannya dan otomatis menampilkan dua toolbar:

| Toolbar                | Fungsi                                                                                                                              |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Header Toolbar         | Pintasan aksi widget, misalnya memilih data sumber, mengatur Query, memindahkan, dan menghapus widget.                              |
| Design Toolbar         | Pengaturan tata letak dan tampilan widget.                                                                                          |

>**note** Isi toolbar berbeda pada layout dan setiap widget
> Panel tata letak sama di semua widget. Header toolbar dan panel tampilan widget bersifat unik untuk masing-masing widget. Keunikan setiap widget dijelaskan di halaman widget masing-masing pada [[#Widget Canvas]].

---
    status: release
    title: "Apa itu Variable"
    description: Variable adalah komponen bawaan Pro yang menjadi satu sumber data universal berisi konstanta dan nilai konfigurasi yang dapat dipakai semua komponen.
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="0 0 52 52"><path
    d="M49.1,7.7c-0.3-0.3-0.6-0.4-1-0.4l0,0c-3.8-0.2-7.7,0.1-11.5,0.2L23.1,7.5c-4.1,0-7.4,0.9-10.5,3.7  c-2,1.8-3.9,4.4-5.4,6.7C7.1,18.2,7,18.4,7,18.8c0,0.8,0.7,1.5,1.5,1.5c0.9,0,1.1-0.6,1.5-1.2c0.4-0.7,0.9-1.3,1.5-1.8  c2.1-1.9,4.9-3,7.7-2.7c-2.4,6.6-5.7,14.2-10.5,19.4c-2,2.2-5.4,4.4-6.1,7.4c-0.8,3.1,2.4,3.9,4.7,3c3-1.2,4.9-4.3,6.4-7  c1.9-3.3,3.6-6.8,5-10.3c1.5-3.5,2.9-6.9,4.4-10.4c0.9-2.1,1.1-2.1,3.3-2.1h5.9c-2.2,4.8-4.3,9.7-6.2,14.6  c-1.5,3.7-4.2,9.2-2.3,13.2c1.9,4,7.2,2.5,10.1,0.5c2.9-2.1,4.9-5.4,6.5-8.6c0.3-0.6,0.6-1.2,0.4-1.9c-0.2-0.6-0.8-0.9-1.4-0.9  c-1.4,0-1.6,1.6-2.1,2.6c-0.8,1.7-2.6,3.2-4.5,2.9c-4.4-0.6-0.5-8.6,0.3-10.7c0.8-2.2,1.7-4.4,2.7-6.5c0.5-1.2,1-2.5,1.7-3.7  c0.8-1.5,0.8-1.5,2.6-1.6c1.5-0.1,5.9,0.7,7.2-0.1c1.1-0.7,1.7-3.3,2.2-5.2l0,0C49.6,8.6,49.4,8.1,49.1,7.7z" /></svg>'
      tree:
        priority: 4
---
# Apa itu Variable?

>**note** _Variable_ merupakan salah satu komponen dalam modul [[Docs/Modul Data/Pengenalan|Data]] di Phoenix.

Variable adalah komponen yang digunakan untuk mengelola Data Variable di dalam [[Docs/Inisialisasi/Apa itu Pro|Pro]]. [[Docs/Tipe Data/Variable|Variable Data]] bersifat unik sehingga data yang Anda simpan dapat menjadi sumber kebenaran dan dipakai di mana saja.

Komponen ini sudah tersedia sejak [[Docs/Inisialisasi/Apa itu Pro|Pro]] dimulai. 

## Mengapa Menggunakan Komponen Variable?

- **Pintu untuk mengelola Variable Data.** Variable Data adalah tipe data khusus didalam Phoenix dan semua komponen mengenalnya, namun hanya ada satu tempat untuk mengelolanya yaitu komponen ini.
- **Satu dan selalu ada.** Komponen Variable hanya ada satu untuk seluruh ekosistem dalam Pro, tidak dapat diduplikasi dan dihapus, sehingga menjadi *source of truth* yang dirujuk semua komponen.
- **Konstanta untuk tim.** Anda membuat data sekali, lalu komponen lain cukup merujuk ke namanya. Tidak ada lagi salinan nilai yang tersebar dan berisiko tidak sinkron.
- **Nilainya bisa tersamarkan.** Jika ada anggota yang tidak memiliki akses komponen ini, maka anggota tersebut tidak akan dapat mengetahui [[^field|Value]] yang disimpan walaupun tetap dapat menggunakannya untuk otomasi atau integrasi.

## Konsep Utama

| Istilah | Penjelasan |
| --- | --- |
| [[Docs/Tipe Data/Variable|Variable Data]] | Data dalam komponen Variable. |
| [[#Cara Kerja Variable|Alias]] | Istilah dari komponen lain yang merujuk ke isi [[^field|Name]] dari Variable Data. |

## Cara Kerja

Penjelasan cara kerja Enum lihat selengkap nya di [[Docs/Modul Data/Enum/Cara Kerja|Cara Kerja Enum]].

## Mengelola Enum

Berikut adalah halaman yang menjelaskan cara untuk mengelola Table:

1. [[Docs/Modul Data/Variable/Menambahkan Data]]
2. [[Docs/Modul Data/Variable/Mengubah Data]]
3. [[Docs/Modul Data/Variable/Menghapus Data]]
4. [[Docs/Modul Data/Variable/Mengotomasi]]: menghubungkan Table dengan [[Docs/Event/Apa itu Event|Event]].

Anda juga dapat memperdalam tentang Tipe Data yang relevan yaitu: [[Docs/Tipe Data/Variable]].

>**note** Tombol Edit tidak tersedia
>Karena nama header tidak dapat diganti, komponen Variable tidak memiliki langkah mengubah atribut komponen. Yang dapat Anda ubah adalah isi data di dalam halaman kerjanya (lihat [[#Mengelola Variable Data]]).

>**danger** Komponen Variable dalam [[Docs/Antarmuka#Area Manajemen Folder]]tidak dapat dibuat baru, diduplikasi ataupun dihapus.

## Membuka Halaman Kerja Variable

Klik [[^field/variable|Variables]] di [[Docs/Antarmuka#Area Manajemen Folder]] untuk membuka halaman kerja Variable.

## Antarmuka

Harap pastikan Anda memiliki akses dan dapat [[#Membuka Halaman Kerja Variable]]. Penjelasan antarmuka Enum lihat selengkap nya di [[Docs/Modul Data/Variable/Antarmuka|Antarmuka Variable]].

## Praktik Terbaik

- **Beri [[^field|Name]] yang deskriptif dan konsisten**, misalnya `AI_API_KEY` atau `HUB_IP_ADDRESS`, agar mudah dikenali saat dipilih atau dipanggil.
- **Isi [[^field|Description]]** untuk menjelaskan kegunaan Variable agar pengelola lain memahami fungsinya.
- **Pilih [[^field|Type]] yang sesuai** dengan Value agar nilai dapat dipakai dengan benar oleh komponen yang memanggilnya.
- **Simpan satu nilai di satu Variable** dan hindari menyalin nilai yang sama ke komponen lain.
- **Periksa pemakaian sebelum menghapus** Variable, terutama yang dipanggil oleh komponen di [[Docs/Modul Logic/Pengenalan|Modul Logic]].
- **Batasi pihak yang dapat melihat komponen Variable** bila [[^field|Value]] berisi nilai sensitif.

## Batasan dan Catatan

- Hanya ada satu komponen Variable di dalam Pro, dan tidak dapat ditambah lewat [[Docs/Antarmuka#Area Manajemen Folder]].
- Komponen Variable tidak dapat dihapus, tetapi dapat dipindahkan ke folder lain.
- Header [[^field|Name]] "Variables" tidak dapat diganti.
- Atribut [[^field|Name]] dari Variable Data harus unik.
- [[^field|Created At]] dan [[^field|Updated At]] terisi otomatis dan tidak perlu Anda isi.
- Menghapus baris Variable dapat membuat [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] atau komponen yang memanggil Name tersebut menghasilkan error.
- Isi [[^field|Value]] ditampilkan secara terbuka pada halaman kerja komponen Variable, sehingga hanya anggota yang memiliki akses komponen Variable yang dapat melihatnya.

## TL:DR

- Variable adalah komponen bawaan Pro yang menjadi satu sumber data universal, dibuat otomatis di folder root dan tidak dapat dihapus.
- Isi Variable dikelola di halaman kerja berbentuk tabel dengan kolom [[^field|Name]], [[^field|Type]], [[^field|Value]], [[^field|Description]], [[^field|Created At]] , dan [[^field|Updated At]].
- [[^field|Name]] harus unik, sedangkan [[^field|Created At]] dan [[^field|Updated At]] terisi otomatis.
- Field bertipe Variable menampilkan daftar dari [[Docs/Tipe Data/Variable|Variable Data]], dan Komponen [[Docs/Modul Logic/Pengenalan|Modul Logic]] dapat memanggil Variable cukup dengan [[^field|Alias]].
- Variable memilki akses yang ketat sehingga [[^field|Value]] yang sensitif dapat dipakai untuk integrasi tanpa perlu diketahui tim.
- Hati-hati saat menghapus [[Docs/Tipe Data/Variable|Variable Data]], karena komponen yang memanggilnya akan menghasilkan nilai kosong atau error.

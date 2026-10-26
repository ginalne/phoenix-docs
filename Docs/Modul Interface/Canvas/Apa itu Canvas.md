---
    status: release
    title: "Apa itu Canvas?"
    description: Canvas adalah komponen modul Interface untuk menyusun, menghubungkan, dan memetakan data atau presentasi secara visual menggunakan widget.
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="0 0 56 56">
  <path
    d="M 2.0241 44.9686 L 21.3578 44.9686 C 22.5443 44.9686 23.2888 44.2241 23.2888 43.0841 C 23.2888 41.9674 22.5443 41.2229 21.3578 41.2229 L 5.8629 41.2229 L 5.8629 41.1065 L 14.9597 32.2656 C 20.4969 26.8913 22.1255 24.0994 22.1255 20.5165 C 22.1255 15.1888 17.4026 11.1172 11.0977 11.1172 C 6.1421 11.1172 1.9078 13.7928 .4886 17.8875 C .2094 18.6786 .1 19.3300 .1 19.9117 C .1 21.0749 .7910 21.8427 1.9310 21.8427 C 3.0245 21.8427 3.4898 21.3308 3.8388 20.1676 C 4.0250 19.4463 4.2809 18.7949 4.6531 18.1900 C 5.8862 16.1194 8.1895 14.7932 11.0977 14.7932 C 14.8667 14.7932 17.8679 17.4455 17.8679 20.7492 C 17.8679 23.4247 16.7745 25.2394 12.1679 29.7762 L 1.2796 40.5947 C .3025 41.5718 0 42.1535 0 43.0143 C 0 44.2241 .7910 44.9686 2.0241 44.9686 Z M 30.0125 44.9221 L 39.5514 44.9221 C 49.9745 44.9221 56 38.7102 56 28.2174 C 56 17.7247 49.9745 11.6524 39.5514 11.6524 L 30.0125 11.6524 C 28.7329 11.6524 27.9187 12.4899 27.9187 13.7928 L 27.9187 42.7584 C 27.9187 44.0845 28.7329 44.9221 30.0125 44.9221 Z M 32.1297 41.1065 L 32.1297 15.4214 L 39.2489 15.4214 C 47.2523 15.4214 51.6960 20.0745 51.6960 28.2407 C 51.6960 36.4534 47.2523 41.1065 39.2489 41.1065 Z" />
</svg>'
      tree:
        priority: 6
---
# Apa itu Canvas?

>**note** Canvas merupakan salah satu komponen dalam modul [[Docs/Modul Interface/Pengenalan|Interface]] di Phoenix.

Canvas adalah komponen yang dapat digunakan untuk menyusun, menghubungkan, dan memetakan data atau presentasi secara visual.

Canvas memberi fleksibilitas untuk membuat diagram, tabel, maupun proyeksi tanpa dibatasi struktur baris dan kolom. Anda menyusun tampilan dari [[#Widget Canvas|widget]] yang mengambil data lewat [[Docs/Tipe Data/Query]], menghubungkannya dengan [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] atau komponen lain melalui tombol, lalu membagikannya sebagai tautan [[#Mempublikasikan Canvas|publish]]. Dengan [[#Binding Canvas|Binding]], satu desain Canvas dapat dipakai ulang untuk data yang berbeda.

## Mengapa Menggunakan Canvas?

- **Bebas dari struktur baris dan kolom.** Anda dapat menyusun diagram, tabel, maupun proyeksi sesuai kebutuhan tampilan.
- **Banyak jenis tampilan dalam satu halaman.** Teks, grafik, tabel, kanban, gantt, timeline, gallery, dan space dapat dikombinasikan dalam satu Canvas.
- **Mulai lebih cepat dengan Template.** [[#Template Canvas|Template]] menggabungkan banyak widget yang sudah didesain dan siap dipakai.
- **Terhubung dengan logika.** Widget Button dapat memicu [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] atau membuka komponen lain.
- **Satu desain untuk banyak data.** [[#Binding Canvas|Binding]] membuat tampilan yang sama menyesuaikan inCanvasasinya dengan nilai parameter yang berbeda.
- **Mudah dibagikan.** Canvas dapat dipublikasikan dan dibuka melalui satu tautan.
- **Data sumber tetap aman.** Menghapus Canvas hanya menghapus template dan propertinya, bukan data sumber.

## Konsep Utama

| Istilah                                                       | Penjelasan                                                                                                                       |
| ------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| [[#Widget Canvas|Widget]]                                    | Elemen penyusun tampilan Canvas, misalnya teks, grafik, tabel, atau tombol.                                                      |
| [[#Layout Canvas|Layout]]                                    | Wadah yang mengatur susunan widget secara horizontal atau vertikal. Layout dapat berisi widget maupun Layout lain.               |
| [[#Template Canvas|Template]]                                | Gabungan banyak widget yang sudah didesain dan siap dipakai.                                                                     |
| [[#Header Toolbar dan Design Toolbar|Header Toolbar]]        | Bilah pintasan aksi widget yang tampil ketika widget dipilih pada Edit Mode.                                                     |
| [[#Header Toolbar dan Design Toolbar|Design Toolbar]]        | Panel pengaturan tata letak dan tampilan widget yang tampil ketika widget dipilih pada Edit Mode.                                |
| [[#Mode View dan Edit|View Mode dan Edit Mode]]              | Dua mode Canvas. View Mode bersifat read only, Edit Mode untuk menyusun dan mengubah isi Canvas.                                 |
| [[#Binding Canvas|Binding]]                                  | Parameter Canvas yang dapat dipakai dalam Query widget dan memiliki nilai bawaan.                                                |
| [[#Mempublikasikan Canvas|Publish]]                          | Konfigurasi untuk mengubah Canvas menjadi tautan yang dipublikasikan.                                                            |
| [[Docs/Tipe Data/Query]]                                      | Tipe Data yang dipakai widget untuk mengambil dan menyaring data sumber.                                                         |

## Cara Kerja

Penjelasan cara kerja Canvas lihat selengkap nya di [[Docs/Modul Interface/Canvas/Cara Kerja|Cara Kerja Canvas]].

## Mengelola Canvas

Berikut adalah halaman yang menjelaskan cara untuk mengelolanya:
1. [[Docs/Modul Interface/Canvas/Membuat Baru]] Canvas dalam halaman kerja.
2. [[Docs/Modul Interface/Canvas/Mengubah]] Atribut Canvas seperti [[^field|Name]], [[^field|Description]], atau [[^field|Filter]].
3. [[Docs/Modul Interface/Canvas/Menghapus]] Canvas.
4. [[Docs/Modul Interface/Canvas/Binding|Memahami Binding]] dalam Canvas.
5. [[Docs/Modul Data/Table/Mempublikasi]]: mengatur publikasi Table.

## Antarmuka

Penjelasan antarmuka Canvas lihat selengkap nya di [[Docs/Modul Interface/Canvas/Antarmuka|Antarmuka Canvas]].

## Mengisi Canvas

Canvas bisa disesuaikan sesuai kebutuhan agar membuat interaksi menjadi lebih mudah. Anda dapat menggunakan [[Docs/Modul Interface/Canvas/Layout]] untuk mengatur tata letak dan [[Docs/Modul Interface/Canvas/Widget/Pengenalan|Widget]] untuk mengisi konten dalam Canvas. Anda juga dapat mengisi dengan [[Docs/Modul Interface/Canvas/Template/Pengenalan|Template Canvas]] siap pakai.

## Hak Akses

Penjelasan tentang pengelolaan Hak Akses dalam komponen Canvas lihat selengkapnya di [[Docs/Modul Interface/Canvas/Hak Akses]].

## Praktik Terbaik

- **Pisahkan tampilan dan data.** Gunakan Canvas untuk menyajikan data, dan kelola Row di [[Docs/Modul Data/Table/Apa itu Table|Table]] atau [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]].
- **Manfaatkan [[#Binding Canvas|Binding]] untuk mendesain sekali.** Satu Canvas dengan Binding dapat dipakai untuk banyak data. Isi [[^field|Default Value]] agar Canvas tidak kosong saat dibuka tanpa parameter.
- **Mulai dari [[#Template Canvas|Template]].** Gunakan Template siap pakai lalu sesuaikan widget-nya agar desain lebih cepat selesai.
- **Pastikan perubahan tersimpan.** Tunggu sekitar 3 detik atau klik [[^button/save|Save]] sebelum meninggalkan halaman, terutama setelah mengubah banyak widget.
- **Periksa [[^field|Status]] sebelum membagikan [[^field|Link]].** Pastikan Status sudah [[^value/radio|Active]] sebelum tautan dibagikan.
- **Berhati-hati dengan Button pada Canvas publik.** Siapa pun yang memiliki tautan dapat menekan widget Button, jadi pastikan [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]] dan Flow yang dipicu aman dijalankan publik.
- **Atur Data Access sesuai peran.** Beri [[Docs/Modul Developer/Workspace/Data Access|Data Access]] Add, Update, atau Delete hanya kepada pengguna yang bertugas mendesain.
- **Lihat halaman widget untuk pengaturan lanjutan.** [[#Header Toolbar dan Design Toolbar|Toolbar]] setiap widget berbeda, jadi rujuk halaman widget yang bersangkutan.

## Batasan dan Catatan

- Canvas dalam [[#Mode View dan Edit|View Mode]] bersifat read only. Berpindah ke [[^value/radio|Edit]] hanya dapat dilakukan jika salah satu Data Access Canvas (Add, Update, atau Delete) bernilai [[^value/boolean/allow]].
- Tombol [[^button/edit|Edit]] hanya mengubah atribut Canvas (Name dan Description), bukan isi Canvas.
- Widget yang menyerupai komponen Interface lain bersifat lite. Query diatur melalui [[^button/q]], sedangkan isinya (data hasil [[Docs/Tipe Data/Query|Query]]) tidak dapat dimanipulasi dari Canvas.
- Canvas hanya memiliki satu jenis [[#Layout Canvas|Layout]], yang dapat ditumpuk di dalam Layout lain. Tipe horizontal atau vertical dapat diubah dengan toggle pada header toolbar.
- Panel tata letak pada [[#Header Toolbar dan Design Toolbar|design toolbar]] sama di semua widget, sedangkan header toolbar dan panel tampilan bersifat unik untuk setiap widget.
- Nama [[#Binding Canvas|Binding]] harus unik dan dipakai dalam Query widget. [[^field|Header]] bernilai N/A bila Canvasat tidak membutuhkannya.
- [[^button/refresh|Refresh]] tidak dapat dilakukan ketika Canvas sedang menyimpan perubahan.
- Tautan [[#Mempublikasikan Canvas|Publish]] yang Active dapat dibuka publik dalam View Mode, termasuk menekan widget Button.
- Menghapus Canvas hanya menghapus template dan properti termasuk Query. Data sumber tetap aman, tetapi tautan yang sudah dibagikan melalui [[#Mempublikasikan Canvas|Publish]] menjadi tidak valid.
- Function Access View Publish hanya melihat konfigurasi publikasi, sedangkan Publish dapat mengubahnya.

## TL:DR

- Canvas adalah komponen modul [[Docs/Modul Interface/Pengenalan|Interface]] untuk menyusun, menghubungkan, dan memetakan data atau presentasi secara visual tanpa dibatasi baris dan kolom.
- Halaman kerja memiliki bilah navigasi ([[^button/edit|Edit]], [[^button/publish|Publish]], toggle [[^field|mode]], [[^button/save|Save]], [[^button/refresh|Refresh]]) dan area kerja. Lihat [[#Antarmuka Canvas]].
- [[#Mode View dan Edit|View Mode]] bersifat read only. Untuk berpindah ke Edit Mode, salah satu Data Access Canvas (Add, Update, atau Delete) harus [[^value/boolean/allow]]. Perubahan tersimpan manual atau otomatis sekitar 3 detik.
- Bangun Canvas dengan menambahkan [[#Layout Canvas|Layout]], [[#Widget Canvas|widget]], atau [[#Template Canvas|Template]], lalu atur melalui [[#Header Toolbar dan Design Toolbar|header toolbar dan design toolbar]] yang muncul saat widget dipilih.
- Gunakan [[#Binding Canvas|Binding]] agar satu desain dapat menampilkan data yang berbeda, dan [[#Mempublikasikan Canvas|Publish]] untuk membagikan Canvas lewat [[^field|Link]] yang dapat dibuka publik dalam View Mode.
- Hati-hati: Button pada Canvas publik dapat ditekan siapa saja, dan menghapus Canvas membuat tautan yang sudah dibagikan tidak valid (data sumber aman).

---
    status: release
    title: "Antarmuka Space"
    description: Penjelasan antarmuka di halaman kerja komponen Space
    pageDecoration:
      tree:
        priority: 5
---
# Antarmuka Space

![[Docs/Modul Interface/Space/interface-space.png]]
Halaman kerja Space terdiri dari bilah navigasi di bagian atas dan area kerja di bagian bawah. Bilah navigasi menampilkan ikon Space dan [[^field|Header Name]] di sisi kiri.

### Bilah navigasi Space terdiri dari:

| Tombol | Fungsi |
| --- | --- |
| [[^button/edit|Edit]] | Mengubah [[^field|Name]] dan [[^field|Description]] Space. |
| [[^button/refresh|Refresh]] | Memuat ulang tampilan halaman kerja. |
| [[^field|Search Space Data...]] | Mencari data pada Outliner berdasarkan Name, termasuk data milik Object yang jumlahnya banyak. |

### Area kerja Space

Area kerja berisi tiga bagian:

1. **View 3D** menampilkan ruang berupa grid lantai dengan penanda sumbu berwarna di titik pusat: x berwarna merah, y berwarna hijau, dan z berwarna biru. Di sinilah Weather, Environment, dan Object ditampilkan.
2. **Outliner** di sisi kiri mengelompokkan data menjadi [[^field|Weather]], [[^field|Environment]], dan [[^field|Object]]. Angka di samping nama kelompok, misalnya `(0)`, adalah jumlah data pada kelompok tersebut. Klik panah di samping nama kelompok untuk membuka atau menutup daftar data.
3. **Panel Properti** di sisi kanan menampilkan nilai data yang difokuskan. Jika belum ada data yang difokuskan, panel menampilkan [[^field|No selection]]. Selengkapnya lihat [[#Panel Properti]].

>**note** Perbedaan tampilan desktop dan mobile
> Pada desktop, view 3D dikendalikan dengan mouse dan keyboard. Pada mobile, view 3D dikendalikan dengan gestur sentuh.

### Interaksi Antarmuka Space

| Fungsi | Aksi |
| --- | --- |
| Memutar sudut pandang | Tekan dan tahan klik kiri pada view 3D, lalu gerakkan kursor. |
| Menggeser tampilan | Tahan tombol Shift, lalu tekan dan tahan klik kiri pada view 3D dan gerakkan kursor. |
| Memperbesar atau memperkecil tampilan | Putar roda mouse (*wheel*) pada view 3D. |
| Memfokuskan data | Klik data pada Outliner, atau klik langsung objek pada view 3D. |
| Memindahkan objek 3D yang difokuskan | Gunakan alat bantu pemindah yang muncul pada objek 3D yang difokuskan. Perubahan nilai hasil pemindahan memperbarui Row sumber jika atributnya di-*bind*. Tidak berlaku untuk Environment, yang diubah lewat [[#Panel Properti]]. |
| Mengubah Origin | Klik kanan Object pada Outliner ➜ [[^field/edit|Edit]]. |
| Menambah data | Klik kanan pada Outliner ➜ [[^field/add|Add Weather]], [[^field/add|Add Environment]], atau [[^field/add|Add Object]]. |
| Menghapus data | Klik kanan data pada Outliner ➜ [[^button/delete|Delete]]. |
| Mengendalikan view 3D di mobile | Geser satu jari untuk memutar, geser dua jari untuk menggeser, dan cubit dengan dua jari untuk memperbesar atau memperkecil tampilan. |

## Panel Properti

Panel Properti tampil di sisi kanan halaman kerja. Selama belum ada data yang difokuskan, panel menampilkan [[^field|No selection]]. Ketika Anda memfokuskan data, baik dengan klik pada Outliner maupun klik langsung pada view 3D, panel menampilkan propertinya dan nilai tersebut dapat diubah.

Tidak ada tombol penyimpanan: perubahan langsung diterapkan. Pada field teks ada jeda (*debounce*) sekitar 300 ms, sedangkan *toggle* dan pilihan berlaku seketika.

Pengaruh perubahan nilai berbeda untuk tiap jenis data:

| Jenis Data | Sumber nilai | Pengaruh perubahan di panel |
| --- | --- | --- |
| [[#Mengelola Weather|Weather]] | Nilai statis atau [[Docs/Tipe Data/Query#Single Output|Single Output]] (hasil kalkulasi) | Hanya mengubah konfigurasi data di Space, tidak memengaruhi Row pada data sumber. |
| [[#Mengelola Environment|Environment]] | Data statis | Hanya mengubah konfigurasi data di Space, tidak memengaruhi Row pada data sumber. |
| [[#Mengelola Object|Object]] | [[Docs/Tipe Data/Query#Table Output|Table Output]] (data riil) | Memengaruhi [[Docs/Tipe Data/Row]] sebenarnya pada data sumber. |

Pada Object, mengubah atribut menjadi [[^value/radio|static]] berlaku untuk seluruh objek 3D yang dirender. Misalnya atribut `on` pada Model lampu yang diubah menjadi true akan menyalakan semua lampu pada tampilan, sedangkan atribut [[^value/radio|bind]] mengikuti Row masing-masing.

>**warning** Perubahan pada Object mengubah data sumber
> Nilai yang diubah pada Object tersimpan ke data sumber dan terlihat oleh komponen lain yang memakai Row yang sama. Perubahan hanya berhasil bila [[#Hak Akses Space|Data Access]] sumber mengizinkan.

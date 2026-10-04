---
    status: release
    title: "Apa itu Form?"
    description: 
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="0 0 16 16">
  <path
    d="M7 2.5a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-7a.5.5 0 0 1-.5-.5zM2 1a2 2 0 0 0-2 2v2a2 2 0 0 0 2 2h2a2 2 0 0 0 2-2V3a2 2 0 0 0-2-2zm0 8a2 2 0 0 0-2 2v2a2 2 0 0 0 2 2h2a2 2 0 0 0 2-2v-2a2 2 0 0 0-2-2zm.854-3.646a.5.5 0 0 1-.708 0l-1-1a.5.5 0 1 1 .708-.708l.646.647 1.646-1.647a.5.5 0 1 1 .708.708zm0 8a.5.5 0 0 1-.708 0l-1-1a.5.5 0 0 1 .708-.708l.646.647 1.646-1.647a.5.5 0 0 1 .708.708zM7 10.5a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-7a.5.5 0 0 1-.5-.5zm0-5a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5m0 8a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5" />
</svg>'
      tree:
        priority: 4
    icon: assets/icons/type/-f.svg
---
# Apa itu Form?

>**note**Info
>_Form_ merupakan salah satu komponen dalam modul [[Docs/Modul Interface/Pengenalan|Interface]] di Phoenix.

Form adalah komponen untuk menginput, melihat, dan mengubah data secara terstruktur. Setiap kolom ditampilkan sebagai field yang jelas dan terarah, sehingga proses pengisian data menjadi lebih rapi, konsisten, dan minim kesalahan. Anda juga dapat membagikan Form kepada publik agar proses pengumpulan data bisa lebih cepat dan efektif.

## Antar Muka

Berikut adalah tampilan form saat pertama kali dibuat:

![[Docs/Modul Interface/Form/form-new.png]]
Berikut penjelasan terkait beberapa fungsi halaman kerja Form:

| | |
|-------------------|---------------------------------------------------------------------------------------------------|
|[[field/form|Judul Form]]| Ikon Form dalam phoenix serta [[field|Header Name]] Form.  
| [[button/edit|Edit]]  | Tombol yang berfungsi untuk membuka modal Edit Form untuk memperbarui nama dan deskripsi Form. |
| [[button/publish|Publish]]  | Tombol yang berfungsi untuk membuka modal Publish Form untuk memperbarui konfigurasi publish Form. |
|  [[mode/view|View]] | Saklar dengan mode View agar konten Form dapat di sunting. |
|  [[mode/edit|Edit]] | Saklar dengan mode Edit agar  konten Form hanya bisa dilihat |
| [[button/save|Save]]  | Tombol yang berfungsi untuk menyimpan perubahan Form. |
| [[button/refresh|Refresh]]  | Tombol yang berfungsi untuk menyegarkan lagi halaman Form. |
|[[button/submission|Submission]]| Tombol yang berfungsi untuk membuka bilik submission.

>**note** Perbedaan Icon
>Dalam mode dekstop tombol [[button/submission|Submission]]sedikit berbeda, tombol terlihat dengan susunan informasi submission yaitu submitted, waiting dan failure

> **warning** Harap hati-hati
> Saat melakukan[[button/refresh|Refresh]] halaman, pastikan bahwa perubahan Anda saat ini sudah disimpan. Jika tombol [[button/save|Save]]masih aktif, berarti perubahan belum disimpan.


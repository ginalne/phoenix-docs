---
    status: release
    title: "Mempublikasi Tree"
    description: Penjelasan cara mempublikasikan komponen Tree
    pageDecoration:
      tree:
        priority: -1
---
# Mempublikasi Tree

Tampilan Tree yang bersifat hirarki dapat dibagikan kesiapapun tanpa otorisasi akun di Phoenix. Caranya adalah dengan mengganti konfigurasi publikasi menjadi terbuka melalui link yang dibagikan.

## Syarat

Membagikan Tree memperlukan ijin akses [[^field|Comp. Access : Visible]] dan [[^field|Function Access : View Publish]] untuk mendapatkan link, namun perlu ijin akses [[^field|Function Access : Modify Publish]] agar dapat mengubah konfigurasi (jika belum publikasi belum diijinkan).

## Mengubah Konfigurasi Publish

![[Docs/Modul Data/Tree/publish-tree.png]]
1. Buka halaman kerja Tree di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik [[^button/edit|Publish]]
2. Ubah status menjadi [[^value/boolean/Active]] untuk dipublikasi.
3. Klik [[^button/copy|Copy]] untuk menyalin tautan.
4. Klik [[^button|Update]] untuk menyimpan konfigurasi

>**success** Tree berhasil dipublikasi
> Kirim tautan ke siapapun agar tampilan Tree dapat diakses dan dilihat tanpa harus akun atau otorisasi akun Phoenix.

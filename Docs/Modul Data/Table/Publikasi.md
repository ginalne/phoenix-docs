---
    status: release
    title: "Mempublikasi Table"
    description: Penjelasan cara mempublikasikan komponen Table
    pageDecoration:
      tree:
        priority: -1
    tags:
      draft
---
# Mempublikasi Table

Tampilan Table yang bersifat hirarki dapat dibagikan kesiapapun tanpa otorisasi akun di Phoenix. Caranya adalah dengan mengganti konfigurasi publikasi menjadi terbuka melalui link yang dibagikan.

## Syarat

Membagikan Table memperlukan ijin akses [[^field|Comp. Access : Visible]] dan [[^field|Function Access : View Publish]] untuk mendapatkan link, namun perlu ijin akses [[^field|Function Access : Modify Publish]] agar dapat mengubah konfigurasi (jika belum publikasi belum diijinkan).

## Mengubah Konfigurasi Publish

![[Docs/Modul Data/Table/publish-table.png]]
1. Buka halaman kerja Table di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik [[^button/edit|Publish]]
2. Ubah status menjadi [[^value/boolean/Active]] untuk dipublikasi.
3. Ubah status pada tabel menjadi [[^value/boolean/Active]] untuk mengijikan kolom dapat diisi.
4. Klik [[^button/copy|Copy]] untuk menyalin tautan.
5. Klik [[^button|Update]] untuk menyimpan konfigurasi

>**success** Table berhasil dipublikasi
> Kirim tautan ke siapapun agar mengisi Table dapat diakses tanpa harus akun atau otorisasi akun Phoenix.

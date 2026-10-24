---
    status: release
    title: "Mempublikasi Form"
    description: Penjelasan cara mempublikasikan komponen Form
    pageDecoration:
      tree:
        priority: -1
    tags:
      draft
---
# Mempublikasikan Form

Publish adalah konfigurasi untuk mengubah Form menjadi dipublikasikan, sehingga dapat dibuka dan diisi oleh publik lewat sebuah tautan.

1. Buka halaman kerja Form
2. Klik [[^button/publish|Publish]]
3. Atur konfigurasi publikasi
4. Klik [[^button|Update]]

![[Docs/Modul Interface/Form/publish-form.png]]

| Konfigurasi | Fungsi |
| --- | --- |
| [[^field|Status]] | Mengaktifkan atau menonaktifkan publikasi. Jika berstatus Non-Active, Form hanya dapat dilihat dan tidak dapat dikirim. |
| [[^field|Link]] | Tautan Form publik. Klik [[^button|Copy]] untuk menyalin, atau [[^button|Open New Tab]] untuk membukanya di tab baru. |
| [[^field|Language]] | Bahasa tampilan Form publik. |
| [[^field|Single Submission]] | Jika aktif, setiap perangkat hanya dapat mengirim Form satu kali. |

>**note** Perubahan konfigurasi tidak memengaruhi Submission yang sudah masuk
> Mengubah [[^field|Status]] atau [[^field|Single Submission]] hanya berlaku untuk pengiriman berikutnya.

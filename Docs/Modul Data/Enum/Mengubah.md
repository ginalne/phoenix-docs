---
    status: release
    title: "Mengubah Enum"
    description: Penjelasan cara mengubah atribut komponen Enum
    pageDecoration:
      tree:
        priority: 1.5
---
# Mengubah Enum

![[Docs/Modul Data/Enum/update-enum.png]]
1. Buka halaman kerja Enum
2. Klik [[^button/edit|Edit]]
3. Ubah [[^field|Name]], [[^field|Description]], [[^field|Format]], [[^field|Header]] (jika dapat diisi), atau [[^field|Strict On Selected]]
4. Klik [[^button|Update]]

>**warning** Mengubah [[^field|Format]]
> [[^field|Format]] masih dapat diubah meskipun Enum sudah memiliki [[Docs/Tipe Data/EnumData]]. Phoenix menampilkan peringatan terlebih dahulu, dan Anda perlu mengisi [[^field|Force Update]] untuk melanjutkan. Hasilnya dapat berupa *loss safe* (akan mencoba mengonversi nilai ke [[^field|Format]] baru, jika gagal akan muncul peringatan yang sama) atau *force* (paksa, nilai yang tidak dapat dikonversi bisa hilang). Mohon periksa [[^field|Value]] yang sudah ada sebelum melanjutkan.


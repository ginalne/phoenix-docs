---
    status: release
    title: "FAQ : Tree"
    description: Pertanyaan yang sering diajukan pada komponen Table
    pageDecoration:
      tree:
        priority: -10
    tags:
      draft
---
# FAQ : Table

Berikut adalah pertanyaan yang sering diajukan pada komponen Table:

> **faq**
> **Apakah Table baru langsung berisi data?**
> Tidak. Row pada Table yang baru dibuat masih kosong. Klik [[^button/add|Add Row]] di halaman kerja.
> **Mengapa saya harus memilih Alias?**
> Alias menentukan nilai [[Docs/Tipe Data/Column]] yang tampil pada field berformat [[Docs/Tipe Data/Row]] dengan pola `ID - Alias Value`, sehingga Row mudah dikenali.
> **Bisakah lebih dari satu Column dijadikan Alias?**
> Tidak. Pilih salah satu Column sebagai Alias.
> **Bisakah Column diubah setelah Table dibuat?**
> Bisa, lewat [[^button/edit|Edit]]. Jika perubahan berisiko menghilangkan data, Phoenix menampilkan peringatan dan Anda dapat melanjutkan dengan *force update*.
> **Dari mana kolom ID dan Action berasal?**
> Keduanya kolom tambahan pada halaman kerja Table, ID di bagian awal (terisi otomatis) dan Action di bagian akhir.
> **Di mana saya bisa mempelajari fungsi Merge, Publish, dan Event?**
> Lihat [[Docs/Modul Data/Table/TableData Merge|Merge]], [[Docs/Modul Data/Table/Publish|Publish]], dan [[Docs/Modul Data/Table/Event|Event]].

---
    status: release
    title: "FAQ : Workspace"
    description: Pertanyaan yang sering diajukan pada komponen Workspace
    pageDecoration:
      tree:
        priority: -10
---
# FAQ : Workspace

Berikut adalah pertanyaan yang sering diajukan pada komponen Workspace:

>**faq**
>**Bagaimana pengguna dapat memakai Workspace?**
>Pengguna harus dipetakan ke Workspace melalui komponen [[Docs/Modul Developer/Group/Apa itu Group|Group]]. Setelah itu, saat membuka Phoenix mereka akan masuk ke Workspace yang terakhir dipakai.
>**Bagaimana cara berpindah Workspace?**
>Klik tombol yang berisi nama Workspace aktif di [[Docs/Dasar/Antarmuka#Area Manajemen Folder]], lalu pilih Workspace tujuan pada popup yang muncul. Lihat [[#Berpindah Workspace]].
>**Workspace mana yang aktif saat saya membuka Phoenix?**
>Workspace yang terakhir Anda pakai. Jika Workspace itu sudah tidak valid, Anda otomatis dipindahkan ke Workspace pertama pada daftar Workspace di Group.
>**Apakah satu pengguna dapat berada di lebih dari satu Group?**
>Tidak. Satu pengguna hanya dapat berada di satu [[Docs/Modul Developer/Group/Apa itu Group|Group]], sehingga akses Workspace-nya mengikuti Group tersebut.
>**Apakah Group anak otomatis memakai Workspace milik Group induk?**
>Tidak. [[Docs/Modul Developer/Group/Apa itu Group|Group]] anak tidak mewarisi Workspace dari Group induk, sehingga Workspace perlu diisi ulang di setiap Group.
>**Apa nilai awal hak akses pada Workspace baru?**
>Nilai awal mengikuti Workspace yang sedang aktif saat Workspace dibuat. Origin, sebagai Workspace pertama, seluruh hak aksesnya [[^value/boolean/allow]].
>**Apakah Origin dapat dihapus?**
>Origin tidak dapat dihapus selama belum ada Workspace lain di posisi root yang terhubung ke [[Docs/Modul Developer/Group/Apa itu Group|Group]]. Ini untuk mencegah hilangnya akses ke root utama.
>**Apakah perubahan hak akses perlu disimpan atau dimuat ulang oleh anggota?**
>Tidak. Perubahan tersimpan langsung dan langsung berlaku bagi anggota yang sedang membuka Phoenix.
>**Apa yang terjadi jika folder diatur disallow tetapi komponen di dalamnya allow?**
>Komponen tidak dapat dibuka karena folder induknya tidak tampil di Area Manajemen Folder. Namun komponen itu tetap dapat muncul pada pilihan *field* atau Query.
>**Bagaimana cara menyembunyikan komponen sepenuhnya?**
>Atur [[^field|Visible]] pada komponen itu sendiri menjadi [[^value/boolean/disallow]], bukan hanya pada folder induknya.
>**Hak akses apa yang dibutuhkan untuk memindahkan folder atau komponen?**
>Untuk memindahkan ke folder lain, diperlukan [[^field|Delete]] pada folder atau komponen yang dipindahkan, dan [[^field|Add]] pada folder tujuan. Mengubah urutan di dalam folder yang sama tidak memerlukan [[^field|Add]] maupun [[^field|Delete]]. Pemindahan juga mengubah struktur folder Pro, bukan hanya tampilan halaman kerja Workspace.
>**Apa bedanya Component Access dan Data Access?**
>[[^field|Component Access]] mengatur komponen secara keseluruhan (header), sedangkan [[^field|Data Access]] mengatur data di dalam komponen, misalnya [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]]. Selengkapnya lihat [[Docs/Modul Developer/Workspace/Data Access]].
>**Apa arti Visible = disallow?**
>Pada komponen, komponen tidak tampil di Area Manajemen Folder dan tidak tampil dalam *field*, termasuk saat mengisi Query atau membuat komponen Interface. Pada folder, folder beserta isinya tidak tampil di Area Manajemen Folder.
>**Mengapa anggota tidak dapat mengubah baris di Table View padahal Data Access sudah allow?**
>Pengelolaan baris memerlukan dua syarat: Data pada [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]] berstatus `editable` dan [[Docs/Modul Developer/Workspace/Data Access]] komponen sumber mengizinkan. Jika salah satunya tidak terpenuhi, baris tidak dapat dikelola.
>**Apakah komponen sumber harus Visible agar Table View dapat menampilkan datanya?**
>Tidak selalu. Komponen sumber hanya perlu [[^field|Visible]] [[^value/boolean/allow]] ketika Query diisi. Setelah Query terisi, [[^field|Visible]] tidak perlu lagi [[^value/boolean/allow]].
>**Apakah Variable Data tetap dapat dipilih jika komponen Variable disembunyikan?**
>Ya. Anggota tanpa akses ke [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] tidak dapat membuka halamannya dan tidak dapat mengetahui [[^field|Value]], tetapi daftar Variable Data tetap dapat dipilih dan dipakai untuk otomasi atau integrasi.
>**Apa bedanya View Publish dan Publish?**
>[[^field|View Publish]] hanya untuk melihat konfigurasi publikasi, misalnya menyalin [[^field|Publish Link]]. [[^field|Publish]] dapat memperbarui konfigurasi publikasi.
>**Apa arti sel yang kosong pada halaman kerja?**
>Hak akses tersebut tidak relevan untuk komponen yang bersangkutan.
>**Apakah tombol Edit dapat dipakai untuk mengubah hak akses?**
>Tidak. Tombol [[^button/edit|Edit]] hanya mengubah [[^field|Name]] dan [[^field|Description]] Workspace. Hak akses diatur dengan tombol toggle pada sel di halaman kerja.
>**Apakah pengisi Form atau pengunjung tautan publikasi perlu diatur di Workspace?**
>Tidak. Akses mereka tidak dibatasi Workspace dan ditentukan oleh pembuat komponen saat mempublikasikannya, sehingga [[^field|Publish]] sebaiknya hanya diberikan kepada [[Docs/Modul Developer/Group/Apa itu Group|Group]] yang tepercaya.
>**Apakah ada pengaman jika saya tidak sengaja mengunci akses administrator?**
>Tidak ada pengaman bawaan untuk pengaturan hak akses. Phoenix hanya mencegah penghapusan Workspace root terakhir yang terhubung ke Group. Karena itu, periksa pengaturan sebelum menonaktifkan akses pada komponen Workspace dan Group.
>**Tombol apa saja yang tersedia pada bilah navigasi Workspace?**
>Hanya [[^button/edit|Edit]] dan [[^button/refresh|Refresh]]
---
    status: release
    title: "FAQ : Group"
    description: Pertanyaan yang sering diajukan pada komponen Group
    pageDecoration:
      tree:
        priority: -10
---
# FAQ : Group

Berikut adalah pertanyaan yang sering diajukan pada komponen Group:

> **faq**
> **Apa bedanya menambahkan Group dari Area Manajemen Folder dan dari halaman kerja Group?**
> Dari Area Manajemen Folder, Group ditambahkan sebagai komponen di folder dan [[^field|Parent]] wajib diisi. Dari halaman kerja Group, formnya tidak memiliki bagian direktori dan [[^field|Parent]] terisi otomatis.
> **Mengapa Group yang saya buat dari halaman kerja tidak muncul di Area Manajemen Folder?**
> Group tersebut belum ditempatkan sebagai komponen. Klik kanan Group ➜ [[^field|Place to Directory]] untuk menempatkannya di posisi *root* folder dari Workspace yang sedang aktif.
> **Apakah Group anak mewarisi Workspace dari Group induk?**
> Tidak. Tambahkan Workspace pada setiap Group melalui [[^field|Search workspace to add...]].
> **Bagaimana cara memindahkan User ke Group lain?**
> Buka halaman kerja Group, lalu *drag and drop* User dari Group lama ke Group tujuan. Lihat [[Docs/Modul Developer/Group/Mengelola User#Memindahkan User]].
> **Apakah satu User dapat berada di beberapa Group?**
> Tidak. Satu User hanya dapat berada dalam satu Group, jadi memindahkan User berarti mengeluarkannya dari Group lama.
> **Apa yang terjadi bila Group tidak memiliki Workspace?**
> Anggota Group tidak memiliki Workspace untuk dipakai. Pastikan setiap Group masih memiliki minimal satu Workspace.
> **Mengapa Group tidak bisa dihapus?**
> Group yang dihapus, beserta Group anaknya, tidak boleh masih memiliki User. Pindahkan semua User ke Group lain terlebih dahulu.
> **Bagaimana cara menutup daftar Group anak?**
> Klik panah di sebelah kiri judul Group.
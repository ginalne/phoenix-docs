---
  pageDecoration:
    tree:
      priority: -13
  tags:
    meta
    prompt
---
2026-11-01 18:30 

![[prompt/Screenshot_20261101_182157.jpg]]

/phoenix-docs-silverbullet /phoenix-docs-knowledge 

Tolong bantu saya buat halaman berikut:

[[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan]]

[[Docs/Modul Logic/Flow/Flow Block/Event/Pulser]], [[Docs/Modul Logic/Flow/Flow Block/Event/Variable Event]], [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event]], [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event]], [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event]].

1. Bagian pengenalan adalah menjelaskan kategori (dalam konteks ini Event) dibandingkan kategori lain.
2. Struktur halaman pada penjelasan Block bisa disesuaikan supaya TLDR, Batasan dan FAQ tidak perlu dimasukan, bagian Contoh Penggunaan mungkin lebih ke kasus kecil dalam penggunaan block secara input dan output yang diberikan, semisal dalam Table Row Event ada 3 penggunaan yang berguna yaitu Melakukan Integrasi ketika ada Row baru, Otomasi ketika ada Row diperbarui, dan Otomasi ketika Row dihapus, dengan variasi kombinasi output dengan tipe data yang mungkin terjadi tanpa melibatkan block lain. Sehingga pada setiap halaman Block pengguna dapat memahami fungsi blok secara komprehensif.
3. FYI untuk claude, saya lupa mengupdate, jadi anggap block EnumData dan TreeNode memiliki output old dan event.
4. field old adalah output dengan tipe data Object. jika tidak ada perubahan make nilai old ada Empty. jika hanya satu field yang diubah maka isi old hanya field itu saja. event menghasilkan output string “create”, “update”, “delete”. Jika event = create maka old akan menghasilkan Empty. Jika event = delete maka isi old adalah semua field.
5. Anda juga bisa memberikan struktur halaman yang lebih baik dalam menjelaskan halaman ini seperti bagaimana dokumentasi aplikasi lain menjelaskan Block Logic mereka.
6. Foto semua block yang saya minta sudah saya susun dan lampirkan.
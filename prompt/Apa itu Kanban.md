---
  pageDecoration:
    tree:
      priority: -7
  tags:
    meta
    prompt
---
2026-10-19 17:00

![[prompt/phoenix.ginalne.com_testing_tableview_3_page=1(Documentation).png]]

![[prompt/phoenix.ginalne.com_testing_kanban_13(Documentation).png]]
![[prompt/phoenix.ginalne.com_testing_kanban_13(Documentation) (1).png]]
/phoenix-docs-knowledge  /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Kanban?".
base knowledge:

1. Kanban menampilkan data dalam bentuk kolom-kolom berdasarkan status atau kategori, dan setiap data direpresentasikan sebagai kartu yang dapat dipindahkan antar kolom. Komponen ini membantu Anda memvisualisasikan alur kerja dan memantau progres tugas secara intuitif.
2. Saat membuat Kanban, wajib mengisi Table - Column dengan format EnumData. Sehingga, EnumData akan dijadikan kolom Kanban. Dalam contoh Enum Status ada 4, sehingga Kanban akan memiliki 4 kolom.
3. Dibagian header adalah jumlah item, nama enumdata (Name - Description), serta setting.
4. Klik setting akan memunculkan modal pengaturan EnumData. Setiap EnumData dapat memiliki pengaturan dengan template Global atau Local. jika Global (default) maka perubahan template akan mempengaruhi EnumData lain, sedangkan Local maka perubahan template hanya diterapkan ke EnumData tersebut.
5. Setiap Row pada Table akan tampil sebagai kartu didalam Kanban (sesuai dengan nilai kolom EnumData nya).
6. Kartu memiliki template sebagai berikut:
   1. Column yang di isi akan tampil sesuai dengan posisi template nya. Class adalah nilai text yang sesuai dengan nama class styling tailwind. Action berisi tombol Delete disetiap baris. (informasi tentang tailwind yang digunakan oleh angular adalah    `"@tailwindcss/postcss": "^4.1.12",  "tailwindcss": "^4.1.12"`)
   2. Header, yaitu memiliki display flex-row dan berada pada bagian paling atas dalam kartu. Urutan pertama hingga terakhir dalam daftar adalah dari kiri ke kanan.
   3. Body, yaitu memiliki display flex-col dan urutannya atas ke bawah.
   4. Footer, yaitu memiliki display flex-row dan berada pada bagian paling bawah dalam kartu. Urutan pertama hingga terakhir dalam daftar adalah dari kiri ke kanan.
7. Jika template kosong (seperti saat pertama kali Kanban dibuat), tampilan kartu kanban adalah Kolom Alias dalam tabel (yang biasanya adalah nama dengan format Short Text).
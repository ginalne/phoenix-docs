---
  pageDecoration:
    tree:
      priority: -8
  tags:
    meta
    prompt
---
2026-10-21 14:00

![[prompt/phoenix.ginalne.com_testing_enum_46(Documentation) (1).png]]
![[prompt/phoenix.ginalne.com_testing_timeline_15(Documentation).png]]
![[prompt/phoenix.ginalne.com_testing_timeline_15(Documentation) (3).png]]
![[prompt/2026-10-21_14-31-36.png]]

![[prompt/phoenix.ginalne.com_testing_timeline_15(Documentation) (2).png]]

/phoenix-docs-knowledge  /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Timeline?".
base knowledge:

1. Timeline menampilkan data dalam urutan waktu sehingga Anda dapat memantau seperti jadwal, riwayat aktivitas, dan perkembangan suatu proses dengan lebih mudah linimasa. Komponen ini cocok untuk perencanaan, pelacakan progres, serta melihat hubungan antar peristiwa dalam satu rentang waktu.
2. Timeline memiliki Timeline Event dan Timeline Data.
3. Timeline Event berfungsi untuk membuat trigger Event (ke Flow Block Pulser) dengan/tanpa pengulangan (field End dan Interval akan hilang jika Repeat = Non-Active). Konteks menu pada block Timeline Event: Edit, Add Data, Add Event, Zoom, Delete Event.
4. Timeline Data berfungsi untuk membuka data sumber dengan bantuan Query. Konteks menu pada block Timeline Event: Rename Data, Add Data, Add Event, Zoom, Delete Data.
5. Klik kiri pada row akan membuka popup preview (judul, start, end, duration, status, calendar, relative, progress, change time (control to shift time), edit row), ketika edit row akan muncul modal form edit (akses tetap mengikuti Access Data pada sumber). Konteks menu pada Row dalam Timeline Data adalah Edit, View, Add Row, Add Data, Add Event, Zoom, Delete Row.
6. Konteks menu pada bagian yang kosong: Add Data, Add Event, Zoom
7. Konteks menu Zoom memiliki cabang: Zoom In, Zoom Out, Quarter - Month, Month - Week, Week - Date, Week - Dayweek, Date - Hour, Time - 30 Minute, Time - 10 Minute, Time - 1 Minute, Minute - Second.
8. Pada bagian Query di bagian Show, ada label Name, Start, End. untuk mengindikasikan kolom mana yang digunakan.
9. Interaksi yang bisa digunakan dalam halaman kerja timeline adalah:
    1. menggeser horizontal untuk berpindah posisi waktu.
    2. menggeser vertikal jika event dan data banyak
    3. wheel untuk mengubah scale factor range waktu timeline
    4. move klik pada blok data dan event: bagian kiri untuk memindahkan waktu start, bagian kanan memindahkan waktu finish, tengah untuk memindahkan keduanya secara simultan.
    5. Select. Ada gap diantara header dan  data, bisa dengan klik move untuk melakukan select, atau ctrl + shift dan klik blok untuk otomatis select pada range block tersebut. atau gunakan shift dan klik move pada area kerja.
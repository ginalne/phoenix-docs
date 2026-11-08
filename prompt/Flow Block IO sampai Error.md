---
  pageDecoration:
    tree:
      priority: -17
  tags:
    meta
    prompt
---
/phoenix-docs-silverbullet /phoenix-docs-knowledge

Tolong buatkan **8 halaman Flow Block** untuk dokumentasi Phoenix, yaitu halaman per block yang menjadi tujuan tautan pada enam halaman Pengenalan kategori Flow Block yang saya lampirkan (Input dan Output, Query, Operator, Modular, Chrono, Error). Enam halaman kategori itu sudah final dan menjadi sumber kebenaran untuk fungsi tiap block, istilah, path, dan alias tautan.

## Daftar halaman

Seluruh path berada di bawah `Docs/Modul Logic/Flow/Flow Block/`. Alias tautan mengikuti tabel pada halaman kategori.

| No | Kategori | Path | Alias tautan |
| --- | --- | --- | --- |
| 1 | Input dan Output | `Input dan Output/Branch` | Branch Block |
| 2 | Input dan Output | `Input dan Output/Passer` | Passer Block |
| 3 | Query | `Query/Condition` | Condition Query Block |
| 4 | Query | `Query/Execute` | Execute Query Block |
| 5 | Modular (API) | `Modular/API/HTTP Request` | HTTP Request API Block |
| 6 | Modular (AI) | `Modular/AI/OpenAI 4` | OpenAI 4 AI Block |
| 7 | Chrono | `Chrono/Delay` | Delay Chrono Block |
| 8 | Error | `Error/Error Message` | Error Message Block |

Catatan: kelompok tipe data pada Operator tidak memiliki halaman Pengenalan sendiri, jadi halaman block langsung berada di bawah folder tipe data.

## Fakta terkonfirmasi (dari penulis)

**Aturan dasar Flow yang relevan**
- Satu output hanya dapat terhubung ke satu input.
- Urutan eksekusi aliran yang bercabang tidak dapat diprediksi. Sebuah block baru diproses setelah setiap block yang terhubung ke inputnya selesai tereksekusi (lihat `Syarat Eksekusi`).

**Input dan Output**
- **Branch:** hanya satu input dan beberapa output, sehingga menjadi solusi atas batasan "satu output hanya ke satu input". Branch **bukan** block bersyarat. Input berupa *field* juga berguna untuk mendefinisikan data yang dapat dipakai banyak block (seperti *local variable*).
- **Passer:** memanfaatkan aturan Syarat Eksekusi. Karena setiap block yang terhubung ke input harus tereksekusi, Passer dipakai untuk memastikan beberapa aliran selesai semua, atau memastikan urutan aliran benar (contoh: membuat kode seri dengan bantuan Concatenate). Input berupa *field* juga berguna untuk mendefinisikan daftar data dalam satu block (seperti *local variable*).

**Query**
- **Condition:** hanya membangun bagian kondisi, yang kemudian dirangkai.
- **Execute:** menjalankan Query. Tidak ada kaidah Output tertentu, bentuk hasil mengikuti cara Query dirangkai.

**Operator**
- **Increment:** ada langkah (*step*) yang ditentukan. Penjelasan rinci ada di halamannya sendiri.
- **Implode:** dikelompokkan pada String karena array yang digabungkan juga harus bertipe String.
- **TableRow Parse** dan **Node Parse:** hasilnya berupa Object.
- **Assign:** hanya menetapkan satu atribut Object.
- **Concatenate, Pad Left, Pad Right, Merge, Parse, Stringify:** fungsi umum sesuai tabel pada halaman Operator (belum ada detail input/output).
- **If:** **belum terkonfirmasi.** Apakah memilih nilai (seperti *ternary*) atau menentukan jalur aliran, dan apa bedanya dengan Branch. Tanyakan kepada saya. Pada diagram Flow di skill, If dipakai sebagai blok kondisi dengan keterangan `If <Kondisi>?`.

**Modular**
- **HTTP Request:** mendukung semua metode (GET, POST, PUT, dan lain-lain). Respons berupa Object atau teks sesuai `Response Type`, dan `application/json` menjadi Object.
- **OpenAI 4:** jenis permintaan dan hal spesifik lain (misalnya kebutuhan kunci atau kredensial) akan dijelaskan di halamannya sendiri, termasuk dalam bentuk callout. Tanyakan kepada saya.

**Chrono**
- **Delay:** menunda aliran dengan waktu yang dapat ditentukan. Selama penundaan, state block menjadi Waiting. Satuan, rentang, dan batas durasi belum diketahui.

**Error**
- **Error Message:** membuat error baru dengan pesan yang dimodifikasi. Saat tereksekusi, seluruh aliran dihentikan dan pesan error muncul sebagai output di Flow Activity. Block ini memengaruhi status Error/Fatal Error, tetapi status mana yang dihasilkan belum diketahui.

## Struktur halaman (usulan awal, skill menang jika berbeda)

Gunakan templat halaman Flow Block di skill. Bila skill belum mendefinisikannya secara rinci, gunakan kerangka berikut dan sesuaikan dengan sifat tiap block:

1. Front matter, callout note pengenalan (block ini bagian dari kategori mana, tautkan ke halaman Pengenalan kategorinya), paragraf definisi singkat.
2. Gambar block (placeholder `![[...png]]` dengan TODO penempatan gambar dan anotasi bernomor).
3. **Input dan Output:** tabel input dan output sesuai antarmuka (label persis seperti di aplikasi, tipe data ditautkan). Perhatikan aturan Output Flow Block pada `Flow Block/Pengenalan#Antarmuka Flow Block`.
4. **Cara Kerja** (apa yang terjadi saat block tereksekusi, perilaku saat input kosong atau tidak cocok).
5. **Contoh Penggunaan** dengan diagram alur Flow bergaya mermaid sesuai aturan di skill dan nama contoh generik.
6. **Praktik Terbaik**, serta **Batasan dan Catatan**.
7. **Lihat Juga** (kategori, Flow Block, Syarat Flow Block Diproses, block terkait, Flow Activity).

Halaman yang sederhana (misalnya Pad Left dan Pad Right, Stringify dan Parse) boleh dibuat ringkas dan saling menautkan, jangan menulis ulang konsep yang berlaku umum untuk semua block.

## Cara kerja yang saya minta

1. **Bertanya dulu, dalam satu pesan bernomor** (maksimal sekitar 15 pertanyaan paling penting) untuk hal yang belum ada di knowledge atau lampiran, misalnya: daftar input dan output tiap block sesuai antarmuka, tipe data input/output, perilaku bila input kosong, kolom konfigurasi (Control atau *field*), If, OpenAI 4, satuan Delay, status Error Message. Bila saya melampirkan screenshot atau JSON, bacalah lebih dulu agar pertanyaan tidak berulang.
2. Setelah saya menjawab, kerjakan **bertahap per kategori** dengan urutan: Input dan Output, Query, Chrono, Error, Modular, lalu Operator (Number, String, Table, Object, Boolean, Tree). Bila keluaran terlalu panjang, berhenti di akhir satu kategori dan lanjutkan saat saya mengetik "lanjut".
3. Output berupa file `.md` per halaman, disusun dalam struktur folder sesuai path di atas (satu file per block), lalu dikemas dalam satu zip pada akhir pekerjaan.
4. Status halaman `draft`. Front matter tanpa ikon. Tulis tanpa indentasi di awal baris.
5. Hal yang belum pasti ditandai TODO (satu TODO per pertanyaan, di tempat yang relevan). Jangan membuat ulang TODO yang sudah saya jawab. Saya akan menjawab di bawah TODO dengan awalan "Jawaban:" dan menandai yang selesai dengan `[DONE]`.
6. **Cek konsistensi** setelah halaman selesai: tautan, alias, dan path sama persis dengan enam halaman kategori; fungsi block pada halaman block tidak bertentangan dengan tabel Fungsi di halaman kategori. Bila ada pertentangan atau halaman kategori perlu diperbarui, **jangan ubah diam-diam**. Tuliskan usulan perubahannya di akhir.
7. Nama contoh pada screenshot saya adalah kasus pribadi dan tidak boleh disebut di dokumentasi. Buat nama contoh generik dan tandai TODO agar gambar disesuaikan.
8. Akhiri dengan: (a) daftar singkat hal yang perlu saya cek, (b) **Usulan update `/phoenix-docs-silverbullet`** dan **Usulan update skill `/phoenix-docs-knowledge`** untuk informasi baru yang saya berikan, masing-masing dengan alasan dan disertai file `.md` agar mudah dipasang.

Mulai dengan membaca lampiran dan skill, lalu ajukan pertanyaan pada langkah 1.
---
  pageDecoration:
    tree:
      priority: -17
  tags:
    meta
    prompt
---
/phoenix-docs-silverbullet /phoenix-docs-knowledge

![[prompt/2026-11-09_02-29-03.png]]
Tolong buatkan **8 halaman Flow Block** untuk dokumentasi Phoenix, yaitu halaman per block yang menjadi tujuan tautan pada enam halaman Pengenalan kategori Flow Block yang saya lampirkan (Input dan Output, Query, Modular, Chrono, Error). Enam halaman kategori itu sudah final dan menjadi sumber kebenaran untuk fungsi tiap block, istilah, path, dan alias tautan.

## Daftar halaman

Seluruh path berada di bawah `Docs/Modul Logic/Flow/Flow Block/`. Alias tautan mengikuti tabel pada halaman kategori.

| No | Kategori | Path | Alias tautan |
| --- | --- | --- | --- |
| 1 | Input dan Output | `Input dan Output/Branch` | Branch Block |
| 2 | Input dan Output | `Input dan Output/Passer` | Passer Block |
| 3 | Query | `Query/Condition/Equal Condition` | Condition Query Block |
| 4 | Query | `Query/Execute/Table Get Id` | Execute Query Block |
| 5 | Modular (API) | `Modular/API/HTTP Request` | HTTP Request API Block |
| 6 | Modular (AI) | `Modular/AI/OpenAI 4` | OpenAI 4 AI Block |
| 7 | Chrono | `Chrono/Delay` | Delay Chrono Block |
| 8 | Error | `Error/Error Message` | Error Message Block |

## Input dan Output

Branch dan Passer memiliki banyak block yang fungsi nya sama, hanya berbeda di jumlah input atau output, sehingga tidak perlu dijelaskan per masing-masing block (9 halaman), cukup dengan 2 halaman (branch dan passer).

**Branch 2 sampai 5**
Memiliki input data apapun, dalam bentuk field ada N/A Type yang perlu diubah. Output adalah aliran keluar yang berisi data input, dimana output yang memiliki aliran lanjut ke block lain adalah output yang memiliki koneksi, urutan aliran mulai dari Output 2, Output 3 dan seterusnya. Jika ada beberapa output (bahkan ditengah sekalipun) yang tidak memiliki koneksi akan tidak mengeluarkan output data. Error tidak mungkin terjadi, namun dapat Fatal Error jika Input dibiarkan N/A Type.

**Passer 1 sampai 5**
Memiliki output n yang sesuai dengan data input n, aturan output mengalirkan data ke block lain adalah seperti Branch Block. Harus dibuat catatan juga bahwa input bisa jadi tidak berguna jika koneksi yang meneruskan data tersebut tidak memiliki koneksi, dan sebaliknya jika Output memiliki koneksi namun Input dibiarkan N/A Type, maka akan menghasilkan Fatal Error.

## Query

**Equal Condition** 


**Execute**
menjalankan Query. Tidak ada kaidah Output tertentu, bentuk hasil mengikuti cara Query dirangkai.


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
---
  pageDecoration:
    tree:
      priority: -17
  tags:
    meta
    prompt
---
2026-11-09 02:00

/phoenix-docs-silverbullet /phoenix-docs-knowledge

![[prompt/2026-11-09_03-07-35.png]]
Tolong buatkan **8 halaman Flow Block** untuk dokumentasi Phoenix, yaitu halaman per block yang menjadi tujuan tautan pada lima halaman Pengenalan kategori Flow Block (Input dan Output, Query, Modular, Chrono, Error).

## Daftar halaman

Seluruh path berada di bawah `Docs/Modul Logic/Flow/Flow Block/`. Alias tautan mengikuti tabel pada halaman kategori.

| No | Kategori | Path | Alias tautan |
| --- | --- | --- | --- |
| 1 | Input dan Output | `Input dan Output/Branch` | Branch Block |
| 2 | Input dan Output | `Input dan Output/Passer` | Passer Block |
| 3 | Query | `Query/Condition/Add Table Filter` | Query Add Table Filter Block |
| 4 | Query | `Query/Execute/Table Output` | Query Table Output Block |
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

**Add Table Filter** 
Memiliki input Query untuk ditambahkan filter table. AND adalah input bertipe boolean, true artinya kondisi AND, dan false untuk OR. Column adalah input bertipe column. Operator adalah input string dengan simbol operator yang valid (arahkan ke [[Docs/Query/Filter/Operator]]). Operand adalah data pembanding dari nilai column yang diinput dengan tipedata yang harus valid (arahkan ke [[Docs/Query/Filter/Operand]]). Fatal Error dapat terjadi jika ada nilai yang dibiarkan kosong (Operand dibiarkan N/A Type, karena empty dengan bertipe data dianggap valid). Error dapat terjadi jika aturan mengisi operator atau operand tidak sesuai, atau Query yang diinput memiliki base yang bukan data Table. Output dari blok ini hanya Query dengan bertipe data Query, yaitu hasil penambahan filter dari query input.

**Table Output**
Memiliki input Query, yang harus menggunakan kaidah [[Docs/Query/Output/Table]]. Fatal Error jika dibiarkan kosong. Output hasilnya adalah Rows yaitu array dengan bertipe Row (berisi setidaknya 1 row), sedangkan Is Empty adalah output boolean jika hasilnya kosong.

## Modular

**HTTP Request**
Input method adalah bertipe string dengan metode http yang valid. Endpoint adalah input bertipedata string. Header adalah input dengan tipedata object yaitu bakal header dari request. Payload adalah input bertipedata object. Fatal Error jika method atau endpoint dibiarkan kosong. Success adalah output bertipedata object jika hasilnya json dan text jika hasilnya html. Error adalah ketika ada respon error dari hasil request, bertipe data object. 

**OpenAI 4**
Input API Key bertipe string, Model bertipe string, Input bertipe text, Messages bertipe object, Tools bertipe object, Tool Choice bertipe object, Max Output bertipe number, dan Temperatur bertipe number. Output dapat Text (bertipe text) atau Function (bertipe json dan jika tools), atau Error jika ada respon error dari OpenAI. Fatal Error hanya terjadi jika API Key, Model, Max Output dan Temperature dibiarkan kosong. 

## Chrono

**Delay**
Input duration bertipe number (dalam satuan detik). dan Output Finish bernilai boolean true jika delay sudah selesai. Selama delay menunggu, status dalam Activity terlihat Waiting. Fatal Error jika duration dibiarkan kosong.

## Error

**Error Message**
Input message bertipe text.

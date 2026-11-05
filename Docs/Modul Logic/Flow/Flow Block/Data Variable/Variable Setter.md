---
status: draft
title: Variable Setter
description: Flow Block untuk memperbarui Value pada Variable Data.
pageDecoration:
  icon: save
  tree:
    priority: 5
---
# Variable Setter

>**note** Variable Setter merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Variable Setter adalah [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] untuk memperbarui [[^field|Value]] pada [[Docs/Modul Data/Variable/Apa itu Variable|Variable Data]] dari dalam [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]]. Dengan block ini, nilai yang menjadi sumber kebenaran dapat berubah otomatis tanpa Anda membuka halaman kerja [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]. Block ini memiliki dua input di sisi kiri dan satu output di sisi kanan.

![[Docs/Modul Logic/Flow/Flow Block/Data Variable/variable-setter-block-flow.png|Flow Block Variable Setter dengan dua input dan satu output]]
## Input dan Output

Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Variable]] | [[Docs/Tipe Data/Variable]] | Variable Data yang akan diperbarui. Isi dengan Variable Data atau hubungkan dari output block lain, misalnya [[^output|Variable]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]. |
| [[^field|New Value]] | Sesuai Type Variable Data | Nilai baru yang akan disimpan ke Value Variable Data. |

### Output

| Output | Tipe Data | Fungsi |
| ------ | --------- | ------ |
| [[^output|Pass]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila Value berhasil diperbarui. |

## Cara Kerja

1. Block menerima Variable Data dari [[^field|Variable]] dan nilai dari [[^field|New Value]].
2. Block mengganti [[^field|Value]] Variable Data dengan [[^field|New Value]].
3. Block mengirim [[^output|Pass]] sebagai tanda proses selesai.

Hanya Value yang berubah. [[^field|Name]], [[^field|Type]], dan [[^field|Description]] Variable Data tetap sama.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Pembaruan lewat Variable Setter tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Variable Event|Variable Event Block]] dengan event [[^value/string|update]], sehingga tidak ada Flow yang berjalan karena pembaruan ini.

## Contoh Penggunaan

| Kondisi | Value Variable Data | [[^output|Pass]] |
| ------- | ------------------- | ---------------- |
| [[^field|Variable]] berisi Variable Data [[^value/string|batas_stok_minimum]] dengan nilai [[^value/number|50]], dan [[^field|New Value]] berisi [[^value/number|100]] | Berubah menjadi [[^value/number|100]] | [[^value/boolean/true]] |
| [[^field|Variable]] kosong atau tidak valid | Tidak berubah | [[^value/empty]] |

Hubungkan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]] ke [[^field|Variable]] dan hasil perhitungan, misalnya dari [[Docs/Modul Logic/Flow/Flow Block/Operator/Number/Increment|Increment Operator Block]], ke [[^field|New Value]] untuk membuat penghitung yang bertambah setiap Flow berjalan.

## Praktik Terbaik

- **Pastikan tipe data [[^field|New Value]] sesuai Type Variable Data** yang menjadi target.
- **Ambil Variable Data dengan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]** agar Anda dapat menangani Variable Data yang tidak ditemukan sebelum memperbarui nilainya.
- **Periksa [[^output|Pass]]** sebelum menjalankan block yang bergantung pada nilai terbaru.

## Batasan dan Catatan

- Variable Setter hanya mengubah Value. Untuk membuat Variable Data baru, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Add Variable|Add Variable Block]].
- Satu eksekusi memperbarui satu Variable Data.
- Variable Setter adalah block non-Event, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- Anggota yang tidak memiliki akses ke komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] tetap dapat mengubah Value lewat Flow.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]]
- [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]
- [[Docs/Tipe Data/Variable]]

<!--
  * [DONE] Letakkan screenshot block Variable Setter sebagai `variable-setter-block-flow.png` di folder `Docs/Modul Logic/Flow/Flow Block/Data Variable/`. Anotasi yang disarankan: nomor 1 dan 2 untuk input Variable dan New Value, nomor 3 untuk output Pass.
  * [TODO] Pada screenshot, input New Value tampil "Empty" (abu-abu), tidak seperti Value pada Add Variable yang tampil N/A Type. Konfirmasi apakah tipe New Value otomatis mengikuti Type Variable Data yang dipilih, atau perlu didefinisikan lewat klik kanan, Change Type.
    Jawaban: maaf ternyata kesalahan saya, harusnya seperti Add Variable yaitu N/A dan perlu Change Type.
  * [TODO] Konfirmasi arti output Pass pada Variable Setter. Saya tulis sebagai Boolean true bila Value berhasil diperbarui.
    Jawaban: bukan, pass disini adalah mengeluarkan data yang diinput, karena konteks nya disini variable, maka isi pass adalah data bertipe variable
  * [TODO] Konfirmasi perilaku bila tipe data New Value tidak sesuai Type Variable Data (ditolak, dikonversi, atau error), serta bila Variable kosong atau tidak valid. Baris tabel Contoh Penggunaan untuk kasus tersebut adalah asumsi saya/
    Jawaban: New value juga memberikan new type, jadi tidak mungkin error. Variable kosong memungkinkan (akan menghasilkan error) tapi tidak valid itu tidak mungkin karena field variable adalah select option.
  * [TODO] Kalimat "Hanya Value yang berubah" dan catatan hak akses saya simpulkan dari fungsi block dan pengetahuan komponen Variable. Mohon konfirmasi.
    Jawaban: Sudah betul
-->

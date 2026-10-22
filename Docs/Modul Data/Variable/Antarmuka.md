---
    status: release
    title: "Antarmuka Enum"
    description: Penjelasan antarmuka di halaman kerja komponen Enum
    pageDecoration:
      tree:
        priority: 0.5
---
# Antarmuka Enum

![[Docs/Modul Data/Variable/interface-variable.png]]
Halaman kerja Variable terdiri dari bilah navigasi di bagian atas dan tabel Variable di bagian bawah.

Bilah navigasi Variable terdiri dari:

| Elemen | Fungsi |
| --- | --- |
| [[^field/variable|Variable]] | Judul komponen, menampilkan ikon Variable dan nama komponen. |
| [[^button/refresh|Refresh]] | Memuat ulang data pada tabel Variable. |
| [[^field|Search Variable Data...]] | Mencari data Variable pada tabel. |

Kolom pada tabel Variable adalah:

| Kolom | Penjelasan | Pengisian |
| --- | --- | --- |
| [[^field|Name]] | Nama Variable. Tidak boleh sama dengan baris lain. | Diisi oleh Anda |
| [[^field|Type]] | Tipe data dari nilai yang disimpan, misalnya [[Docs/Tipe Data/String\|String]]. | Diisi oleh Anda |
| [[^field|Value]] | Nilai yang disimpan, menyesuaikan Type. | Diisi oleh Anda |
| [[^field|Description]] | Keterangan tentang kegunaan Variable. | Diisi oleh Anda |
| [[^field|Created At]] | Waktu baris dibuat. | Terisi otomatis |
| [[^field|Updated At]] | Waktu baris terakhir diperbarui. | Terisi otomatis |

Pada area tabel terdapat:

| Tombol | Fungsi |
| --- | --- |
| [[^button/add|Add Row]] | Menambahkan baris [[Docs/Tipe Data/Variable|Variable Data]] baru. |
| [[^button/save|Save]] | Menyimpan perubahan data. |
| [[^button/delete|Delete]] | Menghapus data. |

## Interaksi Antarmuka Variable

| Fungsi | Aksi |
| --- | --- |
| Melihat kolom di sisi kanan tabel | Geser tabel secara horizontal menggunakan *scroll* di bagian bawah tabel. |


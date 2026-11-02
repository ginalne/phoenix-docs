---
    status: release
    title: "Aturan Koneksi"
    description: 
    pageDecoration:
      tree:
        priority: 5
---
# Aturan Koneksi

Koneksi menghubungkan [[#Output]] sebuah block ke [[#Input]] atau [[#Trigger]] block lain. Jumlah koneksi yang diizinkan berbeda untuk setiap bagian:

| Bagian | Jumlah koneksi |
| --- | --- |
| [[#Output]] | Hanya terhubung dengan satu Input atau Trigger block lain |
| [[#Input]] | Dapat menerima koneksi sebanyak mungkin |
| [[#Trigger]] | Dapat menerima koneksi sebanyak mungkin |

Setiap koneksi harus memiliki tipe data yang cocok antara Output dan Input. Output dapat menghasilkan beberapa kemungkinan tipe data, dan Input yang lebih ketat tetap dapat menerimanya. Namun, jika data yang mengalir ternyata tidak cocok, error akan muncul di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]].

Langkah menghubungkan dan memutus koneksi ada di [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi]] dan [[Docs/Modul Logic/Flow/Flow Block/Menghapus Koneksi]].
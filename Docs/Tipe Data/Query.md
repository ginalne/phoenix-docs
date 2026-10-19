---
    status: release
    title: "Query"
    description: 
    pageDecoration:
      tree:
        priority: 0
---
# Query
Tipe data yang dapat menyimpan konfigurasi penampilan data dengan kombinasi yang kompleks seperti meringkas, menyaring, menyortir serta menghitung jumlah hingga rata-rata ataupun akumulasi dari beberapa dataset sesuai dengan kondisi yang diinginkan.

## Penggunaan dalam Interface
Query cukup baik dalam menyimpan konfigurasi penampilan data sehingga digunakan sebagai delegasi dari subkomponen dalam interfacese seperti dalam [[Docs/Modul Interface/Timeline/Apa itu Timeline|Timeline]], [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]] dan [[Docs/Modul Interface/Space/Apa itu Space|Space]]

## Format
>**note** Tipe data ini tidak memiliki format khusus.

## Error

Konfigurasi yang dirumuskan dalam Query dapat tidak sesuai dengan permintaan ataupun hasilnya. Berikut adalah beberapa pesan error yang tampil sesuai dengan penyebabnya.

| Pesan Error | Penyebabnya |
| ---------------- | -------------------- |
| Query column output is not valid | Hasil Query bukanlah data yang bersifat Table Row, bisa dikarenakan Header yang salah (bukan Table) atau belum diisi. |

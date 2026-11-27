---
    status: release
    title: "Cara Kerja Flow"
    description: Penjelasan cara kerja komponen Flow
    pageDecoration:
      tree:
        priority: 3
---
# Cara Kerja Flow
Flow Block Event memicu proses, lalu hasilnya mengalir lewat koneksi dari satu Flow Block ke Flow Block berikutnya hingga menghasilkan keluaran.

```mermaid
flowchart TB
    Komponen["Komponen Data<br/>(Variable, Enum, Table, Tree)"] -.->|Event| BE["Flow Block (Event)"]
    Manual["Tombol pada Flow Block Event<br/>(eksekusi manual)"] --> BE
    BE -->|Output ke Input| B1["Flow Block"]
    B1 -->|Output ke Input| B2["Flow Block"]
    B2 --> Hasil["Keluaran / otomasi"]
    BE -.->|Dipantau| Act["Activity"]
    B1 -.->|Dipantau| Act
    B2 -.->|Dipantau| Act
```

Flow Block hanya terhubung dari output ke input. Garis putus-putus menandakan relasi yang tidak selalu dipakai, misalnya Flow Block Event yang dipicu dari komponen data atau dijalankan manual.
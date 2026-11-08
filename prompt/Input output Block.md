---
  pageDecoration:
    tree:
      priority: -16
  tags:
    meta
    prompt
---
2026-11-08 21:30

![[prompt/Screenshot_20261108_192341.jpg]]
/phoenix-docs-silverbullet /phoenix-docs-knowledge 

Tolong saya membuat 2 halaman flow block untuk kategori Input Output:

**Branch 2 sampai 5**
Memiliki input data apapun, dalam bentuk field ada N/A Type yang perlu diubah. Output adalah aliran keluar yang berisi data input, dimana output yang memiliki aliran lanjut ke block lain adalah output yang memiliki koneksi, urutan aliran mulai dari Output 2, Output 3 dan seterusnya. Jika ada beberapa output (bahkan ditengah sekalipun) yang tidak memiliki koneksi akan tidak mengeluarkan output data. Error tidak mungkin terjadi, namun dapat Fatal Error jika Input dibiarkan N/A Type.

**Passer 1 sampai 5**
Memiliki output n yang sesuai dengan data input n, aturan output mengalirkan data ke block lain adalah seperti Branch Block. Harus dibuat catatan juga bahwa input bisa jadi tidak berguna jika koneksi yang meneruskan data tersebut tidak memiliki koneksi, dan sebaliknya jika Output memiliki koneksi namun Input dibiarkan N/A Type, maka akan menghasilkan Fatal Error.
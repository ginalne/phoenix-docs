---
    status: draft
    pageDecoration:
      tree:
        priority: -3
---
# Welcome to Phoenix Docs
Sebagai pembaca saya harap anda dapat mengabaikan pesan ini, berikut adalah aturan yang berlaku saat menulis dokumentasi ini:

## Frontmatter
frontmatter adalah section dalam penulisan dokumentasi yang dibuka dengan “---” dan ditutup dengan “---”, isi dari frontmatter ditulis dengan format YAML. 

Berikut adalah atribut penting yang bisa atau wajib digunakan.

1. Status
   *status* adalah atribut untuk penanda status halaman dengan nilai seperti berikut:
   * draft    : jika halaman belum dipublish ke website.
   * released : jika halaman dipublish ke website

2. pageDecoration.icon
   ditulis dengan format seperti berikut
   ```yaml
   pageDecoration:
      icon: something...
   ```
   wajib diisi dengan “x” jika status draft, atau diisi “folder” untuk folder. jangan gunakan jika release atau tidak dibutuhkan (dapat gunakan # agar bersifat notes)
   
3. pageDecoration.icon
   ditulis dengan format seperti berikut
   ```yaml
   pageDecoration:
      tree:
        priority: some number...
   ```
   wajib diisi dengan “x” jika status draft, atau diisi “folder” untuk folder. jangan gunakan jika release atau tidak dibutuhkan (dapat gunakan # agar bersifat notes)

   
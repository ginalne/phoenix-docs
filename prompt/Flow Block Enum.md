---
  pageDecoration:
    tree:
      priority: -15
  tags:
    meta
    prompt
---
2026-11-05 23:00

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/data-enum-block-flow.png|Tujuh Flow Block Data Enum pada Blueprint: Add EnumData, Delete EnumData, Enum, EnumData, EnumData Getter, EnumData Setter, dan EnumData Value]]

/phoenix-docs-silverbullet /phoenix-docs-knowledge 

Tolong saya membuat 6 halaman flow block untuk data variable:

1. Add Enum
   Input, Value, Description adalah field untuk bakal atribut variable. jika name conflict. new variable = empty dan  name conflict = boolean true.
2. Delete EnumData
   Variable adalah input bertipedata variable untuk target variable yang akan dihapus. Force adalah input bertipedata boolean (true jika ingin dihapus secara paksa - berakibat dengan relasi dan histori yang sudah ada). Succeed = boolean true dan Error empty jika berhasil, begitu sebaliknya.
3. Enum
   Variable adalah input bertipedata variable.
4. Variable Getter
   Name adalah input bertipedata string, sebagai alias (exact match). Variable terisi jika name cocok, dan Is Empty = empty, jika gagal variable = empty dan Is Empty = boolean true.
5. Variable Setter
   Variable adalah input bertipedata variable. New Value adalah value yang akan diupdate ke variable.
6. Variable Value
   Variable adalah input bertipedata variable. Value adalah output data langsung (tipe data mengikuti sumber value).

Catatan untuk Calude:
Infomasi mengenai N/A Type, adalah tipe yang belum didefinisi. cara pendefinisiannya adalah dengan klik kanan -> Change Type -> lalu pilih tipe data.
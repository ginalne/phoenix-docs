---
  tags: meta/library
---

```space-style
table {
  border-radius: 15px;
  overflow: hidden;
  border: 1px solid #333;
}
html{
    body table {--editor-wiki-link-page-color: #818181;}
    body thead td {
      border: 1px solid #666;
      background: #2a2a2a;
      padding:6px 12px !important;
      color: #bbb;
    }
    body tbody tr:nth-child(even) {
      background-color: #161616;
    }
    body tbody tr:nth-child(odd) {
      background-color: #141414;
    }
    body tbody td {
      border: 1px solid #333;
      padding:12px !important;
      white-space: pre-wrap !important;
    }
}
```

Run ${widgets.commandButton "System: Reload"} to reload.
```space-style
/* Coret teks task dengan status DONE */
#sb-main .cm-editor [data-task-state="DONE"] ~ .sb-task {
  text-decoration: line-through !important;
  opacity: .5 !important;
  color: #AF2 !important;
}
/* Warnai orange terang */
#sb-main .cm-editor [data-task-state="TODO"] ~ .sb-task {
  color: #FF5 !important;
}
/* Warnai kuning terang */
#sb-main .cm-editor [data-task-state="PROGRESS"] ~ .sb-task {
  color: #FA2 !important;
}
/* Buat task yang diceklist menjadi redup */
#sb-main .cm-editor .cm-task-checked .sb-task {
  opacity: .5 !important;
}
#sb-main .cm-editor .cm-line,
#sb-main .cm-editor .sb-nav-content {
  /*font-family:"Segoe UI" !important;*/
  font-family: "Inter", sans-serif !important;
}

#sb-root {
  --ui-font: "Inter", sans-serif;
}
#sb-root .cm-editor .sb-line-fenced-code {
  font-family: monospace !important;
}
#sb-root .sb-nav-primary {
  font-weight:500 !important;
}
```

lihat selengkapnya [[Docs/Modul Interface/Table View/Apa itu Table View]].

Run ${widgets.commandButton "System: Reload"} to reload.

* [[field|Enable to insert externally]] : Tidak ketat, Enum Data bisa ditambahkan oleh pengguna...

[[field|Disabled to insert externally]] : Tidak ketat, Enum Data bisa ditambahkan oleh pengguna...

```space-style
#sb-main .cm-editor a[href^="field"] {
  display:inline-block !important;
  padding: 6px 8px;
  margin: 2px 0px 6px 0px;
  border: 1px solid #555;
  border-radius: 5px;
  background: #333;
  color: #ddd !important;
  font-size: 0.95em;
  font-weight: 400;
  text-decoration: none !important;
  pointer-events: none;
  white-space: nowrap;
  line-height: 1rem;
}

#sb-main .cm-editor .sb-line-h1 a[href^="field"],
#sb-main .cm-editor .sb-line-li a[href^="field"],
#sb-main .cm-editor .sb-line-ul a[href^="field"] {
  display:inline !important;
  padding: 1.5px 8px;
}

```

```space-style
#sb-main .cm-editor a[href^="mode/"] {
  display:inline-block !important;
  position:relative;
  font-family:"Segoe UI";
  margin: 0.3rem 0.3rem;
  color: #bdbdbd !important;
  padding: 0.1rem 1rem 0.2rem 0.9rem;
  border: 1px solid rgb(63 63 70);
  font-weight: 500;
  font-size: 1.125rem;
  border-radius: 999px;
  background-color: #161616;
  pointer-events: none;
  white-space: nowrap !important;
  text-decoration: none;
}
#sb-main .cm-editor td a[href^="mode/"] {
  display:block !important;
}
#sb-main .cm-editor a[href^="mode/"]::before {
  content: "mode ";
  margin-right:10px;
  font-size: 1rem;
  font-weight: 100;
}
#sb-main .cm-editor a[href^="mode/"]:has(span)::after {
  position:absolute;
  left: 60px;
  top: 1px;
  content: "|";
  font-size: 1rem;
  font-weight: 100;
  opacity:.5;
}
#sb-main .cm-editor a[href^="mode/"] span {
  padding: 0rem .3rem 0rem 0.3rem;
}
#sb-main .cm-editor td:has(a[href^="mode/"]) {
  white-space:nowrap !important;
}
```

|  |  |
|----------|----------|
| [[mode/view|View]] | Saklar dengan mode View agar konten Form dapat di sunting. |

[[mode/edit|Edit]]

Run ${widgets.commandButton "System: Reload"} to reload.

test [[button/edit|Edit]]

> **warning** Warning
> Harap hati-hati saat [[button/refresh|Refresh]] halaman, pastikan bahwa perubahan Anda saat ini sudah disimpan. Jika tombol [[button/save|Save]]masih aktif, berarti perubahan belum disimpan.

```space-style
/* Style links starting with button: */
#sb-main .cm-editor a[href^="button/"] {
  display:inline-block !important;
  font-family:"Segoe UI";
  padding: 0.1rem 1rem 0.2rem 0.9rem;
  margin: 0.1rem 0.3rem;
  color: #bdbdbd !important;
  border: 1px solid rgb(63 63 70);
  font-weight: 500;
  font-size: 1.125rem;
  border-radius: 9999px !important;
  background-color: #161616;
  pointer-events: none;
  white-space: nowrap !important;
}
#sb-main .cm-editor i a[href^="button/"] {
  pointer-events: auto !important;
}
#sb-main .cm-editor a[href^="button/"] span {
  padding: 0rem 0.3rem 0rem 0rem;
}
#sb-main .cm-editor td:has(a[href^="button/"]) {
  white-space:nowrap !important;
}
```

Run ${widgets.commandButton "System: Reload"} to reload.

>**note**Tips
>Meskipun Enum Data bisa bertambah secara liar, namun atribut Name dalam EnumData tetap tidak dapat terduplikat. Meskipun akan banyak variasi Name yang mirip, Anda dapat menggunakan fitur [[Docs/Modul Data/Enum/EnumData Merge]] agar setiap data yang terelasi dengan EnumData tersebut dapat menjadi satu EnumData.

```space-style
#sb-main .cm-editor .sb-admonition {
  padding: 1rem 1.5rem;
}
#sb-main .cm-editor .sb-admonition-title {
  padding: 0.8rem 1.5rem;
}
#sb-main .cm-editor .sb-quote {
  margin: 0rem 0rem 0rem 0.5rem;
}
```
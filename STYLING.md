---
  tags: meta/library
---

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
```


Run ${widgets.commandButton "System: Reload"} to reload.

* [[field|Enable to insert externally]] : Tidak ketat, Enum Data bisa ditambahkan oleh pengguna...

[[field|Disabled to insert externally]] : Tidak ketat, Enum Data bisa ditambahkan oleh pengguna...

```space-style
#sb-main .cm-editor a[href="field"] {
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

#sb-main .cm-editor .sb-line-h1 a[href="field"],
#sb-main .cm-editor .sb-line-li a[href="field"],
#sb-main .cm-editor .sb-line-ul a[href="field"] {
  display:inline !important;
  padding: 1.5px 8px;
}
```

Run ${widgets.commandButton "System: Reload"} to reload.

[[button/edit|Edit]]

```space-style
/* Style links starting with button: */
#sb-main .cm-editor a[href^="button/"] {
  font-family:"Segoe UI";
  padding: 0.2rem 1rem 0.3rem 0.9em;
  color: #adadad !important;
  border: 1px solid rgb(63 63 70);
  font-weight: 500;
  font-size: 1.125rem;
  border-radius: 9999px;
  background-color: #161616;
  pointer-events: none;
}
#sb-main .cm-editor a[href^="button/"] span {
  padding: 0rem 0.3rem 0rem 0rem;
}
#sb-main .cm-editor div:has(a[href^="button"]) {
  display: inline-block;
  cursor: pointer;
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
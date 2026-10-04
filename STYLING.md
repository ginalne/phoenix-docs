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

* [[field|Enable to insert externally]] : Tidak ketat, Enum Data bisa ditambahkan oleh pengguna atau Anda saat melakukan input bebas terhadap Enum ini.

[[field|Disabled to insert externally]]

```space-style
#sb-main .cm-editor a[href="field"] {
  display:inline-block !important;
  margin:4px;
  padding: 6px 8px;
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
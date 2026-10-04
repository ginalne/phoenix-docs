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

[[field|Strict On Selected]]

```space-style
#sb-main .cm-editor a[href="field"] {
  display: inline-block;
  padding: 4px 7px;
  margin: 0 2px;
  border: 1px solid #555;
  border-radius: 5px;
  background: #333;
  color: #ddd !important;
  font-size: 0.88em;
  font-weight: 400;
  text-decoration: none !important;
  white-space: nowrap;
  pointer-events: none;
}
```

Run ${widgets.commandButton "System: Reload"} to reload.

[[button/edit|Edit]]

```space-style
/* Style links starting with button: */
#sb-main .cm-editor a[href^="button/"] {
  font-family:arial;
  padding: 0.5rem 3rem 0.5rem 3rem;
  color: #adadad !important;
  border: 1px solid rgb(63 63 70);
  font-weight: 600;
  font-size: 1.125rem;
  border-radius: 9999px;
  background-color: #161616;
  pointer-events: none;
}
#sb-main .cm-editor div:has(a[href^="button"]) {
  display: inline-block;
  cursor: pointer;
}
```
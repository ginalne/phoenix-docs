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

[[button/edit|Strict On Selected]]

```space-style
/* Style links starting with button: */
#sb-main .cm-editor a[href^="button/"] {
  padding: 0.5rem 1.25rem;
  box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  color: white;
  font-weight: 600;
  cursor: pointer;
  font-size: 1.125rem;
  border-radius: 9999px;
  transition:
    color 0.3s,
    background-color 0.3s;
  pointer-events: none;
  background-image: url('path-to-your-file.svg');
}
#sb-main .cm-editor div:has(a[href^="button/"]) {
  display: inline-block;
  cursor: pointer;
}
```
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

[[button:edit|Strict On Selected]]

```space-style
/* Style links starting with button: */
a[href*="button:"] {
  display: inline-block;
  padding: 4px 10px;
  border-radius: 6px;
  background: #2563eb;
  color: white !important;
  font-weight: 600;
  text-decoration: none !important;
}

/* Field labels */
.phx-field {
}

/* Button references */
.phx-button {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 4px 10px;
  margin: 0 2px;
  border: 1px solid #2563eb;
  border-radius: 6px;
  background: #2563eb;
  color: #fff !important;
  font-size: 0.88em;
  font-weight: 600;
  line-height: 1.5;
  white-space: nowrap;
}

/* Button icon */
.phx-button-icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-size: 1em;
}

/* Keyboard keys */
.phx-key {
  display: inline-block;
  min-width: 1.6em;
  padding: 1px 6px;
  border: 1px solid #a1a1aa;
  border-bottom-width: 2px;
  border-radius: 5px;
  background: var(--editor-widget-background, #f4f4f5);
  color: var(--editor-fg, #27272a);
  font-family: monospace;
  font-size: 0.85em;
  font-weight: 600;
  text-align: center;
  white-space: nowrap;
}

/* Navigation path */
.phx-nav {
  display: inline;
  font-size: 0.92em;
  font-weight: 500;
}

.phx-nav-separator {
  padding: 0 5px;
  color: #a1a1aa;
}

/* Dark theme adjustments */
/*.phx-field,
.phx-key {
  border-color: #52525b;
  background: #27272a;
  color: #e4e4e7;
}*/
```
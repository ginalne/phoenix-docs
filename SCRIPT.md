---
  tags: meta/library
---

This page holds configuration for your SilverBullet space. See [[^Library/Std/Config]] for all options and defaults.

Run ${widgets.commandButton "System: Reload"} to reload.

## User configuration
Anything you add to the block below is yours, edit freely.

```space-lua
-- Add custom configuration here, e.g.:
-- config.set("shortWikiLinks", false)
```

## Managed by the Configuration Manager
The block below is maintained by the ${widgets.commandButton("Configuration Manager", "Configuration: Open")}. Prefer editing it through the UI, although simple hand edits should survive.

```space-lua
-- managed-by: configuration-manager
config.set("markdownPrettify.emphasisMarker", "_")
```


```space-lua
-- priority: 10

slashCommand.define {
  name = "draft",
  run = function()
    editor.insertAtPos([==[---
    status: draft
    pageDecoration:
      icon: x
      tree:
        priority: 0
---
]==], 0, true)
  end
}

slashCommand.define {
  name = "released",
  run = function()
    editor.insertAtPos([==[---
    status: released
    title: 
    desciption: 
    pageDecoration:
      #icon: x
      tree:
        priority: 0
    tags:
---
]==], 0, true)
  end
}

slashCommand.define {
  name = "group",
  run = function()
    editor.insertAtPos([==[---
    status: group
    pageDecoration:
      icon: folder
      tree:
        priority: 0
---
]==], 0, true)
  end
}

slashCommand.define {
  name = "asking",
  run = function()
    local line = editor.getCurrentLine()

    local ws, prefix, rest =
      string.match(line.textWithCursor, "^(%s*)([%-%*]?)%s*(.*)$")

    local me = identity.own()
    
    local username = me and me.name or "unknown"
    local datetime = os.date("%Y-%m-%d %H:%M")

    local text = ws .. "<!--\n @" .. username .. " at " .. datetime .. " ${widgets.commandButton \"toggle mention\"}\n |^|\n-->"
    editor.replaceRange(line.from, line.to, text, true)
  end
}

slashCommand.define {
  name = "answer",
  run = function()
    local line = editor.getCurrentLine()

    if line.from <= 1 then
        return
    end
    
    local total_text = editor.getText()
    
    local idx = line.from - 1
    local username = nil
    local text_before = string.sub(total_text, 1, idx)
    local previous_line_text = string.match(text_before, "[^\n]*$")
    
    while idx >= 1 do
      editor.flashNotification(previous_line_text)
      username = string.match(previous_line_text, "@([%w_-]+)$")
      if username then
          break
      end
      idx = idx - 1
    end

    if username then
        editor.flashNotification("Username ditemukan di baris ke-" .. idx .. ": " .. username)
    else
        editor.flashNotification("Username tidak ditemukan di baris-baris atas.")
    end
  end
}



slashCommand.define {
  name = "todo task",
  run = function()
    local line = editor.getCurrentLine()
    local ws, prefix, rest = string.match(line.textWithCursor, "^(%s*)([%-%*]?)%s*(.+)$")
    editor.replaceRange(line.from, line.to, ws .. "* [TODO] " .. rest, true)
  end
}

```



<!--
 ginalne at 2026-10-02 19:29 ${widgets.commandButton "reply"}
 yes kenapa bang  

 
-->

Run ${widgets.commandButton "System: Reload"} to reload.

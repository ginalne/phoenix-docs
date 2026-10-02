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
    local text = ws .. "<!--\n `@" .. username .. "` at " .. datetime .. " ${widgets.commandButton \"toggle mention\"}\n \n-->"
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
    local lines = {}
    for s in string.gmatch(total_text, "[^\r\n]+") do
        table.insert(lines, s)
    end
    
    local current_line = editor.getCurrentLine()
    local current_line_text = current_line.text
    local current_line_index = 1
    for idx, text in ipairs(lines) do
        if text == current_line_text then
            current_line_index = idx
            break
        end
    end
    
    local idx = current_line_index - 1
    local username = nil
    
    while idx >= 1 do
        local check_text = lines[idx]
        if check_text == "<!--" then
          break
        end
      
        username = string.match(check_text, "@([%w_-]+)")
      
        if username then
            break
        end
        
        idx = idx - 1
    end
    
    if username then
      editor.flashNotification("we got you " .. idx .. "/" .. #lines .. " " .. username)
      while idx < #lines do
          local check_text = lines[idx]
          if check_text == "-->" then
            local updated_document = table.concat(lines, "\n")
            local total_text = editor.getText()
            editor.replaceRange(0, string.len(total_text), updated_document, true)
            break
          end
          idx = idx + 1
      end
    else
        editor.flashNotification("Tidak ditemukan pertanyaan apapun")
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
 `@ginalne` at 2026-10-02 20:01 ${widgets.commandButton "toggle mention"}
 
-->
Run ${widgets.commandButton "System: Reload"} to reload-
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
    local text = ws .. "<!--\n `@" .. username .. "` at " .. datetime .. " ${widgets.commandButton \"toggle mention\"}\n \n-->"
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
    local lines = {}
    for s in string.gmatch(total_text, "[^\r\n]+") do
        table.insert(lines, s)
    end
    
    local current_line = editor.getCurrentLine()
    local current_line_text = current_line.text
    local current_line_index = 1
    for idx, text in ipairs(lines) do
        if text == current_line_text then
            current_line_index = idx
            break
        end
    end
    
    local idx = current_line_index - 1
    local username = nil
    
    while idx >= 1 do
        local check_text = lines[idx]
        if check_text == "<!--" then
          break
        end
      
        username = string.match(check_text, "@([%w_-]+)")
      
        if username then
            break
        end
        
        idx = idx - 1
    end
    
    if username then
      editor.flashNotification("we got you " .. idx .. "/" .. #lines .. " " .. username)
      while idx < #lines do
          local check_text = lines[idx]
          if check_text == "-->" then
            local updated_document = table.concat(lines, "\n")
            local total_text = editor.getText()
            editor.replaceRange(0, string.len(total_text), updated_document, true)
            break
          end
          idx = idx + 1
      end
    else
        editor.flashNotification("Tidak ditemukan pertanyaan apapun")
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
 `@ginalne` at 2026-10-02 20:01 ${widgets.commandButton "toggle mention"}
 
-->
Run ${widgets.commandButton "System: Reload"} to reload-
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
    local text = ws .. "<!--\n `@" .. username .. "` at " .. datetime .. " ${widgets.commandButton \"toggle mention\"}\n \n-->"
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
    local lines = {}
    for s in string.gmatch(total_text, "[^\r\n]+") do
        table.insert(lines, s)
    end
    
    local current_line = editor.getCurrentLine()
    local current_line_text = current_line.text
    local current_line_index = 1
    for idx, text in ipairs(lines) do
        if text == current_line_text then
            current_line_index = idx
            break
        end
    end
    
    local idx = current_line_index - 1
    local username = nil
    
    while idx >= 1 do
        local check_text = lines[idx]
        if check_text == "<!--" then
          break
        end
      
        username = string.match(check_text, "@([%w_-]+)")
      
        if username then
            break
        end
        
        idx = idx - 1
    end
    
    if username then
      editor.flashNotification("we got you " .. idx .. "/" .. #lines .. " " .. username)
      while idx < #lines do
          local check_text = lines[idx]
          if check_text == "-->" then
            local updated_document = table.concat(lines, "\n")
            local total_text = editor.getText()
            editor.replaceRange(0, string.len(total_text), updated_document, true)
            break
          end
          idx = idx + 1
      end
    else
        editor.flashNotification("Tidak ditemukan pertanyaan apapun")
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
 `@ginalne` at 2026-10-02 20:01 ${widgets.commandButton "toggle mention"}
 
-->
Run ${widgets.commandButton "System: Reload"} to reload-
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
    local text = ws .. "<!--\n `@" .. username .. "` at " .. datetime .. " ${widgets.commandButton \"toggle mention\"}\n \n-->"
    editor.replaceRange(line.from, line.to, text, true)
  end
}
slashCommand.define {
  name = "answer",
  run = function()
    local line = editor.getCurrentLine()
    local found = false
    if line.from <= 1 then
        return
    end
    
    local total_text = editor.getText()
    local lines = {}
    for s in string.gmatch(total_text, "[^\r\n]+") do
        table.insert(lines, s)
    end
    
    local current_line = editor.getCurrentLine()
    local current_line_text = current_line.text
    local current_line_index = 1
    for idx, text in ipairs(lines) do
        if text == current_line_text then
            current_line_index = idx
            break
        end
    end
    
    local idx = current_line_index - 1
    local username = nil
    
    while idx >= 1 do
        local check_text = lines[idx]
        if check_text == "<!--" then
          break
        end
      
        username = string.match(check_text, "@([%w_-]+)")
      
        if username then
            break
        end
        
        idx = idx - 1
    end
    
    if username then
      editor.flashNotification("we got you " .. idx .. "/" .. #lines .. " " .. username)
      while idx < #lines do
          local check_text = lines[idx]
          if check_text == "-->" then
            
local before_arrow = string.sub(check_text, 1, start_pos - 1)
local arrow_and_rest = string.sub(check_text, start_pos
local insert_text = "here the answer : |^|"
lines[idx] = before_arrow .. insert_text .. arrow_and_rest)
editor.flashNotification(lines[idx])

found = true
            
            break
          end
          idx = idx + 1
      end
    else
        editor.flashNotification("Tidak ditemukan pertanyaan apapun")
    end

    if found then
      -- Menggabungkan kembali array lines menjadi satu string utuh dipisahkan baris baru (\n)
      local updated_document = table.concat(lines, "\n")
      
      -- Update seluruh dokumen (dari indeks 0 hingga akhir teks saat ini)
      local total_text = editor.getText()
      editor.replaceRange(0, string.len(total_text), updated_document, true)
      
      editor.flashNotification("Teks berhasil ditambahkan sebelum '-->'", "info")
    else
      editor.flashNotification("Tanda '-->' tidak ditemukan hingga akhir dokumen", "warn")
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
 `@ginalne` at 2026-10-02 20:01 ${widgets.commandButton "toggle mention"}
 
-->
Run ${widgets.commandButton "System: Reload"} to reload.
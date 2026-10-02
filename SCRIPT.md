---
    status: released
pageDecoration:
  icon: x
  tree:
    priority: 0
---

This page holds configuration for your SilverBullet space. See [[^Library/Std/Config]] for all options and defaults.
Run ${widgets.commandButton "System: Reload"} to reload.

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
    local text = editor.getText()

    -- Existing frontmatter
    local fmStart, fmEnd = string.find(text, "^%-%-%-\n")
    if not fmStart then
      -- No frontmatter: create it
      editor.insertAtPos([==[---
status: draft
pageDecoration:
  icon: x
  tree:
    priority: 0
---
]==], 0, true)
      return
    end

    local contentStart = fmEnd + 1
    local endStart, endEnd = string.find(text, "\n%-%-%-", contentStart)

    if not endStart then
      -- Invalid/incomplete frontmatter, don't modify it
      return
    end

    local frontmatter = string.sub(text, contentStart, endStart - 1)

    -- status: draft
    if string.match(frontmatter, "\n?status%s*:") or string.match(frontmatter, "^status%s*:") then
      frontmatter = string.gsub(
        frontmatter,
        "([^\n]*status%s*:%s*)[^\n]*",
        "%1draft",
        1
      )
    else
      frontmatter = "status: draft\n" .. frontmatter
    end

    -- pageDecoration exists
    if string.match(frontmatter, "pageDecoration%s*:") then
      -- icon exists somewhere under pageDecoration
      local before, decoration, after =
        string.match(frontmatter, "^(.-pageDecoration%s*:\n)(.-)(\n[^%s].*)?$")

      if decoration and string.match(decoration, "\n%s+icon%s*:") then
        decoration = string.gsub(
          decoration,
          "(\n%s+icon%s*:%s*)[^\n]*",
          "%1x",
          1
        )
      else
        decoration = "  icon: x\n" .. decoration
      end

      frontmatter = before .. decoration .. (after or "")
    else
      frontmatter = frontmatter ..
        "\npageDecoration:\n" ..
        "  icon: x\n" ..
        "  tree:\n" ..
        "    priority: 0"
    end

    local newText =
      string.sub(text, 1, contentStart - 1) ..
      frontmatter ..
      string.sub(text, endStart)

    editor.setText(newText)
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
      icon: x
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
    local text = ws .. "<!--\n  `@" .. username .. "` <small style=\"opacity: 0.5\">at " .. datetime .. "</small>\n  |^| @everynyaw\n-->"
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
      
        username = string.match(check_text, "`@([%w_-]+)")
      
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
              local line = editor.getCurrentLine()
              local ws, prefix, rest =
                string.match(line.textWithCursor, "^(%s*)([%-%*]?)%s*(.*)$")
              local me = identity.own()
              
              local myUserName = me and me.name or "unknown"
              local datetime = os.date("%Y-%m-%d %H:%M")
              local text = ws .. "`@" .. myUserName .. "` <small style=\"opacity: 0.5\">at " .. datetime .. "</small>\n  |^| @" .. username
              editor.replaceRange(line.from, line.to, text, true)
            break
          end
          idx = idx + 1
      end
    else
        editor.flashNotification("Tidak ditemukan pertanyaan apapun")
    end
    if found then
      editor.flashNotification("Teks berhasil ditambahkan sebelum") 
    else
      editor.flashNotification("Tanda '-->' tidak ditemukan hingga akhir dokumen")
    end
  end
}
slashCommand.define {
  name = "todo task",
  run = function()
    local line = editor.getCurrentLine()
    local ws, prefix, rest = string.match(line.textWithCursor, "^(%s*)([%-%*]?)%s*(.+)$")
    local me = identity.own()
    local username = me and me.name or "unknown"
    if username == "unknown" then
      
    editor.replaceRange(line.from, line.to, ws .. "* [TODO] " .. rest, true)
    else
    editor.replaceRange(line.from, line.to, ws .. "* [TODO] " .. rest .. "[assignee: @" .. username .. "]", true)
    end
  end
}
```
Run ${widgets.commandButton "System: Reload"} to reload.
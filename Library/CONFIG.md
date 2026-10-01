---
command: "Journal: Daily Note"
name: Library/myuser/My Library
tags: meta/library
---


```space-lua
command.define {
  name = "Hello world",
  run = function()
    editor.flashNotification "Hello world!x"
    
  end
}
```
```space-lua
command.define {
  name = "Set Draft",
  run = function() 
    local pageName = _CTX.currentPage.name
    editor.flashNotification(pageName)
    local text = space.read_page(pageName)
    
    -- Simple replacement or insertion logic for frontmatter
    -- Example: updating a status attribute to "Done"
    local updatedText, count = string.gsub(text, "status:.*", "status: Done", 1)
    
    if count == 0 then
      -- If attribute doesn't exist, you can inject it after the opening '---'
      updatedText = string.gsub(text, "%-%-%-", "---\nstatus: Done", 1)
    end
    
    space.write_page(pageName, updatedText)
    editor.flashNotification("Frontmatter updated!")
  end
}
```

Hello World


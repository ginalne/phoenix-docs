---
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
    attribute.subAttribute: 10
  end
}
```

Hello World


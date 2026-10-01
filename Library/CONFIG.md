
```lua
config.set("frontmatterFolding", {
  foldByDefault = "always",
})

name: Library/myuser/My Library
tags: meta/library
---
This implements my super awesome hello world library!

```space-lua
command.define {
  name = "Hello world",
  run = function()
    editor.flashNotification "Hello world!"
  end
}
```
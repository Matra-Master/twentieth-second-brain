---
created: 20230905-1236
tags:
  - nvim
  - git
  - diffs
---
What will you discover today?
I found out about some key combos that make diff working easier, and they're present in Nvim out of the box!

`vert diffsplit <file>` this opens a file in a vertical split as a diff of the file I'm actually in

The logic works based on the file where I'm standing in, the other is "The Other"

`do` choose the change from the other file
`dp` choose my change and modify the other
`]c` go to next change
`[c` go to previous change

---
## Related Ideas:
* [[fleeting]]
* [[Neovim]]
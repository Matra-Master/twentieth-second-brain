---
created: 20240405-1530
tags:
  - Resources/projects
  - tmux
  - scripting
---

What will you discover today?

La idea es que cada proyecto tenga su color de status bar para poder diferenciarlos.

Encontré un post donde sugerían una función de bash que haga el set al abrir la sesión. Eso funcionaría con mis scripts actually
```shell
function init-blog {
  cd ~/projects/blog
  tmux new-session -d -s blog
  tmux set -t blog status-style bg=colour22,fg=colour255
  tmux attach-session -t blog
}
```

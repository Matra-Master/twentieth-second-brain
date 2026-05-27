---
created: 20220701-1757
tags:
  - neovim
  - clockify

---

# Neovim and Clockify integration

It doesn't exist, yet
I can combine Clockify-cli with neovim maybe

Listing all projects could be useful but the prompt is all tabulated pretty and is not easily usable as a list

	clockify-cli project list

It was on the `--help` part of the project listing
`-v` is for printing in csv format. There's also a json one. It should be enough to parse through `sed` and then to `fzf` we go

	clockify-cli project list -v

---
# References
[Clockify-cli](https://github.com/lucassabreu/clockify-cli)

---
title: Rice 002 - The learning how to properly rice one
---

# Definitions

_RICE means "race inspired cosmetic enhancement"_

The first purpose of a rice was to **look good**. Ergonomics and actual performance were secondary goals.

# Objectives

We are not modifying cars here so this is my **list of priorities**:

1. Look good
2. Be workable on
3. Have centralized configs

The long term goal is to have a desktop environment that I don't want to modify much so I can use it just for work.
For that the scope should be reduced to the absolute minimum parts and software. Apps directly related to work take precedence over my own funny sofware.
Also, since this is for work anything I do has to work in some way with the mouse. It doesn't need to be directly visible though, just accessible.

 ## Software priorities

1. Directly work related
  - Terminal
  - Neovim
  - Two Browsers
  - pnpm
  - docker
  - git
  - whatever, etc
2. Software that improves my work mood
  - Music, DeadBeef
  - 
3. Rice related software
  - color scheme manager
  - window manager
  - toolbars software
  - notification manager
  - some super menu
  - applications launcher
4. Anything else

## Challenges

The main challenge is the remote session thing. Wayland is not in a good state regarding remote desktop solutions, or at least nothing that I can make accionable remotely.
Chat is right on the money: I noticed I only need remote terminal access, not graphical access.
https://www.reddit.com/r/selfhosted/comments/18491e9/tailscale_the_marvellous_tool_that_became/ Here's someone on reddit talking about their experience with Tailscale.
So my best practical solution will be like this: Tailscale (mesh VPN) + SSH (or mosh) + tmux
Objectives of remote session are: unattended, reliable, work as if I'm in a terminal there.

# Aesthetics

## Themes

Two possible theming options:

1. Tuxdi theme. Based off of [Tuxdi main site](https://tuxdi.com/). This is a dark theme with purple and blue accents.
  -Figma has almost everything I need to create a palette from it.
  - [Coolors palette](https://coolors.co/17082f-af2eff-ffb800-ffffff-d88373) I generated an extra color just for fun.

## Scope

Aesthetics should be done mostly to desktop related stuff. Terminal is in scope but just up to window and shell coloring and theming.
Notifications, bars, menus, fonts, icons, file manager, wallpaper are in scope. I have to solve Qt vs Gtk but whichever I choose it's inside the scope
I can include also something like hellwal in scope with a bunch of premade themes for wallpapers; nothing more. I could make palettes based off of some accent color from projects :thinking:

For now, in terms of theming, scope is three themes: Tuxdi black, Tuxdi white, and Tuxdi Project X(working title, decide project later).

# Inspirations

# References



---
id: Pacman package replacements
aliases: 
tags:
  - pacman
  - linux
created: 20250127-1229
---

# Conflict between "-git" packages and some from the arch repos

Empezó como un día normal de actualizar repos. Resulta que en mi ignorancia cuando instalé `hyprland` normal y `hyprlang-git`
Tener un par de paquetes "-git" al ado de otros normales que son dependientes de ellos hace que al actualizar hyprland se queje
porque quiere actualizar su dependencia `hyprlang`, pero no puedo sacar `hyprlang-git` porque tiene dependencias de otros.

> **Solución a largo plazo**: Instalar todos `-git` o todos normales.

> **Solución de ahora**: operar los paquetes desde un tty (para no romper nada en uso), reemplazar `hyprlang-git` y sus dependientes
> con `hyprlang`

``` bash
pacman -Rd hyprlang-git # -d ignores dependency checks
pacman -S hyprlang
```

---
## Related Ideas
* [[permanent]]



## Sources


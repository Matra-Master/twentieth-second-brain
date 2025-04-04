---
created: "2025-03-20-10:25"
book: Programming in Lua 4ed.
author/s: Roberto Ierusalimschy
tags:
  - cite
  - book
  - Resources/lua
---

Hay dos formas de representar matrices en Lua.

La primera es la clásica del arreglo de arreglos de dimensiones NxM. Esta forma tiene la ventaja implícita de permitirte hacer matrices de formas flexibles manipulando los rangos durante la iteración. Por ejemplo una matriz triangular.

``` lua
  local mt = {}          -- create the matrix
  for i = 1, N do
    local row = {}       -- create a new row
    mt[i] = row
    for j = 1, M do
      row[j] = 0
    end
  end
```

La segunda, que había olvidado que existe, es componiendo dos índices en uno solo. Tenés un arreglo muuuy largo y lo que lo vuelve una "matriz" es la forma de recorrerlo con saltos en los índices.
Para hacer una matriz de NxM:

```lua
  local mt = {}          -- create the matrix
  for i = 1, N do
    local aux = (i - 1) * M
    for j = 1, M do
      mt[aux + j] = 0
    end
  end
```

---
## Connections
* [[]]


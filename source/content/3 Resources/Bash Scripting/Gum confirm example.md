---
tags:
  - snippets
  - bash
---
Se puede usar muchos _&&_ para hacer varias cosas una atras de otra, pero si no se confirma se sale por el _||_

``` bash
gum confirm \
&& rm file.txt \
&& touch whatever \
|| echo "Did nothing"
```

---
## Links:
* {{link}}
* [[]]
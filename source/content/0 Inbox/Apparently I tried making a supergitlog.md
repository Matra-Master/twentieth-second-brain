---
created: 20241018-1107
tags:
---

What will you discover today?
Encontré un script que traté de hacer. Recuerdo querer mostrar todos los commits que he hecho en mis repos locales, para poder rastrear qué hice en una semana. 
Ahora que lo veo es útil pero me va a faltar algo para que cumpla su objetivo: si solo muestro los commits logs no me va a mostrar lo que no tenga commiteado, o sea los cambios de stage. Tengo que incluirlo en la volteada.

Va lo que tengo del script:

```bash
#!/bin/bash
#Print the git log of every git repo in the contiguous directorys and subdirectories
# filtering by day
# usage: superlog.sh
# requires: git
START_DATE=$1
END_DATE=$2
AUTHOR=Franco

git log --oneline --author="$AUTHOR" --since="$START_DATE" --until="$END_DATE"

```


---
## Related Ideas:
* [[fleeting]]

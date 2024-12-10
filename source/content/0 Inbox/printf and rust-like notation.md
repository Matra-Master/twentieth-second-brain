---
created: 20241018-1044
tags:
  - bash
  - commands
---

What will you discover today?

Me crucé este comando en cht.sh 
```bash
tar -czvpf "$(printf '/media/%s/%s/%d:%d_%(%F)T.tgz' "$USER" 'DEVICE' ${UID:-`id -u`} ${GID:-`id -g`} -1)" "$HOME"
```

La parte importante es el printf, que aparentemente reconoce el parámetro `%s` como el reemplazo de cada uno de los strings que vienen luego O.O

O sea, simplificado:

``` bash
printf '/media/%s/%s/T.tgz' "$USER" 'DEVICE'

//Devuelve:
/media/$USER/DEVICE/T.tgz
```


---
## Related Ideas:
* [[fleeting]]
* [[]]
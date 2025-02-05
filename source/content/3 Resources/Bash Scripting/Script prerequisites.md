---
tags:
  - bash
  - commands
  - snippets
---
Snippet para chequear una lista de requirements. Si alguno no existe en el PATH del sistema te avisa y sale. Sale con el primero que encuentra

```bash
requirements=("npm" "rsync" "ssh")

for requirement in "${requirements[@]}"; do
  if ! command -v "$requirement" &> /dev/null 2>&1
  then
    echo "Instalar $requirement"
    exit
  fi
done
```

---
## Links:
* {{link}}
* [[]]
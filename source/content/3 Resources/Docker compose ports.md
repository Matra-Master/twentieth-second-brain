---
created: 20230814-1434
tags:
  - Resources/docker
  - Resources/docker-compose
---

What will you discover today?
According to [Compose File specification v3](https://docs.docker.com/compose/compose-file/compose-file-v3/) the usual *port* format is:

```
service:
  ports:
    "HOST:CONTAINER"
```

Datazo:
> Yaml parsea números menores a 60 como **valores en base 60**. Así que es recomendable siempre escribir los puertos como strings por las dudas.

---
## Related Ideas:
* [[Docker]]

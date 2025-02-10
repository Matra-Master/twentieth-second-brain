---
created: 20230814-1446
tags:
  - Resources/docker
  - Resources/docker-compose
---

What will you discover today?

[Compose File Specification - Profiles](https://docs.docker.com/compose/profiles/)

Parece que se puede crear profiles para usar ciertos grupos de servicios a la vez o.o

Ej: dejás un par de servicios (api y db) sin profile así se usan siempre, y luego le ponés profiles diferentes a distintos fronts. Levantás un profile un día y otro al siguiente y cambian los front o.O 
Ej2: El mismo servicio puesto dos veces en el compose. Uno target dev y otro target build, con perfiles aparte. Cuando el perfil de desarrollo levanta los devs y el de deploy te hace los builds sin tener que modificar el target!

---
## Related Ideas:
* [[fleeting]]
* [[Docker]]

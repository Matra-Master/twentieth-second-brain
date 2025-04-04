---
created: 20250319-1022
tags:
  - Resources/nginx
  - Resources/docker
  - Resources/docker-compose
---
La imagen de nginx **no soporta env variables**. Peeeero, tiene una función que usa `envsubst`  sobre los archivos `.template` que haya en la carpeta `/etc/nginx/tempaltes`, o sea que:

``` compose
web:
  image: nginx
  volumes:
   - ./templates:/etc/nginx/templates
  ports:
   - "8080:80"
  environment:
   - NGINX_HOST=foobar.com
   - NGINX_PORT=80
```

Un compose como este puede tener dos variables y una carpeta templates con un archivo `default.conf.template` que va a reemplazar al default.conf antes de que arranque el nginx dentro del contenedor :O

``` default.conf
  listen ${NGINX_PORT};
  server_name ${NGINX_HOST};
```
Se vuelve
``` default.conf
  listen 80;
  server_name foobar.com;
```


---

## Sources

https://hub.docker.com/_/nginx

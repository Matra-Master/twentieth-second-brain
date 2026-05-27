---
created: 20230901-1227
tags:
  - nginx
---
## Nginx Map para mostrar sitios diferentes

Encontré un post sobre cómo setear un nginx server para que te enrute a carpetas diferentes según la ip desde la que accedés a un dominio. O sea, podés mostrar prod a cualquiera y staging a los de la ip de la oficina.

``` nginx
map $remote_addr $root_yoursite{
    default /var/www/prodsite;
    YOUR_IP_ADDRESS /var/beta/stagingsite;
}
```

``` nginx
Server{
    listen 80;
    root $root_yoursite; # HERE
    server_name yourserver.com www.yourserver.com;

    index index.php index.html index;

    location /{
        try_files $uri $uri/ /index.php?q=$uri$args;
    }
}
```

El map cambia una variable en función de ciertas condiciones, en este caso el valor de $root_yoursite para cualquiera es `/var/www/` y para los de YOUR_IP_ADDRESS (que podría ser la ip de la oficina) es `/var/beta`


## Nginx Map para hacer redirecciones de sitios viejos

``` nginx
# Old website redirect map
map $uri $new_uri {
    /old.html /index.html;
}

server {
    listen 80 default_server;
    listen [::]:80 default_server;

    # Old website redirect
    if ($new_uri) {
        rewrite ^ $new_uri permanent;
    }
```

Si una persona pide old.html que puede ser cualquier dirección que hayamos movido, nginx puede devolverle la nueva en su lugar.
`$new_uri` es una variable que sólo se instancia en el config cuando `$uri` es igual a /old.html. Aparentemente es uno de los pocos casos donde es aceptable usar if en un conf de nginx

Incluso se puede usar map para bloquear por región geográfica :O

---
## Related Ideas:

[Reference](https://codefaq.org/server/how-to-create-staging-and-production-server-in-nginx/)
[Reference 2](https://www.digitalocean.com/community/tutorials/how-to-use-nginx-s-map-module-on-ubuntu-20-04)

---
created: 20230627-1420
tags:
  - Resources/docker
  - Resources/docker-compose
  - fleeting
---

Getting a secret into a container is a two-step process. First, define the secret using the [top-level secrets attribute in your Compose file](https://docs.docker.com/compose/compose-file/09-secrets/). Next, update your service definitions to reference the secrets they require with the [secrets attribute](https://docs.docker.com/compose/compose-file/05-services/#secrets). Compose grants access to secrets on a per-service basis.

Example: 
```yaml
secrets:
   db_password:
     file: db_password.txt
   db_root_password:
     file: db_root_password.txt
services:
   db:
     image: mysql:latest
     volumes:
       - db_data:/var/lib/mysql
     environment:
       MYSQL_ROOT_PASSWORD_FILE: /run/secrets/db_root_password
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD_FILE: /run/secrets/db_password
     secrets:
       - db_root_password
       - db_password
```


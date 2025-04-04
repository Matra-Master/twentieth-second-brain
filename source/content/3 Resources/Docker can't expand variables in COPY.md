---
created: "20250311-1358"
tags:
  - Resources/docker
---

la documentación no lo menciona directamente pero al parecer no es posible expandir variabes en un COPY o ADD dentro de un dockerfile. Lame.

``` dockerfile
COPY ./dockerfiles/.env .env  // valid 
ENV ANOTHER_ENV
COPY ./dockerfiles/$ANOTHER_ENV .env // invalid
```

Sí parecen hacer otras cosas facheras pero no eso.
https://docs.docker.com/build/building/best-practices/#add-or-copy


# I'm lame

Apparently I was missing the {} around that variable. Tried something like this and worked:

``` dockerfile
ENV ANOTHER_ENV_ROUTE=./dockerfiles/.env
COPY ${ANOTHER_ENV_ROUTE} .env
```

---

## Sources

My own experiments

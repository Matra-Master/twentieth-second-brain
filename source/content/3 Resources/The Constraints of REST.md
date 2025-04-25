---
created: "{{date:YYYYMMDD}}-{{time:HHmm}}"
book: Hypermedia Systems
author/s: Carson Gross, Adam Stepinski, Deniz Akşimşek
tags:
    - cite
    - book
    - Resources/rest
---

La persona que definió REST, Roy Fielding, disertaba sobre la arquitectura de la web; y lo describía en contexto comparando con otras arquitecturas existentes.
Hablaba sobre REST como una *arquitectura de red*, y hasta ese momento los sistemas distribuidos no se pensaban de esa forma.
Enfazis en esto: **Fielding describe REST en una época donde no existían las APIs.**


# Los Constraints de REST

- Arquitectura cliente-servidor
- Debe ser 'stateles'. O sea, cada request tiene que contener toda la información necesaria para reponder a la misma request.
- Debe permitir cacheo.
- Debe tener una *interfaz uniforme*.
- Es un sistema en capas.
- Opcionalmente, debe permitir *code-on-demand*, o sea, scripting.

---
## Connections

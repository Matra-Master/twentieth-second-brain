---
created: "202503251044"
author/s: Theo, from T3
video: https://youtu.be/d5x0JCZbAJs
tags: 
  - Resources/cite
  - Resources/video
---

Es un video de 3 horas que estoy siguiendo para un proyecto personal. Suuuper útil.
Tiene momentos que quiero preguntar a Patán y otros que mostrarle para ver si le sirven a los demás.

https://youtu.be/d5x0JCZbAJs?t=2110  Nextism: a deployed page get's cached on the server. The page is created only the **first time** somebody goes into it.
To solve this you can make any operation in the page that is clearly specific to the user, like requesting `headers();` or using auth related stuff.
But the better thing would be to use the new typescript bindings for NextJS like this:
```
export const dynamic = "force-dynamic";
```



---
## Connections


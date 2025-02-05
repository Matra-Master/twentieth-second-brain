---
tags:
---
# German strings explained

La idea va algo así.
### Usual strings
Se supone que un string es una concatenación de caracteres que puede ser de cualquier tamaño por lo cual en rust se los implementa como un vector de caracteres con tres propiedades:
- len. longitud del string
- cap. capacidad del buffer alocado en el heap para contener al string
- ptr. puntero a la locación de memoria donde está el buffer
Como un string es de tamaño dinámico estas propiedades cambian cuando se escriben más cosas dentro de un string. Rust aloca un bloque más grande, muda el string y desaloca el viejo.

### German strings
Se basan en que en el mundo real se dan las siguientes situaciones:
- La mayoría de los strings son cortos.
- La mayoría de los strings no suelen cambiar.
- Cuando se comparan u ordenan strings sólo se observa de a un pequeño substring a la vez.

Basado en esto se idearon optimizaciones en la estructura del string. German string tiene 2 representaciones según la longitud del string a guardar.

#### Corta

Usa 16 bytes: 4 para longitud y 12 para el actual string

#### Larga

Parecido al string normal pero con dos vueltas de rosca:
- Usa 4 bytes en vez de 8 para len. Lo que limita el string a 4Gb de tamaño.
- Los siguientes 4 bytes son un fragmento del string completo que se deja guardado en línea con el string. Esto optimiza búsquedas y ordenamiento porque usás el prefijo primero y sino lo buscás al heap

---
## Links:
* [Article about german strings in rust](https://tunglevo.com/note/an-optimization-thats-impossible-in-rust/#german-strings)
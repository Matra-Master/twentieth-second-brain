
## Crate

Una caja(*crate*) en rust es una unidad funcional de un programa. No es exactamente así pero es una abstracción suficiente para entenderlo si no entendés nada al principio.
Un proyecto recién iniciado con `cargo new` es considerado como un *package* que tiene adentro un único *crate* para Rust.

Hay 2 tipos de *crate*:
- **Binary crate.** tiene una función main que corre cuando se llama al crate. El programa hecho con cargo new cuenta como tal. Se compila a un binario y se pasa como si fuera un programa cualquiera.
- **Library crate.** no tiene main y es más bien un conjunto de propiedades, estructuras, funciones y demás. Lo dice el nombre, es una librería. Normalmente cuando un paquete termina en `-crate` es una librería de estas, es una convención.

Un paquete(*package*) es un conjunto de *crates* listado y agrupado por un archivo `Cargo.toml`

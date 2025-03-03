---
tags:
  - Resources/learning
  - Resources/programming
---


How can a person think of code in terms of performance without getting too hardcore into performance stuff?

Yo estoy desarmando un request en varios mini requests y endpoints para optimizarlo para el front.
Pero para el back, y en términos de eficiencia del uso del disco en el server, técnicamente es más eficiente usar un request que pase a varias funciones los objetos que necesiten, porque se hace un pedido a la DB y se reparte data entre estructuras de PHP en la ram. 
Hacer varios requests es hacer varios pedidos redundantes a la db. Cuál elijo optimizar en el API: la RAM, el disco, la red? Quién más piensa en eso realmente?
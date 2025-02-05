---
created: 20231220-1038
tags:
  - Resources/devops
  - Resources/git
---

What will you discover today?
https://github.com/nektos/act

Act can run Github workflows locally through docker 👀

---
# Update:

Luego de usarlo un rato es una boludez, es exceleente!

Se usa como un test suite: escribís tu archivo de github workflow y corrés `act` para probarlo.

No es totalmente compatible con GA, sus artefactos son medio raros y aparentemente el docker runner también pero me sirve.

Datazo: para usar build artifacts hay que agregar el parámetro `--artifact-server-path` indicando una carpeta donde guardar los artefactos luego de buildear cosas. Útil para probar ciertos pipes. [Link del issue en Github](https://github.com/nektos/act/issues/329)



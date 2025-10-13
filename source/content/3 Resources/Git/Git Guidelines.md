---
tags:
  - git
  - guide
---

### Description
Acá voy a recopilar cosas consideradas como **buenas prácticas** para que todxs puedan acceder y referenciar cuando tengan dudas de cómo proceder con git.

### Basic concepts
- [Todo en local](#everything-local)
- [Área de staging](#staging-area)

### Todo en Local
Git plantea un flujo de trabajo en el cual un desarrollador trabaja sobre una copia del historial completo del código. Lo primero que se espera de uno es que *clone* el repositorio para empezar a trabajar; y automáticamente ese repositorio es considerado como *origin remote* o *upstream*. 
Si bien el uso de Git GUIs(gitkraken, vscode git, Git Extensions) facilita mucho el aprendizaje de los comandos y poderes que uno tiene a su disposición, tienen la desventaja de borrar la línea entre local y remoto al facilitar funciones automáticas como 'commit & push'.

Esto es un problema menor que se vuelve notorio cuando uno necesita reescribir el historial de cambios recientes, porque cualquier cambio que tengas que reescribir de remoto va a afectar a los demás desarrolladores.
Una cosa muy común es querer hacer un `git commit --amend` para corregir el último commit que hicimos, ya sea porque uno escribió mal el comentario del commit o porque hay un cambio que no corresponde. Y si tuvieramos ese commit en local sin pushear tal cosa sería trivial.
Una **peligrosa** es querer corregir algo haciendo un force push y sin saberlo eliminar los commits que otro puso en el branch remoto 😰

La regla de oro es: *No pushees tu código hasta que no estés conforme con él.*


### Área de staging
El concepto de *stage area* diferencia a git de otros CRMs de su momento, y permite que el proceso de cambiar software se adapte al estilo de cada developer.
La idea es que por defecto a Git no le incumbe el código que uno cambia, así que para registrar un cambio a cualquier archivo al alcance de Git uno debe "subirlo al escenario", o sea agregarlo al área de staging.
En el área de staging nada es seguro aún; uno puede arrepentirse y sacar cosas, o elegir qué cambios van al siguiente commit y cuáles no. Es posible hacer 100 cambios de una feature nueva e ir commiteando de a 1, o commitear todos a la vez (NO recomendable by Fran).

---
## General good practices
- [Separar cambios](#separar-cambios)
- [Preferir merges](#preferir-merges)
- [Mergear hacia arriba](#mergear-hacia-arriba)
- [Fixes a prod](#fixes-a-prod)
- [Emplear branches de descarte](#branches-de-descarte)

### Separar cambios
Como regla general, uno debería tratar de separar sus cambios en **pasos lógicos pequeños** (tanto como se pueda) y commitear cada uno. Cada commit debería funcionar independientemente de los nuevos commits, y en lo posible pasar algún test (a futuro).
Git fue hecho pensando en que es más **fácil hacer un *squash*** de commits chicos que separar un commit grande. Uno no debería tener miedo de hacer pasos muuy chicos o imperfectos, mientras se hagan [pocos push al día](#pocos-push-al-dia) los cambios locales pueden ser reescritos con facilidad usando `git rebase --interactive` o [comandos similares][git-rebase]. 

### Preferir merges
Hay dos métodos que se pueden usar para incluir cambios de un branch en otro: [Merge][git-merge] o [Cherry-pick][git-cherry-pick]. La gran diferencia entre uno y otro es que los Merges operan al nivel de branches completos, y el cherry-pick es para commits individuales. 
En general, el **cherry-pick** sólo es perferible cuando el objetivo es pasar un **cambio pequeño y rápido** entre branches; el mejor ejemplo de eso es un fix o parche que se usó en production (*upstream* o corriente arriba) y que luego se lleva a development(*downstream* o corriente abajo)

### Mergear hacia arriba
El flujo esperable de desarrollo lleva una *feature* de los branches más bajos y volátiles a los más altos y estables usando **merges** (o *rebases* si sabés lo que estás haciendo con tu historial). 
Cuando una funcionalidad va siendo testeada y aprobada se dice que se "gradúa" y asciende a los branch superiores. 

### Fixes a prod
Si bien la **disponibilidad** de los branches que van de cara a clientes y testers **debe ser máxima**, es entendible que llegue algún **error a producción** o staging. En estos casos, el **cambio que se revisa rápidamente** y que soluciona el problema en el menor tiempo posible se prioriza y **se commitea diréctamente en prod**.
Luego se espera que ese cambio sea llevado corriente abajo con cherry-picks para ser asimilado por el resto del código.

### Branches de descarte
Ante la duda de que una combinación de features vaya a funcionar o no, siempre crear un branch de descarte.
Un branch de descarte **no es para ser pusheado a remoto**, sino **para probar cosas**, así que su nombre y los mensajes de commits son indiferentes. 
En los entornos de Github o Gitlab de proyectos grandes es bastante común que los testeos automatizados de pull requests o merge request los haga un bot sobre un branch de descarte.


---
# References

[git-everyday]: https://git-scm.com/docs/giteveryday "Git EveryDay"
[git-rebase]: https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History "Git tools - Rewriting history"
[git-merge]: https://git-scm.com/docs/git-merge "Git merges Documentation"
[git-cherry-pick]: https://git-scm.com/docs/git-cherry-pick "Git Cherry-pick Documentation"
[staging-area]: https://git-scm.com/about/staging-area "Git about staing area"
[workflows]: https://git-scm.com/docs/gitworkflows "Git workflows"


# Ejercicio 1

* ¿Qué comando utilizaste en el paso 11? ¿Por qué?

```bash
git reset --hard HEAD~1
```
He usado este comando por que con "~" le decimos al puntero `HEAD` que se mueva al paso anterior y es la forma más fácil de deshacer el último cambio.
`--hard` para perder los cambios y tener el working copy tal y como estaba en el paso anterior.

* ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?

Tenemos dos opciones para solventar este paso. En ambos casos primero hariamos un `git reflog` (aquí es un ejercicio y está claro que solo tenemos que rehacer un paso pero puede ser que estemos en un repositorio en el que trabajan muchas personas y lo que queremos hacer es solventar una “cagada” de alguien que deshizo lo que no debía, por ejemplo).

Con el `git reflog` buscamos hasta donde queremos rehacer (en realidad es deshacer lo deshecho), en este caso sería 1 único paso el que queremos rehacer y podemos hacerlo con el id del commit con en este caso el id *5df399d*:

```bash
git reset —hard 5df399d
```
O también moviendo el puntero `HEAD` con: ```
git reset —hard HEAD@{1}
```

* El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?

No porque no hubo ningún commit que entrara en conflicto de master, el puntero de la rama master estaba en el commit desde el que salió la rama *htmlify* y por tanto no había ningún commit después en master que modificara las mismas líneas (si hubiese otro commit pero modificase otras líneas tampoco habría conflicto).

* El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?
Si, porque había un commit en la rama *matrix* con cambios en las mismas líneas que *htmlify* que era un nuevo commit y no un commit anterior de *htmlify*.

* El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?
No, porque las ediciones de esas líneas se hicieron en un commit que partía de esa rama y al mezclarlo el commit coge los cambios del último commit de *htmlify*.

* ¿Qué comando o comandos utilizaste en el paso 25?
  `git log --graph`
  
  Aunque si tuviese muchos commits habría usado `git log --graph --pretty=oneline`
  
  `git log —graph` nos muestra los commits con el diagrama.

* El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?
  
  Sí que podría porque lo único que hacemos al hacer el merge en realidad es mover el puntero de *master* porque esa rama podría estar en master perfectamente debido a que no ha habido nuevos commits en *master*.

* ¿Qué comando o comandos utilizaste en el paso 27? 
```bash
git reset HEAD~1
```

* ¿Qué comando o comandos utilizaste en el paso 28?
```bash
git checkout -- poem.md
```

* ¿Qué comando o comandos utilizaste en el paso 29?
  
  Primero me equivoque porque no me acordaba que había deshecho el merge y había cambios que *“mezclar / añadir”* antes de borrar la rama y use `git branch -d title` como falló, me di cuenta de por qué (git es un chivato…) y usé `git branch -D title` haciendo que se quedara sin *"mezclar / añadir"* los cambios

* ¿Qué comando o comandos utilizaste en el paso 30?
```bash
git reflog
```
Busqué el commit que decía *“Merge branch 'title' --no-ff (paso 26)”* y tenía el id *bdd74fa* así que hice:
```
git reset —hard bdd74fa
```

* ¿Qué comando o comandos usaste en el paso 32?
```bash
git reflog
git reset —hard 7105089 
```
  Tambien podríamos haber usado:
```bash
git reset —hard HEAD@{20}
```
(En mi caso 20 porque tuve que hacer un par de movimientos ya que me perdí entre los pasos por dejar el ejercicio a medias y tener que seguir más tarde; work things)

* ¿Qué comando o comandos usaste en el punto 33? 
```bash
git reset —hard HEAD@{1}
```
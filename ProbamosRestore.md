Hola
Como 

Este archivo será para probar algo. 
If git restore --staged solo elimina el archivo de la staging area o además eleimina los cambios hechos en el y restaura al archivo tal cual estaba en el último commit.
Entonces lo creamos. Escribimos "Hola" lo añadimos a staging area y lo commiteamos.
Luego del commit lo modificamos, lo añadiremos y realizaremos el git restore --staged. Veremos si se elimina todo y queda únicamente "Hola". Copiare esto por precaución.

Añadí el archivo a la staging area, ejecute el restore para sacarlo de allí y no se borró la modificación del archivo, simplemente se eyectó de la staging area.
Comandos usados:
<!--  
    git add ProbamosRestore.md 
    git restore --staged ProbamosRestore.md
-->

<!-- Ya que estamos, comprobaremos que funcione la restauración normal. En este caso, copiaré el código con más convicción que antes ya que se borrará. -->

git restore ProbamosRestore.md

<!-- Efectivamente. Se restauro el último commit. Excepto la linea 1 se borraron el resto. -->

<!-- Commitearemos este archivo para sobreescribir su guardado. Luego intentaré deshacerlo y recuperar el commit anterior donde solo "Hola" era la versión guardada. -->


<!-- Ya realizamos el commit
Ahora, como lo deshacemos? O mejor dicho, como volvemos al anterior que será lo que haremos..
Primero, identificamos el commit que deseamos usar, usamos git log para ver los commits y encontramos su hash (id), lo copiamos para usarlo en el siguiente commando: -->
<!-- Este es el commit que restauraremos, encontrado con git log -->
<!-- commit d7dc7e00d230a48947d19a43c1e2b1b09aab6ca4
Author: Agustin Dahbar <agustindahbarpp@hotmail.com>
Date:   Fri Feb 23 10:39:27 2024 -0300

    Add ProbamosRestore 
-->

git reset --hard d7dc7e00d230a48947d19a43c1e2b1b09aab6ca4

<!-- 
Efectivamente se borró el commit anterior al cargado, al hacer git log aparecerá como último commit el que cargamos, los posteriores han sido borrados (uno solo en este caso). 
De todas formas con CNTRL + Z, he recuperado el código borrado, esto no significa que hayamos recuperado el commit, sigue borrado, no se deshizo el comando git que ejecutamos (28), solo se recuperó el codigo borrado por la funcionalidad de VSCODE. El archivo quedo en "Modified" se editó nuevamente al archivo, podremos volver a crear el commit recien borrado, pero intentaremos recuperarlo de otra forma.
 -->

<!-- Tenemos que obtener su hash (ID) mediante -->
 git reflog 
<!-- Se nos muestran operaciones, entre ellas todos los commits. Encontramos el que necesitamos que es: -->
<!-- e211cdb HEAD@{1}: commit: ProbamosRestore commit  -->

<!-- Una vez tengamos el hash (id) tenemos dos opciones, crear una rama o una etiqueta. Crearemos una etiqueta ya que aún no lo hemos probado -->
<!-- Etiqueta: --> git tag "Etiqueta de recuperacion" e211cdb
<!-- Branch: -->   git branch "Rama de recuperacion" e211cdb

<!-- Al crear la etiqueta debemos pararnos sobre ella -->
git checkout Rama de recuperacion

<!-- Efectivamente, nos paramos sobre ella y nos spawnea el archivo con la versión correspondiente al commit recuperado -->

<!-- Ahora al ejecutar el comando -->
git log
<!-- Volvemos a ver el commit en la lista con su nombre "ProbamosRestore commit" con la diferencia de que al lado de (HEAD) separado por una coma se encuentra el "tag: TagRecuperacion" con el que lo hemos recuperado. -->

<!-- Ahora haremos un nuevo commit, que será la primer versión de este archivo en la etiqueta "TagRecuperacion"  -->

git add ProbamosRestore.md
git commit -m "Update ProbamosRestore en TagRecuperacion"

<!-- Hemos tenido problemas con la Etiqueta por lo tanto guardaremos este archivo en la Rama Tres haciendo el mismo commit pero aquí ahora. El problema es que los archivos de TagDeRecuperación se iban a una etiqueta rara y generica a la que luego no sabía acceder, es decir, perdía todo. Cada vez que cerraba VSCODE y lo abría me aparecía ese TAG extraño. Le saque screenshot. -->

git add ProbamosRestore.md
git commit -m "Update ProbamosRestore en RamaTres"

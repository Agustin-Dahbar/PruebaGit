<!-- CARGAR COMMITS CON GIT RESET --soft -->
git reset --soft 93cb3a
<!-- Este comando mueve el puntero HEAD al commit especificado, pero deja los cambios en el directorio de trabajo y el índice de ensamblaje (staging index) tal como estaban. Es decir, no afecta los archivos en el directorio de trabajo ni los cambios que hayas preparado en el índice de ensamblaje (staging area). Se utiliza principalmente cuando deseas deshacer el último commit, pero mantener los cambios realizados para poder editarlos y volver a confirmarlos mediante el commit.
En resumen, deshace el commit pero mantiene su contenido, estará en el staging area y se podrá volver a commitear o eliminar de allí para hacer un restore al commit anterior al borrado. -->
git restore --staged hola.md <!-- Sacamos los cambios de la staging area, para poder restaurar el  commit seleccionado. --> 
git restore hola.md <!--Restauramos el archivo a la versión del commit indicado en git reset --soft -->

<!-- CARGAR COMMITS CON GIT RESET --HARD -->
git reset --hard 93cb3a 
<!-- Este comando mueve el puntearo HEAD al commit especificado, pero a diferencia de --soft no conserva los cambios realizados posteriormente al commit invocado. Son eliminados del directorio de trabajo (archivos) y del índice de ensamblaje (staging area) -->

Entonces cuando tengamos muchos archivos en el repositorio es mejor usar --soft asi no perdemos contenido del total de ellos. Analizamos en el staging area cuáles archivos querremos mantener y cuáles restaurar. Para mantenerlos les haremos un git commit y para restaurar un git restore.

Pero si tenemos un solo archivo o algunos pocos y sabemos con exactitud que queremos restaurarlos a todos y nunca necesitaremos nuevamente el contenido de los commits posteriores al que volveremos, deberiamos usar un --hard para ahorrarnos los pasos hacia la restauración que requiere --soft.



<!-- VER COMMITS GIT CHECKOUT -->
git checkout 93cb3a
<!-- Tendremos una vista previa de la versión del archivo en ese commit, fines de lectura. -->




<!-- Podemos reemplazar el hash por un esta sintaxis. El número indica cuantos commits se retrocederá. De todas formas no puedo usarla por no tener en el teclado eso y no poder pegar en el bash. -->
git reset --soft HEAD~1

hola.md es el archivo donde realicé 3 commits para comprobar esto.
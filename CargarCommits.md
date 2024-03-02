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




<!-- Podemos reemplazar el hash por un esta sintaxis. El número indica cuantos commits se retrocederá. De todas formas no puedo usarla por no tener en el teclado eso y no poder pegar en el bash. --> PREGUNTAR A GUILLE COMO HACERLO. ME AHORRARÍA MUCHO TIEMPO.
git reset --soft HEAD~1

hola.md es el archivo donde realicé 3 commits para comprobar esto.



<!-- INTENTO DE PULL REQUEST, FALLIDO. SOLUCIÓN TEMPORAL Y PERMITIDA EN ESTA SITUACIÓN. -->

<!-- Intente hacer el pull request pero fallé, luego lo reintentaré. Entonces mi solución fue hacer -->
git checkout RamaPullRequest - CargarCommits.md
<!-- Exitosamente se pegó el archivo de esa rama. El problema con esto, es que PEGA TODO EL ARCHIVO (no únicamente nuestra modificación (commit)), en este caso lo pude utilizar, porque el código era idéntico, pero si es diferente se reemplazará todo, y nosotros solo queremos la edición hecha en el commit, por lo tanto, solución en este contexto, aprender a hacer correctamente la pull request. De todas formas podemos restaurar fácilmente el código en caso de usar un git checkout y arruinar el código, con:  -->
git restore CargarCommits.md
<!-- Asi cargaremos la versión anterior de la rama, la final, claro mientras no hayas commiteado el archivo luego del git checkout. Pero de todas formas, si hubieramos cometido ese error también tendría solución, sería tan fácil como usar un  -->
git reset --hard hashDelCommit
<!-- Con hard eliminaremos el código actual modificado y la versión deseada se cargará automaticamente. Con soft mantendríamos el código y el archivo estaría en un estado de modified dentro de la staging area, esperando de hacerse un commit para sobreescribir el archivo, o un restore del mismo archivo, que requerería que el archivo salga de la staging area para poder ejecutarse, el orden sería: -->
git restore --staged fileName --> git restore fileName.


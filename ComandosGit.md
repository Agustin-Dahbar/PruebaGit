Al realizarse modificaciones en los archivos estos deben agregarse a un area llamada "Staging area", acá se pueden realizar commits de las modificaciones añadidas, esto es una confirmación del cambio. 
Al confirmarlo ya está listo para ser enviado al repositorio web en el host usado y asi actualizarse la página con los cambios realizados.

<!-- ÍNDICE DE COMANDOS -->
Ubicación de directorio (16-27)
Creación e inicialización de repositorio git en el directorio. (36-40)
Comandos relacionados con la Staging Area (49-75)
Insertar los archivos del repositorio local en el repositorio de github (83-93)
Branchs/Ramas (102-123)
Borrar archivos de los repositorios (local y git) (130-155)
Extras (164)




<!-- COMANDOS UBICACIÓN DE DIRECTORIO -->
cd /c/Users/Agustin
<!-- cambiamos el directorio. No es necesario poner la ruta completa, podemos solo usar el comando con una sola carpeta y de ahí acceder de una en una. -->

cd Users
<!-- No es necesario hacer el CD con la ruta completa, podemos ir accediendo de archivo a archivo, siempre y cuando el archivo indicado este dentro del repositorio en el que estemos parado. -->

cd Agustin
<!-- Completariamos el acceso. -->

cd ..
<!-- Retrocedemos un archivo en el directorio -->



<!-- 
-->



<!-- CREACIÓN REPOSITORIO (CARPETA) y lo inicializamos con GIT -->
mkdir miweb

git init
<!-- Inicializamos el repositorio y se crea la carpeta oculta .git. Esto provoca que la carpeta en la que se realize tenga todas las capacidades que necesitamos. En la línea de código 72 profundizaremos-->



<!-- 
-->



<!-- COMANDOS PARA MODIFICACIONES DE ARCHIVOS EN ETAPA STAGED -->
git status || git status -s
<!-- Muestra estado actual de nuestro repositorio. Si hay archivos en etapa Stage para commitear, si no los hay. Si están modificados y se necesita un git add o un git restore (línea 39).. -s resume la información-->

git add <file> 
<!-- Al ejecutar este comando por primera vez el archivo se enviará a la etapa STAGED. Esta etapa permite que se puedan commitear los archivos. Si este archivo ya esta en la etapa Staged, el uso del comando sobreescribirá a la versión del archivo que este en staged por la nueva. -->

git add .
<!-- Agreamos todos los archivos del repositorio en la staging area. -->

git add .md
<!-- Esto agregará los archivos que tengar terminación 'md'. Es decir que podemos subir todos los archivos de un tipo de lenguaje específico. -->


git restore <file> 
<!-- Este comando elimina los cambios realizados y deja al archivo como su última versión commiteada. Se lo conoce como BACKROLL.-->

git restore --staged <file>
<!-- Este comando saca un archivo del área de preparación (staging area) sin modificar el estado del archivo en el directorio de trabajo. Es útil cuando has agregado un archivo al área de preparación pero decides que no quieres incluirlo en el próximo commit. -->

git rm --cached <file>
<!-- Este comando elimina el archivo del área de preparación (staging area) y también lo mantiene en el directorio de trabajo. La diferencia con git restore --staged <file> es que git rm --cached <file> también actualiza el estado del archivo en el directorio de trabajo para que ya no esté marcado como "modificado".
Es útil cuando deseas dejar de rastrear un archivo en Git (por ejemplo, cuando deseas ignorar un archivo que accidentalmente ha sido rastreado), pero no quieres eliminar el archivo del sistema de archivos.
Sin embargo, git rm --cached <file> no elimina el archivo del sistema de archivos. Si deseas eliminar el archivo tanto del área de preparación como del sistema de archivos, deberás seguir git rm --cached <file> con git commit para confirmar la eliminación en el repositorio. -->

git commit -m "nombre desc del commit"
<!-- Este comando realiza un commit de las modificaciones realizadas en la etapa staged. No se puede hacer si no hay nada en esta etapa. Significa que se sobreescribirán los datos del archivo real con lo que estaba añadido en la etapa "Stage". -->



<!-- 
-->


<!-- COMANDOS PARA VINCULAR EL REPOSITORIO LOCAL AL REPOSITORIO DE GITHUB, PARA ASI ENVIARLE LOS ARCHIVOS SELECCIONADOS -->
git remote add origin https://giturl
<!-- Realizamos la vinculación -->

git remote -v
<!-- Para verificar la correcta vinculación. Se nos mostrará la URL del repositorio de GitHub vinculado. -->

git push -u origin nombredelbranch
 <!--Enviaremos  los commits realizados en la rama. Es decir actualizaremos el repositorio remoto de github con los cambios realizados localmente en el repositorio de git. En caso de que sea la primera vez que lo ejecutamos, enviaremos archivos al repositorio de github. Podemos no hacer un git add, pero se subirán todos los archivos del repositorio. Hacerlo para seleccionar cuáles subir y cuáles no. Profunda explicación de la sintaxis en 206 -->

 

<!-- 
 -->



<!-- COMANDOS PARA TRABAJAR CON BRANCH´S -->
git branch
<!-- Veremos todas las ramas del repositorio, se nos específicara cual es en la que estamos parados. -->

git checkout -b SegundaRama
<!-- Creamos una rama. Nos paramos sobre ella. -->

git checkout master
<!-- Comando para cambiar la rama donde estamos parados-->

git checkout RamaTres -- ArchivosVistos.md
<!-- Se utiliza para que en la rama en la que nos encontremos peguemos un archivo de otra rama. El archivo se mantendrá en su rama de origen y ahora estará en ambas, por eso el termino "pegar" y no "transferir". 
En este caso trae a "ArchivosVistos.md" de la RamaTres a la rama que ejecutó el comando.-->

git merge SegundaRama
<!-- En la rama en la que ejecutamos el comando se pegarán todos los archivos de la rama "SegundaRama". Mismo comando que el anterior pero totalitario, con el otro podemos específicar que archivos enviar. -->

git push -u origin SegundaRama
<!-- Enviar ramas al repositorio de github en caso de no estar aún y necesitarlas. -->

cat messi.txt
<!-- Podremos ver el contenido de los archivos, en cada rama tendrá un resultado != ya que son != versiones del mismo código -->



<!-- 
-->



<!-- COMANDOS PARA BORRAR ARCHIVOS DEL REPOSITORIO -->
ls
<!-- Veremos los archivos: archivo2.txt hola.txt -->

rm archivo2.txt
<!-- lo borramos del sistema de archivos locales, con git status comprobamos esto. Sin embargo seguirá en la etapa de "Stage", debemos añadir este cambio para que desaparezca. Lo haremos en el siguiente comando. -->

git add archivo2.txt
<!-- Añadimos los cambios de archivo 2, es decir su eliminación. Para capitalizarla en un commit. -->

<!-- Ahora realizaremos el commit de las modificaciones recien realizadas (la eliminación del archivo) -->
git commit -m "Eliminacion de archivo2.txt"
<!-- [master 0a1ab39] Eliminacion de archivo2.txt
 1 file changed, 2 deletions(-)
 delete mode 100644 archivo2.txt -->

ls
<!-- Para ver los archivos dentro del repositorio y comprobamos que la eliminación fue correcta al solo aparecer "hola.txt" -->

git restore archivo2.txt
<!-- Recuperamos el archivo borrado -->



<!-- PODEMOS AHORRARNOS ESTOS PASOS CON EL SIGUIENTE COMANDO: -->
git rm archivo2.txt
<!-- Además de borrarlo de los archivos locales como el comando anterior, lo eliminamos del repositorio de git y nos ahorramos los dos pasos (add && commit).-->



<!--
-->



<!-- EXTRAS -->
ls || ls -a || ls -s
<!-- Muestra los archivos del repositorio. || Con el -a, se incluyen los ocultos, como el .git. -->

git -h
<!-- Help. Te da opciones. -->

pwd     
<!--Mostrará el repositorio donde estamos ubicados. -->

code .
<!-- Abrimos en VSCODE el repositorio en el que estamos parados. -->

clear
<!-- Limpiamos git bash -->

 
<!-- Cambiar nombres de archivos:  -->
git mv new.txt neww.txt
<!-- Cambio de nombre nuevamente -->

git status
<!-- Comprobamos el cambio. Deberá decir "Renamed" -->

git commit -m "CambioDeNombre"
<!-- Realizamos el commit para confirmar los cambios. -->

       

<!-- COMO VER LOS CAMBIOS REALIZADOS -->
git diff es un comando útil para ver en el bash los cambios que realizamos recientemente en los archivos. 
git diff --staged mostrará los cambios que queremos commitear. 

<!-- VER EL HISTORIAL DE CAMBIOS DE GIT -->
git log 
<!-- comando que se mostrará el historial de movimientos en el git  -->
git log --oneline 
<!-- para que se vea reducido -->



<!-- Explicacion detallada de la sintaxis del comando -->
git push -u origin RamaDos

<!-- git push: Envía los cambios confirmados localmente al repositorio remoto.

-u: Esto configura la rama local para rastrear la rama remota. Esto significa que en futuros git push o git pull, 
    no necesitarás especificar la rama y la dirección remota, Git ya sabrá a dónde enviar o desde dónde obtener los cambios. Esto es útil si planeas trabajar con esta rama de forma regular.
    En el repo en github podremos ir a la sección "Commits" para analizarlos, clickearemos en sus nombres para ver visualmente los cambios mediante los colores rojo y verde. 

origin (repositorio remoto de github): 
        Es el nombre asignado al repositorio remoto. Generalmente, cuando clonas un repositorio desde GitHub, el repositorio remoto s llama origin de forma predeterminada.

master (branch pusheado al repositorio de github): 
        Es la rama local que estás empujando al repositorio remoto. -->

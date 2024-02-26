<!-- Ubicación de directorio y creación del repositorio al que le iniciaremos GIT-->
cd Users <!--Cambio de directorio (carpeta) (cd = change directory). -->
cd .. <!--Retrocedemos al directorio anterior al que nos encontramos.-->
mkdir nombreDelRepositorio <!--Creamos un nuevo directorio (carpeta). -->

<!-- Comandos de git relacionados con la staging area -->
git init <!--Inicializamos el repositorio de git en el directorio en el que nos encontremos-->
git status (-s) <!--Muestra el estado de los archivos de la staging area (Added, Modified, Deleted, etc)-->
git add nombreDelArchivo.suTerminacion <!--Seleccionaremos que archivos o modificaciones añadir a staging area-->
git add .terminacionDeArchivos <!--Subirá o modificará todos los archivos con esa terminación a la staging area-->
git commit -m "nombre commit"<!--Confirma los cambios que esten en el staging area y sobreescribe al archivo-->
git restore <!--Recuperamos la versión del código del último commit guardado. Cargamos el último guardado.-->
git restore --staged <!--Sacaremos al archivo de la staging area-->
git rm --cached <!--Eliminamos un archivo de GIT de la staging area. Pero no se borrá de los archivos.-->


<!-- RAMAS -->
git branch <!--Se nos mostrarán todas las ramas del repositorio local de git-->
git checkout -b nombreRama <!-- Creamos una rama y nos paramos sobre ella. -->
git checkout nombreRama <!-- Seleccionamos otra rama para usar-->
git checkout RamaTres -- ArchivosVistos.md <!--En la rama que ejecutó el código pegamos un archivo de la rama indicada-->
git reset --hard hashDelCommit <!--Restauraremos un archivo con un commit anterior, eliminaremos el contenido de los siguientes commits aunque seguirán existiendo-->
git reset --soft hashDelCommit <!--A diferencia del anterior, no se perderán los datos de los siguientes commits-->
git merge SegundaRama <!--En la rama que ejecutó el código se pegarán todos los archivos de la rama indicada.-->
git push -u origin SegundaRama<!-- Pusheamos ramas al repositorio web de github.-->

<!-- GITHUB -->
git remote add origin https://giturl <!--Vinculamos nuestro repositorio local git al repositorio web de github-->
git remote -v <!--Se nos mostrará la URL del repositorio web al que vinculamos nuestro repositorio local -->
git push -u origin nombredelbranch <!--Pusheamos una rama al repositorio web de github-->


<!-- EXTRAS -->
cat messi.txt <!--Se muestra el contenido del archivo indicado.-->
ls (-a) (-s) <!--Se nos mostrarán los archivos del repositorio local git.--> 
<!-- -a agrega las carpetas ocultas (el repositorio .git) -s nos muestra el tamaño de cada directorio (carpeta) en bloques de discos -->
git -h <!-- Help. Te da opciones. -->
pwd <!--Mostrará el repositorio donde estamos ubicados. -->
code . <!-- Abrimos en VSCODE el repositorio en el que estamos parados. -->
clear <!-- Limpiamos git bash -->

<!-- CAMBIAR NOMBRES DE ARCHIVOS Y SU PROCESO PARA ACTUALIZARLOS EN LA PÁGINA WEB -->
git mv nombre.txt newNombre.txt <!-- Cambio de nombre. Ahora se debe agregar este cambio a staging area y commitearlo para pushearlo.-->
git status <!-- Comprobamos el cambio de nombre. Deberá decir "Renamed" -->
git add newNombre.txt <!-- Añadimos el cambio de nombre a la staging area. -->
git commit -m "CambioDeNombre" <!-- Realizamos el commit para confirmar los cambios. -->
git push -u origin <!-- Pusheamos al repositorio web todos los cambios commiteados. En este caso el "git mv" que fue commiteado. -->

<!-- VER CAMBIOS REALIZADOS -->
git diff <!-- Mostrará los cambios realizados recientemente--> 
git diff --staged <!--Mostrará los cambios de la staging area listos para commitearse. -->

<!-- VER EL HISTORIAL DE CAMBIOS DE GIT -->
git reflog <!--Comando que mostrara EL HISTORIAL COMPLETO-->
git log <!-- Comando que se mostrará el historial reciente de movimientos en el git ( mostrará todos los commits con su nombre, autor y fecha) -->
git log --oneline <!-- Para que se vea reducido en una línea. Solo se mostrará el nombre del commit y su hash (ID) -->

<!-- BORRAR ARCHIVOS CON COMANDO GIT -->
git rm archivo2.txt <!-- Además de borrarlo de los archivos locales (working directory) lo eliminamos del repositorio de git. -->
git add archivo2.txt <!--Añadimos el delete a la staging area-->
git commit -m "Eliminacion de archivo2.txt" <!--Commiteamos la eliminación para sobreescribirla.>

<!-- BORRAR ARCHIVOS CON COMANDO DE SISTEMA OPERATIVO -->
rm archivo2.txt <!--Borramos el archivo del working directory (archivos locales) -->
git add archivo2.txt<!--Añadimos la eliminación a la staging area para commitearla y capitalizarla.-->
git commit -m "Eliminacion de archivo2.txt" <!-- Ahora realizaremos el commit de la eliminación. -->
git restore archivo2.txt <!-- Recuperamos el archivo borrado -->



<!-- Problema al intentar borrar y su posterior solución -->
$ git rm ComandosGit.md
% error: the following file has changes staged in the index:
%     ComandosGit.md
% (use --cached to keep the file, or -f to force removal)

$ git rm -f ComandosGit.md
<!-- rm 'ComandosGit.md' -->


<!-- Preguntarle a Guille como resolver el no poder ejecutar comandos al usar git log || git reflog -->
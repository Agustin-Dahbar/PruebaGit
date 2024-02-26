<!-- PASO A PASO PARA REALIZAR TAREAS DE CÓDIGO -->

<!-- Crear una rama en donde hacer el trabajo propio. -->
git checkout -b "RamaDeDesarrollo"

<!-- Parados en ella, desarrollamos los archivos que se nos pidan. Al finalizar: -->
git add fileName.cs

<!-- Ya en el staging area podremos commitear los cambios. -->
git commit -m "tarea 35 fileName.cs"

<!-- Al ya confirmar los cambios en el repositorio local, deberemos hacerlo en el web--remoto (github)-->
git push -u origin RamaDeDesarrollo

<!-- Ya tenemos la rama con nuestros cambios en el repo web de github. Ahora toca la pull request-->

<!-- PULL REQUEST DE NUESTRA RAMA DE TRABAJO HACIA LA RAMA PRINCIPAL -->
Pull request o solicitud de extracción es una solicitud de revisión que enviamos a los revisores para que confirme nuestro código y lo incluyan en la rama que les indicamos, usualmente a la principal que suele llamarse 'main' || 'master'. Esto lo haremos en github.   

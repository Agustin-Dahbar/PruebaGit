<!-- COMANDOS PARA MODIFICACIONES Y ETAPA STAGED -->
git add <file>
<!-- Al ejecutar este comando por primera vez el archivo se enviará a la etapa STAGED. Esta etapa permite que se puedan commitear los archivos. Si este archivo ya esta en la etapa Staged, el uso del comando sobreescribirá a la versión del archivo que este en staged por la nueva. -->

git restore --staged <file>
<!-- Este comando saca un archivo de la etapa Staged, no podrá ser commiteado hasta no volver a la misma -->

git restore <file>
<!-- Este comando to discard changes in working directory -->




<!-- COMANDOS CON RELACIÓN A GITHUB -->
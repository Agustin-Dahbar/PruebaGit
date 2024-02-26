<!--Cree un archivo con 3 commits. Volví al primero mediante : -->
Este lo logramos mediante 3 comandos de git:-->
git reset --soft idDelCommit
<!--Usamos soft ya que este commit es compartido entre ComandosResumen y extra y solo queremos cambiar uno (extra), asi que el otro archivo debe conservarse. Y eso es lo que provoca --soft, nos paramos en un commit anterior pero el código se mantiene siendo el más reciente, esto provoca que al estar en un antiguo commit, se entienda como un código modificado y este en la "staging area". En cambio si usamos --hard no estaría el archivo en la staging area ya que se sobreescribiria el contenido del mismo por el del commit restaurado. Ya que usamos soft y el código esta en la staging area, no podremos reestablecerlo directamente, debemos sacarlo de allí.-->
git restore --staged extra.md <!--Lo sacamos de staging area-->
git restore extra.md <!-- Restauramos el archivo  -->

<!-- El hash (ID) del commit se puede obtener en Git Graph o con el comando Git Reflog.  -->
La solución se divide en diferente secciones (serán carpetas), las más importantes son:

1. Entidades
2. Interfaces
3. Procesos
4. Servicios
5. WebSites


<!-- En este archivo desarrollaremos las características de cada sección. En la solución están los comentarios explicativos de la sintaxis del código.-->

1. Entidades (5 proyectos)
<!-- Esta sección es la capa de las entidades de se encontrarán los objetos que serán mapeados al proyecto desde la base de datos, específicamente desde las tablas, sus filas serán las entidades mapeadas como objetos. 
Cada sección tiene diferentes proyectos (bibliotecas de clases que se encargarán de diferentes tareas con relación a estos objetos). --> 




PROYECTOS:
<!--En el primer nivel de jerarquía de varios proyectos habrá carpetas, estas representaran el esquema de la base de datos donde esta ubicada la tabla (clase en el caso del IDE visual studio) -->
                                                
                                                --SondalIConstruye.Framework.Entidad.DTO
<!-- 
En este proyecto se encontrará el objeto visual. Es el objeto que será devuelto en el Frontend. 
(DTO == Data Transfer Object; Objeto de transferencia de datos) 
Las entidades DTO son el puente entre la sección de datos (Entidades.NH) y el resto de secciones de la solución.
La sección de datos (Entidades.NH) solo ve los objetos de bases de datos pero cuando lo tiene que compartir a la presentación o a la interfaz lo que se comparte es el DTO, NO EL NH.
-->


                                                --SondaIConstruye.Framework.Entidad.NH
<!--
En este proyecto se encontrarán los objetos de la base de datos, es decir es la creación más completa y auténtica posible del objeto. Es el objeto Backend, no se mostrará en el frontend. Es una capa de datos. 
Estos objetos se crearán a partir de clases que determinarán sus propiedades y metodos, estarán en la carpeta "NH" en el esquema correspondiente (carpeta) dentro del proyecto.
LAS CLASES DE ESTE PROYECTO HEREDERÁN DE DomainObject (clase del framework NA EVERNET, EL ORM PARA MAPEO) 
La ruta a este proyecto es:
Entidades -> Sondal...Entidad.NH -> Esquema -> NH    

Clases == Tablas; Objetos == Filas; Propiedades == Columnas.
--> 

<!-- Estos dos primeros proyectos vistos estan relacionados entre sí ya que referencian a los objetos, pero uno habla del visual y otro del de base de datos. Un proyecto se encarga de su presentación (DTO) y otro de su creación mediate mapeación (NH) mapeación que logramos con el ORM NA-EVERNET y los archivos de configuración .xml (en el proyecto Mappings) -->


                                                --SondalIConstruye.Framework.Enums
<!-- 
En este proyecto se encontrarán archivos con clases dentro que tendrán interfaces o metodos que devolverán opciones de interfaces. Las interfaces tendrán diferentes posibles que podrán devolver, separadas por comas. Por ej un interfaz tendrá todos los "Estados" de un pliego posibles, devolverá uno solo de ellos por cada pliego, en el código de la solución los comentamos para verlos en profundidad.
Habrá dos tipos de clases, las que contengan enumerados encargados de crear los diferentes estados y las clases que contengan los metodos que manejarán la lógica para retornar los estados del objeto correspondiente.
Ejemplo, tendremos una clase "Estados.cs" (en el Explorador de Soluciones) en sintaxis donde se accede a ella se llamara "EnuEstados", esta clase es del primer tipo posee muchos enumerados que contiene las diferentes opciones,estados, descripciones para diferentes objetos, ej hay un enumerado con los estados del ConvenioMarco y luego hay otra clase (EstadoConvenioMarcoEnum.cs) que mediante un metodo devuelve esta información, esta información se argumenta al metodo y se obtiene desde el enumerado en el otro archivo.
Entonces los archivos con enumerados tienen fines de capa de datos (data layer) y los archivos con metodos que son argumentados con los valores de estos enumerados para ser devueltos en el front end tienen fines de capa de negocio (business layer)  

<!-- Archivo con metodo que devuelve un valor obtenido de un enumerado : -->
EstadoConvenioMarcoEnum.cs
-->


                                                --SondalIConstruye.Framework.Hubs
<!-- 
-->


                                                --SondalIConstruye.Framework.Mappings
<!-- 
En este proyecto que es de acceso a datos se encuentran archivos .XML. Estos archivos se encargarán de cumplir el mapeo entre las filas de las tablas de la DB y los objetos de las clases del IDE, son archivos de configuración. Estos archivos tendrán etiquetas que deberemos llenar con la información adecuada para representar la tabla y clase mapeadas entre si.
Ejemplo:
--> 
<class name="Pliego" schema="PLI" table="pliego">
<id name="Id" column="IdPliego" type="long" unsaved-value="0">
    <generator class="identity"/>
</id>
<property name="NumeroPliego" type="string">
<property name="FechaCreacion" type="DateTime">
<!-- La etiqueta class pide los nombres de la tabla y clase a mapear además del esquema donde se ubican -->
<!-- La etiqueta ID generará una identificación para este mapeo realizado PREGUNAR GUILLE.-->
<!-- La etiqueta property representa a las propiedades/columnas de la clase/tabla, indicamos su nombre y su tipado -->
<!-- El framework NA EVERNET se ocupará al hacer de hacer las tareas al nosotros ejecutarlas con: Pliego.Save(), Pliego.Find() o la que corresponda. -->


FIN SECCIÓN ENTIDADES



<!-- 
 -->


SECCIÓN: 

2. Interfaces (11 proyectos) (Interfaces, Interop, VOY POR ACA Anses, GDE, LoginAuth, OAuthServer)
<!-- Aquí es donde nos podremos conectar a los servicios externos al necesitarlos, hay diferentes maneras para hacer esto, podemos crear el enchufe que necesitamos, lo uso y lo "tiró" Ej: autorizar en sidico, debemos llamar al servicio externo, podemos hacer la referencia del servicio externo, crear el webservice local a nivel código, llamarlo y manejar el resultado, pero hay que hacerlo muchas veces en todo el proyecto, llamar al mismo servicio )clases de Service references) o distintos, o incluso hay veces que el extremo del servicio cambia (cambio de sistema, en este caso se deberá modificar todos los llamados al servicio del sistema anterior, al tener la sección interfaces tendremos fácilidad para encontrar estos llamados) -->

<!-- Esta sección es donde se encontrarán todos los llamados a servicios externos o locales que hayamos realizado. Necesitaremos de ciertos sistemas/servicios externos. 
Ej: Autorizar en SIDICO, obtener número de expediente en GDE.

<!-- Empecemos con sus subsecciones -->
- SUBSECCIÓN "INTERFACES"
<!-- Esta sección manejará los servicios locales, los de la solución SEAC (COMPR.AR), no los de sistemas externos. Se divide en 5 proyectos, las desarrollamos a continuación: -->

                                                -Interfaces.Datos
<!-- En este proyecto se crea, actualiza o busca un objeto de la clase ticket en la base de datos.
Mediante metodos que llaman y ejecutan STORED PROCEDURES de la base de datos. La lógica consiste en mapear la base de datos y el procedure creando instancias de las clases correctas (Database, DbCommand) y en la asignación de esta instancia ejecutar un metodo para realizar el mapeo de ambos, estos metodos son: CreateDataBase() y GetStoredProcedure(), ambos metodos deben argumentarse con el nombre de la DB y del SP.-->
        


                                                -Interfaces.EntidadDTO
<!-- En este proyecto se encuentran las clases creadoras de los objetos visuales que serán manipulados por los servicios. Dentro de las clases tendremos las propiedades que podrán tener o no atributos, asi como podrán tener o no capacidades GET y SET. La clase tendrá los atributos [Serializable, DataContract]. En algunas clases habrá enumerados (contenedores de múltiples opciones != de las cuáles solo una será devuelta). -->



                                                -Interfaces.Interfaces
<!-- En este proyecto se crea una interface pública que almacena todos los servicios locales para usar sobre  SEAC. Cada servicio tendrá un atributo descriptivo == [OperationContract]
Estos servicios deberán ser argumentados con los objetos que deben manipular, objetos creados a partir del proyecto anterior (EntidadDTO)
Cada servicio de esta clase será referenciado en Interfaces.Servicios, donde se llamará finalmente.-->



                                                -Interfaces.Negocio
<!-- En este proyecto dentro de clases se encuentra la lógica de todos los servicios locales, identificados en la interfaz del proyecto "Interface". Luego estos estos metodos con la lógica son llamados en el proyecto "Servicios". -->

        - Este proyecto tendrá una carpeta "Web References"
   <!-- En ella, habrá archivos raros que desconozco que son que tendrán los servicios relacionados. Serán 5 archivos con diferentes servicios. Luego estos servicios se llamarán en las clases aisladas del primer nivel de jerarquía del proyecto en el que estamos (Interfaces.Negocio). -->



                                                -Interfaces.Servicios
<!-- En este proyecto se llamarán a los servicios desarrollados en las clases del proyecto "Negocio" se hará dentro de un metodo encapsulador que será el metodo final. 
Un ejemplo: -->
public bool SincronizarOrdenCompra(DocumentoContractualSIGAF documento)
{
    Negocio.ServicioBAC servicioBAC = new SondaIConstruye.Framework.Interfaces.Negocio.ServicioBAC(); 
    return servicioBAC.SincronizarOrdenCompra (documento); 
}

<!-- En estos metodos del proyecto Servicios no solo nos conectamos con Interfaces.Negocio por usar servicios de sus clases, si no tambien con Interfaces.Interfaces ya que el nombre de los metodos es el mismo que el de los servicios dentro de la interfaz en Interfaces.Interfaces y se puede comprobar viendo que la interfaz aparecen todos sus metodos como referenciados en este proyecto. -->

<!-- Fin de la sección de Interfaces Locales. Continuamos con las interfaces de los sistemas externos. -->






- SUBSECCIÓN "Interop" 
PROYECTOS:  
                --Datos: 
   <!-- tendrá los datos en una clase llamada "ProcesosDAO.cs".   -->
        
                --Interop: 
   <!-- tendrá dos carpetas (DTO && EXCEPTIONS) donde se encontrarán el objeto visual (DictamenProcuracionDTO) y las excepciones controladas y 3 servicios. -->


CLASES SUELTAS: 
                --Conversor.cs
   <!-- En esta clase se realizarán conversiones de objetos DTO a NH. Literalmente hablando lo que haremos será trasnferir datos del DTO al NH. Serán dos objetos diferentes. Se crean metodos que reciben como argumentos objetos DTO. Ya en el flujo de ejecución de los metodos convertores primeramente se realiza la instancia de clase deseada, en este caso el objeto NH. Luego se comprueba que el argumento (objeto DTO) tenga datos, una vez comprobado que los tiene se realizan las trasnferencias de datos para crear el nuevo objeto NH requerido. Algunas transferencias requerirán de metodos de por medio ej: "PartidaPresupuestaria" (el primer metodo) -->

                --Servicio.cs
   <!-- En esta clase se crearán metodos que ejecutarán los servicios de interop, que se encuentran en la carpeta especial "ServicioSEAC" en Services References. Primero en el metodo deben crearse los objetos DTO que serán manipulados por el servicio y luego en un bloque try se ejecutará el servicio argumentado con el objeto creado. Se deben asignar valores a todas las propiedades necesarias del objeto DTO, estas se asignan con los argumentos del metodo.
   Hay metodos que usarán servicios del archivo de referencias "RenderizacionDocumentos", no todos vendrán de "ServiciosSEAC".
El error al llamar a "ServicioSEACClient" se soluciona borrando ServicioSEAC. su sintaxis predecesora.-->
 

                --UtilDTO.cs
   <!-- En esta clase se desarrollan metodos públicos y estáticos que crearán los objetos DTO necesarios en interop. Para esto debemos acceder a ellos via la "carpeta especial" (ServicioSEAC) anidada en "Services References" que es donde se encuentran las clases creadoras.
   <!-- AHORA LOS 4 PROYECTOS (BIBLIOTECAS DE CLASE) DEL PRIMER NIVEL DE JERARQUÍA -->

 FIN DE LA SUBSECCIÓN INTEROP.

AHORA ESTARÁN LOS 4 PROYECTOS SUELTOS DE LA SECCIÓN INTERFACES  

COMPRAR.Interfaces.ANSES
<!-- En este proyecto se encontrarán las interfaces de ANSES -->


 COMPRAR.Interfaces.GDE
<!-- En este proyecto se encontrarán las interfaces de GDE (que son todas las llamadas del expediente) -->


LoginAuth
<!-- La interface entre la solución de COMPRAR y la solución de AUTENTIFICACION (que debemos tener abierta para desarrollar en comprar, esta solución es otro sistema que se conecta con COMPRAR.)  -->


OAuthServer
<!--  -->



FIN DE LA SECCIÓN INTERFACES 



<!-- 
-->



<!-- SECCIÓN: -->
3. Procesos (44 proyectos)
<!-- El sistema tiene muchas tareas programadas que se deben ejecutar cada cierto tiempo (algunas online y otras offline, es decir cuando no haya usuarios operando) para ejecutarlas se crea un proyecto que contendrá una clase (Program.cs) que ejecutará los procesos. Para ejecutar estos procesos se deberá obtener una contraseña desde el archivo App.config, además debemos instanciar la clase que contiene al proceso (esta clase será en la mayoría de casos ServiciosSoapClient y se encontrará en el archivo de ConnectedServices, también pueden ser interfaces). Luego, en el bloque try con esa instancia heredaremos y ejecutaremos al proceso. 
Proyecto comentado en la solución: EjecucionVersionadoOfertas  -->



<!-- 
En esta sección habrá proyectos donde se llamarán servicios de una clase llamada ServiciosSoapClient, esta clase estará dentro de la carpeta especial anidada en "Services Refereces" en el mismo proyecto y nivel de jerarquía que la clase Program.cs (la que invoca a su servicio). La clase ServiciosSoapClient además antes de ella tendrá un interface donde estarán todos los procesos disponibles del proyecto en el que nos encontremos.
-->


<!-- FIN SECCIÓN PROCESOS -->


<!-- 
-->


SECCIÓN:
4. Servicios (5 proyectos)
<!-- En esta sección se encuentra la mayor parte de la lógica de negocio.. Específicamente en el proyecto Servicios.Impl -->

PROYECTO                                                     -- Servicios
<!--Aquí se almacenarán dentro de una interface todos los servicios que se usarán en esta sección d la solución-->

PROYECTO                                                    -- ServiciosAFIP
<!-- Aqui -->

PROYECTO                                                    --Servicios.Impl
<!--  -->

PROYECTO                                                    --Servicios.Web
<!--  -->

PROYECTO                                                    --Sonda.Procesos.Servicios
<!--  -->



<!-- 
-->



5. Websites 
<!-- 
Es la capa de presentación de la aplicación web (el frontend). Contendrá los formularios webs. Tendrá 3 proyectos (en la solución SEAC) también usaremos el proyecto de la solucion APICOMPRAR. 
Necesitamos que estos 3 proyectos de Websites se ejecuten simultaneamente, para eso hacer la siguiente configuración, en la solución Click derecho -> Propiedades -> Proyecto de inicio -> Proyectos de inicio múltiples (chx checked) y en el cuadro buscar los 3 proyectos e indicar "Iniciar"
-->
PROYECTO                                                    Sonda.Framework.Website.Web
<!-- En este proyecto se encontrará la página de COMPR.AR. Todos los formularios a los que podemos acceder navegando por comprar. -->

PROYECTO                                                    Sonda.Procesos.Web
<!-- En este proyecto se encontrarán todas las tareas programadas, es decir, los procesos. -->

PROYECTO                                                    SondaConstruye.Framework.Interfaces.Host
<!-- En este proyecto se encontrarán las llamadas a otros servicios. Es decir, cada vez que deba llamar a algún servicio externo (GDE, API DE USUARIOS) se deberá usar este proyecto de interface. -->






<!-- RAMAS USADAS EN SEAC -->
El repositorio tendrá 3 ramas fijas (hotfix, testing, prod). Las ramas que se crean heredan el contenido de otra. 

HOTFIX (corrección de errores)
<!-- Esta rama es una copia de prod, en ella se corrigen errores de producción. 
Al completarse la corrección, la rama se fusiona en la rama principal tanto en las ramas de desarrollo activas como sea necesario para asegurar que el problema se resuelva en todas las versiones futuras del software. -->

TESTING 
<!-- Esta rama se utiliza para realizar un testeo de las nuevos cambios antes de hacerle el pull request a la rama de producción. -->

PROD
<!-- En esta rama se encuentra el proyecto expuesto a los clientes. El producto final.
Los cambios de esta rama se realizan a través de fusiones de ramas de desarrollo, no se usa para realizar cambios. -->

Para desarrollar debemos crear una nueva rama parados en la rama que corresponda según nuestra tarea. Es decir, para realizar modificaciones de producción, nos paramos en hotfix, creamos una rama propia para desarrollar que herede de hotfix y allí podemos desarrollar sin arruinar hotfix. Una vez notemos que en nuestra rama clon de hotfix estan correctos pasamos los cambios a hotfix (git checkout rama--file o pull request?), y de allí se deploya en el ambiente de pruebas, si esta todo correcto se pasa a producción (pull request) y finalmente allí se hace el despliegue.



<!-- EXTRAS -->
Con CTRL + F12 nos redirecciona a la implementación de lo buscado, mientras que con f12 nos llevará a su interfaz.

<!-- ATRIBUTOS VISTOS EN LA SOLUCIÓN -->
[Serializable] 
<!-- Indica que todos los campos públicos y privados (no estáticos) de la clase se pueden serializar. Por lo tanto, los objetos de esa clase pueden ser convertidos en un flujo de bytes que pueden ser almacenados o transmitidos. Esto es especialmente útil en aplicaciones que necesitan persistir datos o comunicarse con otros sistemas. -->
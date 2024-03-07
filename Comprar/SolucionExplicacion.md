La solución se divide en diferente secciones que serán carpetas, las más importantes son:

1. Entidades
2. Interfaces
3. Procesos
4. Servicios
5. WebSites


<!-- En este archivo desarrollaremos las características de cada sección. En la solución están los comentarios explicativos de la sintaxis del código.-->

1. Entidades (5 proyectos)
<!-- Esta sección es la capa de las entidades de se encontrarán los objetos que serán mapeados al proyecto desde la base de datos, específicamente desde las tablas, sus filas serán las entidades mapeadas como objetos. 
Cada sección tiene diferentes proyectos (bibliotecas de clases que se encargarán de diferentes tareas con relación a estos objetos). 

PROYECTOS (bibliotecas de clases) -->
SondaIConstruye.Framework.(Entidad.DTO/Entidad.NH/Enums/Hubs/Mappings)
<!-- Cada proyecto tendrá muchas carpetas dentro, esto refiere a los esquemas de la DB. Cada esquema tendrá sus clases que contendrán el código que crea y maneja a las Entidades.-->



<!-- PROYECTOS: -->
                                                --SondalIConstruye.Framework.Entidad.DTO
<!-- 
En este proyecto se encontrará el objeto visual. Es el objeto que será devuelto en el Frontend. 
(DTO == Data Transfer Object; Objeto de transferencia de datos) 
Los objetos de este proyecto son el puentes entre la sección de datos y el resto de secciones de la solución.
La sección de datos (seccion "Entidades") solo ve los objetos de bases de datos, los del proyecto NH pero cuando lo tiene que compartir a la presentación o a la interfaz lo que se comparte es el DTO, NO EL NH.
-->


                                                --SondaIConstruye.Framework.Entidad.NH
<!--
En este proyecto se encontrarán los objetos de la base de datos, es decir es la creación más completa y auténtica posible del objeto. Es el objeto Backend, no se mostrará en el frontend. 
Estos objetos se crearán a partir de clases que determinarán sus propiedades y metodos, estarán en la carpeta "NH" en el esquema correspondiente (carpeta) dentro del proyecto.
LAS CLASES DE ESTE PROYECTO HEREDERÁN DE DomainObject (clase del framework NA EVERNET, EL ORM PARA MAPEO) 
La ruta a este proyecto es:
Entidades -> Sondal...Entidad.NH -> Esquema -> NH    

Clases == Tablas; Objetos == Filas; Propiedades == Columnas.
--> 

<!-- Estos dos primeros proyectos vistos estan relacionados entre sí ya que referencian a los objetos, pero uno habla del visual y otro del de base de datos. Un proyecto se encarga de su presentación (DTO) y otro de su creación mediate mapeación (NH) mapeación que logramos con el ORM NA-EVERNET y los archivos de configuración .xml (en el proyecto Mappings) -->


                                                --SondalIConstruye.Framework.Enums
<!-- 
En este proyecto se encontrarán clases dentro tendrán interfaces, estos devolverán una opción entre muchas posibles. Por ej un interfaz tendrá todos los "Estados" de un pliego posibles, y devolverá uno solo de ellos por cada pliego, en el código de la solución los comentamos para verlos en profundidad.
Habrá dos tipos de clases, las que contengan enumerados encargados de crear los diferentes estados y las clases que contengan los metodos que manejarán la lógica para retornar los estados del objeto correspondiente.
Ejemplo, tendremos una clase "Estados.cs" (en el Explorador de Soluciones) en sintaxis donde se accede a ella se llamara "EnuEstados", esta clase es del primer tipo posee muchos enumerados que contiene las diferentes opciones,estados, descripciones para diferentes objetos, ej hay un enumerado con los estados del ConvenioMarco y luego hay otra clase (EstadoConvenioMarcoEnum.cs) que mediante un metodo devuelve esta información, esta información se argumenta al metodo y se obtiene desde el enumerado en el otro archivo.
Entonces los archivos con enumerados tienen fines de capa de datos (data layer) y los archivos con metodos que son argumentados con los valores de estos enumerados para ser devueltos en el front end tienen fines de capa de negocio (business layer)  
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






<!-- 
 -->




2. Interfaces (11 proyectos)

<!-- Esta sección es donde se encontraran todos los llamados a servicios externos o locales que hayamos realizado. Necesitaremos de ciertos sistemas/servicios externos. 
Ej: Autorizar en SIDICO, obtener número de expediente en GDE.

En el primer nivel de jerarquía se encuentran 2 secciones (carpetas con proyectos dentro) y 4 proyectos sueltos (bibliotecas de clases) las explicaremos: -->

- Sección "Interfaces"
<!-- Esta sección manejará los servicios locales. Se divide en 5 proyectos, ellos harán referencia a los datos, los objetos DTO, las interfaces, la lógica de negocio y los servicios -->

                                                -Interfaces.Datos
<!-- En este proyecto se realiza un create, update o select de un objeto (ticket) en la base de datos.  -->
        


                                                -Interfaces.EntidadDTO
<!-- En este proyecto se encuentran los objetos que serán manipulados por los servicios,  -->



                                                -Interfaces.Interfaces
<!-- En este proyecto se crea una interface pública que almacena el total de los servicios disponibles para usar sobre la solución local SEAC. Cada servicio tendrá un atributo descriptivo. [OperationContract]
Estos servicios serán argumentados con los objetos que manipulen, que se encontrarán usualmente en el proyecto "Interfaces.EntidadDTO"
Cada servicio de esta clase será referenciado en Interfaces.Servicios -->



                                                -Interfaces.Negocio
<!-- En este proyecto dentro de clases se encuentra la lógica de todos los servicios locales, identificados en la interfaz del proyecto "Interface". Luego estos estos metodos con la lógica son llamados en el proyecto "Servicios". -->

        - Este proyecto tendrá una carpeta "Web References"
   <!-- En ella, habrá archivos raros que desconozco que son que tendrán los servicios relacionados. Serán 5 archivos con diferentes servicios. Luego estos servicios se llamarán en las clases aisladas del primer nivel de jerarquía del proyecto en el que estamos (Interfaces.Negocio). -->



                                                -Interfaces.Servicios
<!-- En este proyecto se llamarán a los servicios desarrollados en las clases del proyecto "Negocio" se hará mediente un metodo que será el final. 
Un ejemplo: -->
public bool SincronizarOrdenCompra(DocumentoContractualSIGAF documento)
{
    Negocio.ServicioBAC servicioBAC = new SondaIConstruye.Framework.Interfaces.Negocio.ServicioBAC(); 
    return servicioBAC.SincronizarOrdenCompra (documento); 
}

<!-- En estos metodos del proyecto Servicios no solo nos conectamos con Interfaces.Negocio por usar servicios de sus clases, si no tambien con Interfaces.Interfaces ya que el nombre de los metodos es el mismo que el de los servicios dentro de la interfaz en Interfaces.Interfaces y se puede comprobar viendo que la interfaz aparecen todos sus metodos como referenciados en este proyecto. -->

<!-- Fin de la sección de Interfaces Locales. Continuamos con las interfaces de los sistemas externos. -->






- Sección "Interop" 
<!-- PROYECTOS:  -->
                --Datos: 
   <!-- tendrá los datos en una clase llamada "ProcesosDAO.cs".   -->
        
                --Interop: 
   <!-- tendrá dos carpetas (DTO && EXCEPTIONS) donde se encontrarán el objeto visual (DictamenProcuracionDTO) y las excepciones controladas y 3 servicios. 


<!-- CLASES: -->
                --Conversor.cs
   <!-- Esta clase convertirá los datos de Entidades tanto DTO, NH, como entidades provenientes del archivo ServicioSEAC que es uno de los 3 archivos de referencias en "Service References"  -->

                --Servicio.cs
   <!-- En esta clase se crearán metodos que ejecutarán los servicios de interop, que se encuentran en la carpeta especial "ServicioSEAC" en Services References. Primero en el metodo deben crearse los objetos DTO que serán manipulados por el servicio y luego en un bloque try se ejecutará el servicio argumentado con el objeto creado. Se deben asignar valores a todas las propiedades necesarias del objeto DTO, estas se asignan con los argumentos del metodo.
   Hay metodos que usarán servicios del archivo de referencias "RenderizacionDocumentos", no todos vendrán de "ServiciosSEAC".
El error al llamar a "ServicioSEACClient" se soluciona borrando ServicioSEAC. su sintaxis predecesora.-->
 

                --UtilDTO.cs
   <!-- en esta clase se desarrollan metodos públicos y estáticos que crearán los objetos DTO necesarios en interop. Para esto debemos instanciar la clase que los posee para heredarlos, en este caso accedemos a la "carpeta especial" (ServicioSEAC) anidada en "Services References".

   <!-- AHORA LOS 4 PROYECTOS (BIBLIOTECAS DE CLASE) DEL PRIMER NIVEL DE JERARQUÍA -->




<!-- 
-->




3. Procesos (44 proyectos)
<!-- 
En esta sección habrá proyectos donde se llamarán servicios de una clase llamada ServiciosSoapClient, esta clase estará dentro de la carpeta especial anidada en "Services Refereces" en el mismo proyecto y nivel de jerarquía que la clase Program.cs (la que invoca a su servicio). La clase ServiciosSoapClient además antes de ella tendrá un interface donde estarán todos los procesos disponibles del proyecto en el que nos encontremos.
-->




<!-- 
-->




4. Servicios (5 proyectos)
<!-- 
 -->




<!-- 
-->




5. Websites 
<!-- 
Es la capa de presentación de la aplicación web (el frontend). Contendrá los formularios webs. 
-->





<!-- EXTRAS -->
[Serializable] 
//Indica que todos los campos públicos y privados (no estáticos) de la clase se pueden serializar. Por lo tanto, los objetos de esa clase pueden ser convertidos en un flujo de bytes que pueden ser almacenados o transmitidos. Esto es especialmente útil en aplicaciones que necesitan persistir datos o comunicarse con otros sistemas.
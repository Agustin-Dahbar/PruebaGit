La solución se divide en diferente secciones que serán carpetas, las más importantes son:

1. Entidades
2. Interfaces
3. Procesos
4. Servicios
5. WebSites


<!-- En este archivo desarrollaremos las características de cada sección. En la solución están los comentarios explicativos del código.-->

1. Entidades (5 proyectos)
<!-- En esta sección se encontrarán los objetos que serán mapearados al proyecto desde la base de datos, específicamente desde las tablas, sus filas serán las entidades mapeadas como objetos. 
Cada sección tiene diferentes proyectos (bibliotecas de clases que apuntan a diferentes cosas pero con relación a los mismos objetos existentes).

PROYECTOS (bibliotecas de clases) -->
SondaIConstruye.Framework.(Entidad.DTO/Entidad.NH/Enums/Hubs/Mappings)
<!-- Cada proyecto tendrá muchas carpetas dentro, esto refiere a los esquemas de la DB. Cada esquema tendrá sus clases que contendrán el código que crea y maneja a las Entidades.-->


<!-- PROYECTOS: -->
--SondalIConstruye.Framework.Entidad.DTO
<!-- 
En este proyecto se encontrará el objeto visual. DTO == Data Transfer Object. 
Los objetos de este proyecto serán los puentes entre la capa de datos y el resto de las capas de la solución.
(capas == secciones / carpetas que dividen la solución) 
La capa de datos (seccion "Entidades" ) solo ve el objeto del proyecto NH que estabamos viendo antes pero cuando lo tiene que compartir a la presentación o a la interfaz lo que se comparte es el DTO, es decir el objeto del proyecto .DTO, no el del proyecto .NH
-->


--SondaIConstruye.Framework.Entidad.NH
<!--
En este proyecto se encontrará el objeto de base de datos se crearán a partir de clases que determinarán las propiedades y metodos de los mismos, estarán en la carpeta "NH" en cualquier esquema dentro del proyecto. Las clases representan las tablas, las propiedades las columnas, y los objetos las filas. La ruta a este proyecto es:
Entidades -> Sondal...Entidad.NH -> Pliego -> NH  
--> 

<!-- Estos dos primeros proyectos vistos estan relacionados entre sí ya que referencian a los objetos, pero uno habla del visual y otro del de base de datos. Un proyecto se encarga de su presentación (DTO) y otro de su creación mediate mapeación (NH) mapeación que logramos con el ORM A-EVERNET y los archivos de configuración .xml (en el proyecto Mappings) -->


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
En este proyecto se encuentran archivos .XML. Estos archivos se encargarán de cumplir el mapeo entre las filas de las tablas de la DB y los objetos de las clases del IDE, son archivos de configuración. Estos archivos tendrán etiquetas que deberemos llenar con la información adecuada para representar la tabla y clase mapeadas entre si.
Ejemplo:
--> 
<class name="Pliego" schema="PLI" table="pliego">
<id name="Id" column="IdPliego" type="long" unsaved-value="0">
    <generator class="identity"/>
</id>
<property name="NumeroPliego" type="string">
<property name="FechaCreacion" type="DateTime">
<!-- La etiqueta class pide los nombres de la tabla y clase a mapear además del esquema donde se ubican.  -->
<!-- La etiqueta property representa a las propiedades de la clase/tabla, indicamos su nombnre y su tipado -->





<!-- 
 -->




2. Interfaces (11 proyectos)

<!-- Esta sección es donde mediante los proyectos (bibliotecas de clases) nos pondremos en contacto con los servicios externos (sistemas) para llevar a cabo tareas que requieran de ellos. 
Ej: Si necesitamos autorizar en SIDICO, obtener un número de expediente de GDE.

En el primer nivel de jerarquía se encuentran 2 secciones (carpetas) y 4 proyectos (bibliotecas de clases) las explicaremos: -->

    - Sección "Interfaces"
<!-- aquí se encontrarán en 5 proyectos diferentes los datos (Datos), los objetos (Entidad.DTO), las interfaces (Interface), los servicios (Servicios) y la lógica de negocio (Negocio) de la sección PADRE "Interfaces". Esta sección hija es la más importante de la sección padre (ambas "Interfaces"). -->


    - Sección "Interop" 
<!-- tendrá dos proyectos  -->
        --Datos: 
<!-- tendrá los datos en una clase llamada "ProcesosDAO.cs".   -->
        
        --Interop: 
<!-- tendrá dos carpetas (DTO && EXCEPTIONS) donde se encontrarán el objeto visual (DictamenProcuracionDTO) y las excepciones controladas. 

También tendrá 3 clases en el mismo nivel de jerarquía a estas carpetas. -->

        --Conversor.cs
<!-- esta clase convertirá los datos de varios objetos visuales (DTO) -->

        --Servicio.cs
<!-- esta clase tendrá el servicio para conectarse con SIGAF. -->
 

        --UtilDTO.cs
<!-- en esta clase se desarrollan metodos públicos y estáticos que instanciaran clases de la solución es decir, crearán objetos. Para lograr esto necesitamos un servicio local, este busca a estas clases que se ubican en otra parte del código de la solución. Los valores de las propiedades se asignan con los parametros del metodo público y estático ejecutado.
Domicilio, ClasificadorPresupuestario, Comprobante son alguna de las clases instanciadas en esta clase.  -->

<!-- AHORA LOS 4 PROYECTOS (BIBLIOTECAS DE CLASE) DEL PRIMER NIVEL DE JERARQUÍA -->




<!-- 
-->




3. Procesos (44 proyectos)
<!-- 
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
Es la capa de presentación, es decir el front end. Contendrá los formularios webs. 
-->





<!-- EXTRAS -->
[Serializable] 
//Indica que todos los campos públicos y privados (no estáticos) de la clase se pueden serializar. Por lo tanto, los objetos de esa clase pueden ser convertidos en un flujo de bytes que pueden ser almacenados o transmitidos. Esto es especialmente útil en aplicaciones que necesitan persistir datos o comunicarse con otros sistemas.
<!-- LOS MAS IMPORTANTES: -->

 SECCION ENTIDADES 

<!-- PROYECTO ENUMERADOS -->
Estados.cs (clase de SondalConstruye.Framework.Enums) <!--ENUMERADOS-->
<!--Este archivo contendrá todos los enumerados que representen los diferentes estados posibles d las entidades-->
EstadoConvenioMarcoEnum.cs (clase de SondalConstruye.Framework.Enums) <!--METODO-->
<!-- Este archivo contendrá un metodo llamado GetDescription() que devolverá un string, este string se obtendrá del enumerado EstadoConvenio que proviene del archivo Estados.cs. La lógica de estos metodos es crear un arreglo de strings  -->
EstadoConvenioMarcoEnum.cs (clase de SondalConstruye.Framework.Enums) <!--METODO-->
<!-- Contiene metodo que devuelve el estado del ConvenioMarco al recibirlo como argumento.  -->

EstadoSolicitudCompraEnum (clase de SondalConstruye.Framework.Enums) <!--METODO-->
<!-- Esta clase se encarga de devolver el estado de la solicitud de compra, el orden de sucesos es:
Se crea una propiedad que almacenará el estado, estará tipada con el enumerado del que vendrá el valor. 
Luego se declara un metodo que se argumenta con el valor del estado de la solicitud, proveniente del enumerado, ese argumento es asignado como valor de la propiedad declarada anteriormente.
Declaramos un metodo (Value) que le dará la capacidad get y set a la propiedad "value" la que almacenará el valor del estado. 
Por último se crea el metodo que devolverá el valor de la propiedad es decir, el estado de la solicitud de compra.  -->


<!-- 
 -->


SECCIÓN INTERFACES   
<!-- SUBSECCIÓN INTERFACES-->
<!-- PROYECTO DATOS -->
ProcuracionDAO.cs (clase de Interfaces.Datos)
<!-- Este archivo contiene metodos que ejecutan procedimientos de la DB. Se debe realizar la adaptación del procedimiento a C# y luego se realiza la ejecución del mismo para realizar una solicitud GET || POST || PUT  -->

<!-- PROYECTO ENTIDADDTO-->
DetalleBoleta.cs (clase de Interfaces.EntidadDTO)

<!-- PROYECTO INTERFACE -->
IServicioSEAC.cs (Interfaces.Interface)
<!-- Este es el archivo que contiene la interface que encapsula todos los servicios locales. A la interface se le da el atributo [ServiceContract] que indica que la interface es un servicio de comunicación en un sistema basado en servicios web. Esto significa que otros programas puedan comunicarse con la interface a través de servicios web. Dentro de la interface se encontrarán todos los metodos que representarán a los servicios de SEAC, cada uno de ellos tendrá el atributo [OperationContract] que indica que el metodo es una operación que está disponible para ser invocada y usada por los clientes conectados a través del servicio web. Este atributo se utiliza en conjunto con [ServiceContract] -->

<!-- PROYECTO NEGOCIO  -->
ServicioBAC.cs (clase de Interfaces.Negocio)
<!-- En este archivo se llama a los servicios ubicados dentro de clases en la carpeta especial "WCF_BAC" de "Services References". Habrá diferentes regiones en el archivo que tendrán sus propios servicios. Ejemplo la Region "Proveedores". En esta región se llamarán a los servicios "AltaProveedor", "ModificacionProveedor", "BajaProveedor"  que se ubicarán en la clase "ServicioClient" (7280, (7357, 7361, 7365)) == líneas de código de la clase y sus servicios en la carpeta especial WCF_BAC.
Esta clase ServicioClient de WCF_BAC solo será referenciada por este archivo (ServicioBAC.CS) y PresupuestoSIGAF.cs. El resto de archivos de Interfaces.Negocio no la usan. -->

WCF_BAC (Interfaces.Negocio.Service References)
<!-- Estos archivos dentro de "Service References" sirven para almacenar lógica o llamados a servicios que usarán el resto de archivos de la interfaz Negocio. Aquí estarán las referencias hechas al llamar servicios, de ahí el nombre de la sección. En el se encuentran clases, enumerados, interfaces, metodos, etcetera. Hay clases con distintos fines, por ejemplo, primero se declarán las clases que crearán los objetos involucrados en los servicios, para que estos sean los argumentos de los próximos servicios, las propiedades de estas clases tendrán una sintaxis desarrollada ya que se les darán capacidades de get y set y además en caso de SET se comprobará que el nuevo valor sea != al aún actual. Ya con esas clases que nos aseguren tener los argumentos de los servicios, creamos otras clases que encapsularán los servicios, no la lógica de ellos, si no el llamado a ellos, la lógica estará en un sistema externo..   -->

ConversorGetBenificiario.cs (clase de Interfaces.Negocio)
<!-- Este archivo contiene un metodo que se encarga de hacer una conversión de un objeto, en este caso un de "beneficiarioBean" a un "BeneficiarioSidif" 
Este archivo no se conecta con el mismo archivo de "Web Services" para obtener los datos necesarios de sistemas externos, si no que lo hace con eSidifGetBeneficiario.   -->


eSidifGetBeneficiario (Interfaces.Negocio.Service References)
<!-- Este es otro de los archivos que almacena las referencias de los servicios. Es el usado por la clase vista anterior. Lo usamos para heredar la clase con la que tiparemos al argumento.   -->



<!-- PROYECTO SERVICIOS -->
ServicioSEAC.cs (Interfaces.Servicios)
 <!-- En el se crean metodos encapsuladores con try/catch que ejecutan los servicios locales desarrollados en las clases del proyecto "Negocio" de Interfaces.Negocio.
 Los nombres de estos metodos coinciden con los nombres de los metodos anidados en la interface IServicioSEAC ubicada en el proyecto "Interface" -->



-SUBSECCIÓN INTEROP 
<!-- PROYECTO: FRAMEWORK.INTEROP -->
ServicioSEAC (Framework.Interop.ServicioSEAC) Archivo dentro de "Service References" 
<!--
Este "archivo" tiene muchas clases, enumerados e interfaces. De aquí las clases del proyecto obtendrán este tipo de cosas. Hay clases para crear objetos usados en los servicios de esta sección (Interop) y tambien hay clases que tienen metodos que realizan el llamado a los servicios de los sistemas externos, estos metodos son los que se llaman en el archivo "Servicio.cs".
Ej, hay una clase "ServicioSEACClient" que tiene los metodos con los llamados a los servicios de "AltaProveedor", "ModificacionProveedor" Ej de un metodo que llama a un servicio externo. 
-->
public bool ModificacionProveedor(SondaIConstruye.Framework.Interop.ServicioSEAC.Proveedor proveedor) {
    return base.Channel.ModificacionProveedor(proveedor);
}

<!--
Aunque si el archivo se llama ServicioSEAC no tiene mucho sentido pensar que son servicios externos, pero si no lo son, donde esta la lógica de los mismos entonces?  
-->

Conversor.cs
<!-- 
En este archivo se realizan conversiones de objetos DTO (visuales) a objetos NH (de base de datos). Literalmente hablando es una transferencia de datos. La lógica consiste en que el metodo recibe al objeto DTO. Se crea un objeto NH. Se comprueba que el argumento (objeto DTO) tenga valores para transferirle al objeto NH. Si los tiene llevamos a cabo la trasnferencia de valores, o mas bien un copy and paste ya que el objeto DTO no se borra ni pierde sus valores. Algunas trasnferencias requerirán de metodos como la conversión de la "PartidaPresupuestaria". Otros como la conversión del "ImporteCredito" serán muy simples nh.prop == dto.prop
 -->

Servicio.cs (Framework.Interop) Archivo suelto en el proyecto.
<!--
En esta clase se crearán metodos que ejecutarán los servicios de interop, que se encuentran en la carpeta especial "ServicioSEAC" en Services References. Primero en el metodo deben crearse los objetos DTO que serán manipulados por el servicio y luego en un bloque try se ejecutará el servicio argumentado con el objeto creado. Se deben asignar valores a todas las propiedades necesarias del objeto DTO, estas se asignan con los argumentos del metodo.
   Hay metodos que usarán servicios del archivo de referencias "RenderizacionDocumentos", no todos vendrán de "ServiciosSEAC".
El error al llamar a "ServicioSEACClient" se soluciona borrando ServicioSEAC. su sintaxis predecesora.
-->

Util.DTO (Framework.Interop) Archivo suelto en el proyecto.
<!-- 
En esta clase se desarrollan metodos públicos y estáticos que crearán los objetos DTO necesarios en interop. Para esto debemos acceder a ellos via la "carpeta especial" (ServicioSEAC) anidada en "Services References".
 -->
 



<!-- PROYECTO: FRAMEWORK.INTEROP.DATOS -->
ProcesosDAO
<!-- En este archivo se crean metodos que ejecutarán procedimientos de la base de datos. Estos procedimientos tienen que ver con la modificación del estado del proceso en interop.
La lógica para el mapeo del procedimiento es la siguiente.
 Primero mapeamos la base de datos en una instancia de la clase "Database", la inicializamos con el metodo que la mapeará ( CreateDatabase() ) argumentamos el metodo con el nombre de la base de datos.
 Segundo mapeamos el procedimiento en una instancia de la clase DbCommand, inicializamos la instancia con el metodo que mapeará al procedure( GetStoredProcCommand() ) lo argumentamos con el nombre del procedure. Para ejecutar este metodo debemos estar parados sobre la instancia de la DB recién creada. -->




 SECCIÓN SERVICIOS 

<!-- PROYECTO: SERVICIOS -->
IUsuarioService.cs (Servicios.Servicios esquema Adm)
<!-- 
 Aquí se encontrarán todos los servicios disponibles. De aquí se llamaran al ser usados en los otros proyectos de la sección "Servicios"
 -->

<!-- PROYECTO: SERVICIOS.IMPL -->
MensajeriaOrdenCompraAbiertaService (Servicios.IMPL esquema OC)

AbstractMensajeriaService (Servicios.IMPL esquema Broker)

<!-- 
 -->




SECCION PROCESOS 
<!-- Cada proceso será un proyecto que dentro tendrá una clase (Program.cs) con sus Services References -->
EjecucionVersionadoOfertas (proyecto que contendrá el ejecutable Program.cs donde se llamará al proceso requerido)





SECCIÓN WEBSITES
<!--  PROYECTO: SondaIConstruye.Framework.Interfaces.Host-->
Global.asax
<!-- Esta clase tendrá metodos para manejar los diferentes eventos de la aplicación web en el largo de su ciclo de vida, estos metodos provienen de la clase HttpApplication, por lo tanto hay que darle la herencia correspondiente a la clase. -->
ServicioSEAC.svc
<!-- En este archivo habrá una etiqueta que hara la referencia  -->












                                                            ENTIDADES
   <!-- SondalConstruye.Framework.Entidad.DTO -->
           

   <!-- SondalConstruye.Framework.Entidad.NH -->
        Aclaratoria.cs          (Pliego)     (Esquemas)
        Circular.cs             (Pliego)
        Convenio Marco          (Pliego)
        Pliego.cs               (Pliego)
        Evaluador               (Evaluación)
        EvaluadoresConsiderados (Evaluación)

   <!-- SondalConstruye.Framework.Enums -->
        Estados.cs 
        Tipos.cs   
        EnuRibs.cs
        EnumOc.cs


                                                            INTERFACES
   
Esta sección tiene una sección menor que se llama igual a ella, en ella se manejan los servicios locales. Se divide en 5 proyectos, ellos harán referencia a los datos, los objetos DTO, las interfaces, la lógica de negocio y los servicios.

-INTERFACES (CARPETA-SECCIÓN HIJA)
<!-- SondalConstruye.Framework.Interfaces.Datos -->
        ProcuracionDAO.cs 

<!-- SondalConstruye.Framework.Interfaces.Entidades.DTO -->
        ConsultaExpedienteDetallado.cs

<!-- SondaIConstruye.Framework.Interfaces.Interface  -->
        IServicioSEAC.cs (interfaz con los servicios)

<!-- SondaIConstruye.Framework.Interfaces.Negocio -->
        Procuracion.cs
        ServicioIntercomunicacionBAC (en este proyecto heredaremos servicios del siguiente: )
   
   <!-- Carpeta "Web References" en "Interfaces.Negocio" -->
        IntercomunicacionBAC 
        
<!-- SondalConstruye.Framework.Interfaces.Servicios -->
        ServicioSEAC (Esta clase heredará de la interfaz IServicioSEAC.cs (Línea 34) para usar sus servicios) 



<!-- SondaIConstruye.Framework.Interfaces.Servicios -->
        ServicioSEAC.cs
        

- INTEROP (CARPETA-SECCIÓN HIJA)






                                                            PROCESOS





                                                            SERVICIOS 












                                                            WEBSITES

<!-- Sección: Controles -->
<!-- header.ascx  -->
     es el header del menú principal de cualquier perfil de este Control desencadenamos en:
   <!-- CambiarClave.aspx -->
     Es el web form donde se cambia la clave. Se encuentra en el esquema RIUPP (carpeta).
   <!--  -->
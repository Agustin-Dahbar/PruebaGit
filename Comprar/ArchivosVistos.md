<!-- LOS MAS IMPORTANTES: -->


<!-- SECCIÓN INTERFACES  --> NAMESPACE DE LOS ARCHIVOS ENTRE ()

<!-- Sección menor Interfaces -->
ServicioSEAC.cs (Interfaces.Servicios)
 <!-- En el se crean metodos con try/catch que ejecutan los servicios locales desarrollados en las clases del proyecto "Negocio" de Interfaces.Interfaces.
 Los nombres de estos metodos coinciden con los nombres de los metodos de la interface IServicioSEAC ubicada en el proyecto "Interface" -->

IServicioSEAC.cs (Interfaces.Interface)
<!-- Este es el archivo que contiene la interface recientemente mencionada y que se encuentra en el proyecto "Interface" de Interfaces.Interfaces -->


<!-- Sección Interop -->

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

Servicio.cs (Framework.Interop) Archivo suelto en el proyecto.
<!--
En este archivo se llaman a los servicios que se encuentran en ServicioSEAC.
-->

Util.DTO (Framework.Interop) Archivo suelto en el proyecto.
<!-- 
En este archivo se desarrollan metodos que crean los objetos que se necesitarán para los servicios de interop. Estas clases instanciadas son las desarrolladas en el "archivo base" de este proyecto ServicioSEAC. 
 -->



<!-- PROYECTO: FRAMEWORK.INTEROP.DATOS -->
ProcesosDAO
<!-- Pendiente -->











<!-- Secciones -->













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
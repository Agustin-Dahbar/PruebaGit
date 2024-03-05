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
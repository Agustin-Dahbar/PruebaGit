La solución se divide en diferente secciones que serán carpetas, las más importantes son:

1. Entidades
2. Interfaces
3. Procesos
4. Servicios
5. WebSites


<!-- En este archivo desarrollaremos las características de cada sección. En otro archivo mostraremos un ejemplo de cada sección, y de cada proyecto de la misma. -->

1. Entidades
<!-- En esta sección se encontrarán los objetos que se mapearan al proyecto desde la base de datos, específicamente desde las tablas, sus filas serán las mapeadas como objetos. 
Tiene diferentes proyectos (bibliotecas de clases que apuntan a diferentes cosas pero con relación a los mismos objetos existentes).
Esta sección tiene diferentes proyectos (bibliotecas de clases) -->
SondaIConstruye.Framework.Entidad.DTO
SondaIConstruye.Framework.Entidad.NH
SondaIConstruye.Framework.Enums
SondaIConstruye.Framework.Hubs
SondaIConstruye.Framework.Mappings

<!-- Cada proyecto tendrá muchas carpetas dentro, esto refiere a los esquemas de la DB. Cada esquema tendrá sus clases -->

<!--
Las clases que determinarán el cuerpo de los objetos (sus propiedades y metodos) se encontrará en la carpeta NH dentro de cualquier esquema del proyecto "Entidad.NH" de la sección Entidades. La ruta es:
Entidades -> Sondal...Entidad.NH -> Pliego -> NH -> clases

-- "Pliego" simula ser el esquema en donde se encuentra la tabla.

-- "NH" específica que es la carpeta en donde estarán las clases que se realizará la creacion, las otras tienen otros motivos.
-->

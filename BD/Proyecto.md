#individual
La Universidad Mariano Gálvez de Guatemala cuenta con múltiples campus a lo largo del país. Cada campus posee una biblioteca con un catálogo único de libros, revistas y materiales digitales. A lo largo del tiempo, la gestión de préstamos, devoluciones, y la adquisición de nuevos  ejemplares se ha tornado complicada debido a la descentralización de información.

## Problema:
La falta de una base de datos centralizada genera inconvenientes como:  
1. Duplicidad de adquisiciones de ejemplares por desconocimiento del stock en otras bibliotecas. 
2. Estudiantes que no pueden acceder a ejemplares disponibles en otros campus.  
3. Falta de seguimiento puntual a préstamos vencidos y deterioro de ejemplares.  
## Objetivo:
Desarrollar un sistema de gestión integral para la cadena de bibliotecas universitarias que permita:  
1. Centralizar la información de todos los ejemplares disponibles en las distintas bibliotecas.  
2. Gestionar préstamos y devoluciones de manera eficiente, permitiendo a los estudiantes reservar ejemplares incluso de otros campus.  
3. Facilitar reportes sobre ejemplares más solicitados, préstamos vencidos y necesidades de adquisición  
## Entidades y Operaciones Básicas:
1. Bibliotecas: Cada una con su ubicación, encargado y horario.  
2. Ejemplares: Clasificados por tipo (libro, revista, material digital), con datos de autor, año, editorial y existencia por biblioteca.  
3. Estudiantes: Con datos personales, carrera, y registro de préstamos.  
4. Préstamos: Registro de ejemplares prestados, fecha de préstamo, fecha de devolución y estado.  
5. Reservas: Permitir que un estudiante pueda reservar un ejemplar, incluso si se encuentra en otro campus.

El sistema debe considerar la creación de TRIGGERS para la actualización automática del stock, así como PROCEDURES y VIEWS para facilitar consultas recurrentes y la generación de reportes. Adicionalmente, se deberá contemplar la creación de índices y optimización de consultas para garantizar la rapidez y eficiencia del sistema ante la gran cantidad de datos manejados.  
## Trigger
1. Actualizar stock tras un préstamo:  
Después de realizar un préstamo, se debe decrementar el stock del ejemplar  
correspondiente en la biblioteca.  
2. Actualizar stock tras una devolución:  
Al devolver un ejemplar, se debe incrementar el stock del mismo.  
## Vistas:  
1. Préstamos Activos:  
Vista que muestra todos los préstamos que no han sido devueltos.  
2. Ejemplares Sin Stock:  
Vista para identificar rápidamente qué ejemplares necesitan ser reabastecidos.  
## Procedimientos:  
1. Préstamos Vencidos de un Estudiante:  
Procedimiento que retorna la lista de préstamos vencidos para un estudiante en  
particular.  
2. Reservar Ejemplar:  
Procedimiento para facilitar la reserva de un ejemplar por parte de un estudiante,  
verificando si el ejemplar está disponible.  
## Consultas a responder:  
1. Consulta de Ejemplares Disponibles en una Biblioteca Específica  
2. Ejemplares Más Solicitados en el Último Mes  
3. Estudiantes con Préstamos Vencidos  
4. Ejemplares Disponibles de un Autor Específico  
5. Total, de Préstamos por Biblioteca en un Rango de Fechas  
6. Reservas Activas de un Estudiante  
7. Ejemplares que Deben ser Repuestos o Adquiridos Nuevamente (Stock 0)  
8. Préstamos Realizados por un Estudiante Específico  
9. Bibliotecas con Más Préstamos Activos  
10. Estudiantes que han Reservado un Ejemplar Específico
## Datos técnicos  
La universidad cuenta con la aprobación de Consejo Directivo para utilizar, Mysql, Workbench /  
HeidySQL para su desarrollo.  
Puede utilizar cualquier generar de datos de prueba para llenar la base de datos.  
## Entrega:  
1. Diagrama de entidad y relación (Glosario de tablas y relaciones)  
2. Video Publicado en YouTube con la solución dada al problema  
3. Entrega de todos los scripts para la base de datos, llenado, triggers, vistas, procedimientos, así como consultas.
4. Fecha de entrega: 28 de octubre 2023

# modelo principal

![](https://i.imgur.com/wX39XOW.png)
# Observaciones
![](https://i.imgur.com/EjqhSdb.png)

![](https://i.imgur.com/HG9e7Ca.png)



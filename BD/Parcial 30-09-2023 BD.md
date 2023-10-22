Estudiante: José Raúl Botzoc Mérida
Carnet: 4090-19-7994
Curso: Base de datso I
Tema: Segundo Parcial 
# Primera serie
Categorias de SQL Explique significado para que se utilizan, instrucciones que componen cada una de las categorias:

## DDL
### Significado
Es el lenguaje de definición de datos
### Para que se utilizan 
se utiliza para crear objetos modificar y eliminalos en la base de datos como los siguientes:
- Vistas 
- Tablas
- Indices
### Instrucciones
Estan son para crear:
```SQL 
CREATE TABLE "NOMBRE DE LA TABLA"(atributos que uno desee) -> ESTE ES PARA CREAR TABLAS
CREATE INDEX "NOMBRE DEL INDICE" on table(columna`s); -> ESTE ES PARA CREAR INDICES
CREATE VIEW "NOMBRE DE LA VISTA" consulta;
CREATE DATABASE "NOMBRE DE LA BASE DE DATSO" -> ESTE SIRVE PARA CREAR LAS BASES DE DATOS
```
Estan son para modificar:
```SQL
ALTER TABLE "NOMBRE DELA TABLA"(ADD NUEVO CAMPO NUMBRE (3)); 
```
Esta es para destruir tablas:
```SQL
DROP TABLE "NOMBRE DE LA TABLA"
```
## DML
### Significado
El signifiacado es el lenguaje de Manipulacion de datos
### Para que se utilizan 
es para manipular datos almacenados en una data base, se puede instertar datos, actualizar, eliminar he consultar
### Instrucciones
```SQL
INSERT INTO "NOMBRE DE LA TABLA" (COLUMNA, COLUMNA2 ...) VALUES(VALOR1, CVALOR 2) -> ESTE ES PARA LA INSERTAR NUEVOS DATOS EN UNA TABLA
UPDATE "NOMBRE DE LA TABLA ORIGIN" SET COLUMNA = NUEVODATOS, COLUMNA2 = NUEVOSDATOS, WHERE "CONDICION DEL DATO PUEDE COLOCAR EL ID"; -> ESTE ES PARA MODIFICAR LOS DATOS EXISTENTES EN UNA TABLA
DELETE "NOMBRE DE LA TABLA" WHERE "ID DE DATO" -> ESTE ES PARA ELIMINAR LOS DATOS
SELECT columna, columna2, FROM "TABLA A CONSULTAR" -> ES PARA HACER CONSULTAS DE LOS DATOS QUEDESEAMOS SABER
```
## DCL
### Significado
el significado es de Lenguaje de control de datos 
### Para que se utilizan 
Es mas utilizado para el contrl de acceso donde podemos manipular los roles de cada usuarios crear el usuaior y eliminarlo, asignamos privilegios he incluso los podemos revocar
### Instrucciones
```SQL
GRANT -> ASIGNAR ROLES
REVOKE -> RETIRAR ROLES
CREATE USER -> CREAR USUARIO
DROP USER -> ELIMINAR USUARIO
CREATE ROLE -> CREAR ROL
DROP ROLE -> ELIMINAR ROL
ALTER USER -> MODIFICAR PROPIEDAD DEL USUARIO
ALTER ROLE -> MODIFICAR PROPIEDAD DEL ROL
```
## SEGUNDA SERIE
explique las siguintes instrucciones para reliazr xonsultas y brinde un ejemplo

### Having
se utiliza para filtrar los resultados de una consualta agrupada va despues de group by y antes de select, este solo aplica a los grupos de cumplen las condiciones especificas

por ejemplo:

ID_venatas|Fecha_ventas|Cantidad_vendida
---|---|---
1|2023-05-12|400
2|2023-06-23|500
3|2023-08-12|600
4|2023-10-24|700

```SQL
SELECT fecha_venta, SUM(cantidad_vendida) AS total_vendido FROM ventas GROUP BY fecha_venta HAVING total_vendido > 500;
```
aqui estamos dicienso que vamos hacer una consulta donde tendremos las fecha de la venta y el total vendido como una columna nueva y que esta sonulta sea mauyor a 500

fecha_venta|total_vendido
---|---
2023-06-23|500
2023-08-12|600
2023-10-24|700
### Group by
este se utiliza para agrupar los resultados, en funcion de los valores de una o varios columnas se utiliza despues de FROM y antes de SELECT, estte se utiliza funciones agregando en el SELET que pude ser como SUM AVG COUNT

Ejemplo:

ID_venatas|Fecha_ventas|Cantidad_vendida
---|---|---
1|2023-05-12|400
2|2023-06-23|500
3|2023-08-12|600
4|2023-10-24|700

```SQL
SELECT fecha_venta, SUM(cantidad_vendida) AS total_vendido
FROM ventas
GROUP BY fecha_venta;

```

Fecha_ventas|Total_vendido
---|---
2023-05-12|400
2023-06-23|500
2023-08-12|600
2023-10-24|700

aqui vemos que agrupamos los datos por fecha de venta aqui al devolvenos el SELECCT nos data el fecha de vneta y el total vendido para ese grupo 
### Count
este se utilizar oara contar el numeor de filas que complen una determinada condicion este se usa depsues de SELECT y antes de un FROM aqui se puede usar el * o el nombre de la columna 
por ejemplo:

|ID de empleado|Nombre|Apellido|
|---|---|---|
|1|Juan|Pérez|
|2|María|García|
|3|Pedro|Sánchez|

```SQL
SELECT COUNT(*)
FROM empleados;
```

al momneto de hacer la consulta vamos a poder visualizar que nos devolvera 3 asi como podemos ver en la tabal que hacer 3 datos:
### Max
Este consulta de max se utiliza para devolver el macimo de una columna se utiliza entre SELCT y el FROM

por ejemplo:

ID_venatas|Fecha_ventas|Cantidad_vendida
---|---|---
1|2023-05-12|400
2|2023-06-23|500
3|2023-08-12|600
4|2023-10-24|700

```SQL
SELECT MAX(cantidad_vendida)
FROM ventas;

```
al momento de ejecutar estamos visualizando que nos de la cantidad maxima de esta colunna de venats que esta va ser 700
### Distinict
el Distinict es para devolver lso valores distintos de una columna o el conjuntto de columnas si se usa el distinict asi solo asi nos devolvera todas las columnas especificadas en el SELECT pero si decalramos la columnna que quremos nos devolvera ese columna

por ejemplo:

|ID de empleado|Nombre|Apellido|
|---|---|---|
|1|Raul|Merida|
|2|Magdalena|García|
|3|Lilian|Gomez|
|4|Raul|Ramos|

```SQL
SELECT DISTINCT nombre
FROM empleados;
```

en este ejemplo vamos a consultar que nos devuleva solo los nombre dentrol de la columna tabla en este caso solo nos devolvera 3 nombres porque vemos que juan esta repetido

## Tercera serie

### Modelo entidad/relacion
![](https://i.imgur.com/yp0ZkFQ.png)

### Query para creacion de tablas y data base

![](https://i.imgur.com/ageQxg9.png)
``` SQL
CREATE DATABASE UNG_Estudiantes
```

```SQL
CREATE TABLE Tab_Area_conocimiento (
    id_area INT NOT NULL AUTO_INCREMENT,
    nombre_area VARCHAR(255) NOT NULL,
    PRIMARY KEY (id_area)
);

CREATE TABLE Tab_Departamentos (
    id_departamento INT NOT NULL AUTO_INCREMENT,
    nombre_departamento VARCHAR(255) NOT NULL,
    id_area INT NOT NULL,
    PRIMARY KEY (id_departamento),
    FOREIGN KEY (id_area) REFERENCES Tab_Area_conocimiento (id_area)
);

CREATE TABLE Tab_Titulacion (
    id_titulacion INT NOT NULL AUTO_INCREMENT,
    nombre_titulacion VARCHAR(255) NOT NULL,
    nombre_departamento VARCHAR(255) NOT NULL,
    PRIMARY KEY (id_titulacion),
    FOREIGN KEY (nombre_departamento) REFERENCES Tab_Departamentos (nombre_departamento)
);

CREATE TABLE Tab_Profesores (
    id_profesores INT NOT NULL AUTO_INCREMENT,
    nombre_profesores VARCHAR(255) NOT NULL,
    id_area INT NOT NULL,
    PRIMARY KEY (id_profesores),
    FOREIGN KEY (id_area) REFERENCES Tab_Area_conocimiento (id_area)
);

CREATE TABLE Tab_Asignatura (
    id_asignatura INT NOT NULL AUTO_INCREMENT,
    nombre_asignatura VARCHAR(255) NOT NULL,
    id_titulacion INT NOT NULL,
    id_area INT NOT NULL,
    PRIMARY KEY (id_asignatura),
    FOREIGN KEY (id_titulacion) REFERENCES Tab_Titulacion (id_titulacion),
    FOREIGN KEY (id_area) REFERENCES Tab_Area_conocimiento (id_area)
);

CREATE TABLE Tab_Clases_Impartidas (
    id_clasesImprar INT NOT NULL AUTO_INCREMENT,
    id_profesor INT NOT NULL,
    id_asignatura INT NOT NULL,
    PRIMARY KEY (id_clasesImprar),
    FOREIGN KEY (id_profesor) REFERENCES Tab_Profesores (id_profesores),
    FOREIGN KEY (id_asignatura) REFERENCES Tab_Asignatura (id_asignatura)
);
```

![](https://i.imgur.com/AWPqutE.png)


drive:
https://drive.google.com/drive/folders/1Ras15IgMmedSGJceT8f2BR340mvAFxTv?usp=sharing
## Para crear una base de datos
```SQL
CREATE DATABASE TiendaMaria
```
![](https://i.imgur.com/ALHcxfk.png)
## Para crear una tabla de base de datos 
donde tambien pueda logear una relacion o bien que tenga una llave forenea y primaria
```SQL 
CREATE TABLE compra (
  Id_compra INT NOT NULL IDENTITY(1,1) PRIMARY KEY,
  Ventas INT NOT NULL,
  Fecha DATE NOT NULL
);

CREATE TABLE cliente (
  Id_cli INT NOT NULL IDENTITY(1,1) PRIMARY KEY,
  Nombre VARCHAR(50) NOT NULL,
  Apellido VARCHAR(50) NOT NULL,
  Direccion VARCHAR(255) NOT NULL,
  Telefono INT NOT NULL,
  Id_compra int not null,
  CONSTRAINT fk_grupo FOREIGN KEY (Id_compra)
  REFERENCES compra (Id_compra)
);
```
se pone como primero la que que se hagara de foranea y despues la primaria


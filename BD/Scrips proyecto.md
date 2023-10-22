## Base de datos
```SQL
CREATE DATABASE UMG_bibliote
```
![](https://i.imgur.com/Nkggn8y.png)
## Tablas
```SQL
CREATE TABLE Biblioteca(
Id_biblioteca INT PRIMARY KEY IDENTITY(1,1),
Nombre VARCHAR(50) NOT NULL,
Ubicacion VARCHAR(50) NOT NULL,
Encargado VARCHAR(50) NOT NULL,
Horario VARCHAR(50) NOT NULL,
);

CREATE TABLE Estudiante(
Id_estudiante INT PRIMARY KEY IDENTITY(1,1),
Nombre VARCHAR(50) NOT NULL,
Apellido VARCHAR(50) NOT NULL,
Carrera VARCHAR(50) NOT NULL
);

CREATE TABLE Ejemplar(
Id_ejemplar INT PRIMARY KEY IDENTITY(1,1),
Titulo VARCHAR(50) NOT NULL,
Autor VARCHAR(50) NOT NULL,
Año INT NOT NULL,
Editorial VARCHAR(50) NOT NULL,
Tipo VARCHAR(50) NOT NULL,
Existencia INT NOT NULL,
Id_biblioteca INT NOT NULL,
FOREIGN KEY (Id_biblioteca) REFERENCES Biblioteca(Id_biblioteca)
);

CREATE TABLE Prestamo(
Id_prestamo INT PRIMARY KEY IDENTITY(1,1),
Fecha_prestamo DATE NOT NULL,
Fecha_devovulucion DATE NOT NULL,
Estado VARCHAR(50) NOT NULL,
Id_estudiante INT NOT NULL,
FOREIGN KEY (Id_estudiante) REFERENCES Estudiante(Id_estudiante),
Id_ejemplar INT NOT NULL,
FOREIGN KEY (Id_ejemplar) REFERENCES Ejemplar(Id_ejemplar)
);

CREATE TABLE Reservar(
Id_reservar INT PRIMARY KEY IDENTITY(1,1),
Fecha_reserva DATE NOT NULL,
Fecha_vencimiento DATE NOT NULL,
Estado VARCHAR(50) NOT NULL,
Id_estudiante INT NOT NULL,
FOREIGN KEY (Id_estudiante) REFERENCES Estudiante(Id_estudiante),
Id_ejemplar INT NOT NULL,
FOREIGN KEY (Id_ejemplar) REFERENCES Ejemplar(Id_ejemplar)
);
```
## DIagrama relacion
![](https://i.imgur.com/i3NMIfN.png)
## Tigres
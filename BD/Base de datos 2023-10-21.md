Jose Raul Botzoc Merida
scrip de llenado de tablas 

# creacion de base datos
```SQL 
CREATE DATABASE Base_de_datos_clase
```

# Creacion de tablas
```SQL
-- Tabla de Clientes
CREATE TABLE Clientes (
    NIT VARCHAR(15) PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    calle VARCHAR(100),
    numero INT,
    comuna VARCHAR(100),
    ciudad VARCHAR(100)
);

-- Tabla de provedor
CREATE TABLE  Proveedores(
    NIT VARCHAR(15) PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    calle VARCHAR(100),
    numero INT,
    comuna VARCHAR(100),
    ciudad VARCHAR(100)
);

-- Tabla de Teléfonos de Clientes
CREATE TABLE TelefonosClientes (
    idTelefono INT IDENTITY(1,1) PRIMARY KEY,
    NIT VARCHAR(15),
    telefono VARCHAR(15) NOT NULL,
    FOREIGN KEY (NIT) REFERENCES Clientes(NIT) ON DELETE CASCADE ON UPDATE CASCADE
);

-- Tabla de Categorías
CREATE TABLE Categorias (
    idCategoria INT IDENTITY(1,1) PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    descripcion TEXT
);

-- Tabla de Productos
CREATE TABLE Productos (
    idProducto INT IDENTITY(1,1) PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    precioActual DECIMAL(10,2),
    stock INT NOT NULL,
    NITProveedor VARCHAR(15),
    idCategoria INT,
    FOREIGN KEY (NITProveedor) REFERENCES Proveedores(NIT) ON DELETE CASCADE ON UPDATE CASCADE,
    FOREIGN KEY (idCategoria) REFERENCES Categorias(idCategoria) ON DELETE CASCADE ON UPDATE CASCADE
);

-- Tabla de Ventas
CREATE TABLE Ventas (
    idVenta INT IDENTITY(1,1) PRIMARY KEY,
    fecha DATE,
    NITCliente VARCHAR(15),
    descuento DECIMAL(10,2),
    montoFinal DECIMAL(10,2),
    FOREIGN KEY (NITCliente) REFERENCES Clientes(NIT) ON DELETE CASCADE ON UPDATE CASCADE
);

-- Tabla de Detalles de Ventas
CREATE TABLE DetalleVentas (
    idDetalle INT IDENTITY(1,1) PRIMARY KEY,
    idVenta INT,
    idProducto INT,
    precioVenta DECIMAL(10,2),
    cantidad INT,
    montoProducto DECIMAL(10,2),
    FOREIGN KEY (idVenta) REFERENCES Ventas(idVenta) ON DELETE CASCADE ON UPDATE CASCADE,
    FOREIGN KEY (idProducto) REFERENCES Productos(idProducto) ON DELETE CASCADE ON UPDATE CASCADE
);

```

![](https://i.imgur.com/JR6MWvQ.png)

---
# scrip para llenar 

```SQL
INSERT INTO Proveedores (NIT, nombre, calle, numero, comuna, ciudad)
VALUES
  ('001', 'ProveedorA', 'Calle A', 1, 'Comuna 1', 'Ciudad 1'),
  ('002', 'ProveedorB', 'Calle B', 32, 'Comuna 2', 'Ciudad 2'),
  ('003', 'ProveedorC', 'Calle C', 21, 'Comuna 3', 'Ciudad 3'),
  ('004', 'ProveedorC', 'Calle d', 43, 'Comuna 3', 'Ciudad mexico'),
  ('005', 'ProveedorC', 'Calle e', 7, 'Comuna 3', 'Ciudad asd'),
  ('006', 'ProveedorC', 'Calle f', 38, 'Comuna 3', 'Ciudad gt'),
  ('007', 'ProveedorC', 'Calle g', 53, 'Comuna 3', 'Ciudad chimaltenago'),
  ('008', 'ProveedorC', 'Calle h', 3, 'Comuna 3', 'Ciudad belice'),
  ('009', 'ProveedorC', 'Calle i', 5, 'Comuna 3', 'Ciudad le salvador'),
  ('010', 'ProveedorC', 'Calle j', 33, 'Comuna 3', 'Ciudad alaska'),
  ('011', 'ProveedorC', 'Calle k', 12, 'Comuna 3', 'Ciudad spaña'),
  ('012', 'ProveedorC', 'Calle l', 23, 'Comuna 3', 'Ciudad chiguagua'),
  ('013', 'ProveedorC', 'Calle m', 53, 'Comuna 3', 'Ciudad mixca'),
  ('014', 'ProveedorC', 'Calle n', 92, 'Comuna 3', 'Ciudad candelaria'),
  ('015', 'ProveedorC', 'Calle o', 12, 'Comuna 3', 'Ciudad peru'),
  ('016', 'ProveedorC', 'Calle p', 21, 'Comuna 3', 'Ciudad peronia'),
  ('017', 'ProveedorC', 'Calle q', 10, 'Comuna 3', 'Ciudad jalsico'),
  ('018', 'ProveedorC', 'Calle r', 12, 'Comuna 3', 'Ciudad perez'),
  ('019', 'ProveedorC', 'Calle s', 89, 'Comuna 3', 'Ciudad mocerat'),
  ('020', 'ProveedorC', 'Calle t', 09, 'Comuna 3', 'Ciudad tierra nueva'),
  ('021', 'ProveedorC', 'Calle u', 1, 'Comuna 3', 'Ciudad villa nueva'),
  ('022', 'ProveedorC', 'Calle w', 27, 'Comuna 3', 'Ciudad argentina'),
  ('023', 'ProveedorC', 'Calle x', 17, 'Comuna 3', 'Ciudad bracilia'),
  ('024', 'ProveedorZ', 'Calle y', 25, 'Comuna Z', 'Ciudad ms'),
  ('025', 'ProveedorC', 'Calle z', 12, 'Comuna 3', 'Ciudad pemprona');
```

# drive
https://drive.google.com/drive/folders/1IzYgruIVEvAh45SbPoi0Jk-DyCYvy5aE?usp=sharing
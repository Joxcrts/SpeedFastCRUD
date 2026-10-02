# SpeedFast CRUD - Semana 8

Aplicacion de escritorio en Java Swing para gestionar repartidores, pedidos y entregas de SpeedFast.
Usa JDBC con MySQL y el patron DAO (paquetes modelo, dao y vista).

## Como ejecutar

1. Crear la base de datos en MySQL con el script de abajo.
2. Cambiar usuario y clave en `src/dao/ConexionDB.java` si es necesario.
3. El conector MySQL esta en la carpeta `lib`.
4. Ejecutar `vista/VentanaPrincipal.java`.

## Script SQL

```sql
CREATE DATABASE IF NOT EXISTS speedfast_db;
USE speedfast_db;

CREATE TABLE repartidores (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE pedidos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    direccion VARCHAR(100) NOT NULL,
    tipo ENUM('COMIDA','ENCOMIENDA','EXPRESS'),
    estado ENUM('PENDIENTE','EN_REPARTO','ENTREGADO')
);

CREATE TABLE entregas (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_pedido INT,
    id_repartidor INT,
    fecha DATE,
    hora TIME,
    FOREIGN KEY (id_pedido) REFERENCES pedidos(id),
    FOREIGN KEY (id_repartidor) REFERENCES repartidores(id)
);
```

Autor: Joxan Cortes

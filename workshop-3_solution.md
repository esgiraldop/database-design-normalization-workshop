**Ejercicio 1: Base de datos de una biblioteca**

Punto de partida

| ID_Libro | Titulo               | Autor1                | Autor2         | Autor3     | Genero1        | Genero2 |
|----------|----------------------|-----------------------|----------------|------------|----------------|---------|
| 1        | Don Quijote          | Miguel de Cervantes   | NULL           | NULL       | Novela         | Clásico |
| 2        | Cien Años de Soledad | Gabriel García Márquez| NULL           | NULL       | Realismo Mágico| Novela  |
| 3        | La Odisea            | Homero                | NULL           | NULL       | Épica          | Clásico |
| 4        | Good Omens           | Neil Gaiman           | Terry Pratchett| NULL       | Fantasía       | Comedia |


Normalización: Primera forma normal

| ID_libro | Titulo               | Autor                  | Genero          |
| -------- | -------------------- | ---------------------- | --------------- |
| 1        | Don Quijote          | Miguel de Cervantes    | Novela          |
| 1        | Don Quijote          | Miguel de Cervantes    | Clásico         |
| 2        | Cien Años de Soledad | Gabriel García Márquez | Realismo Mágico |
| 2        | Cien Años de Soledad | Gabriel García Márquez | Novela          |
| 3        | La Odisea            | Homero                 | Épica           |
| 3        | La Odisea            | Homero                 | Clásico         |
| 4        | Good Omens           | Neil Gaiman            | Fantasía        |
| 4        | Good Omens           | Neil Gaiman            | Comedia         |
| 4        | Good Omens           | Terry Pratchett        | Fantasía        |
| 4        | Good Omens           | Terry Pratchett        | Comedia         |



**Ejercicio 2: Base de datos de una tienda en línea**

Punto de partida:
| ID_Pedido | ID_Producto | Cliente          | Dirección             | Producto      | Precio |
|-----------|-------------|------------------|-----------------------|---------------|--------|
| 1         | 101         | Juan Pérez       | Calle 123, Ciudad A   | Camiseta      | 20.00  |
| 1         | 102         | Juan Pérez       | Calle 123, Ciudad A   | Pantalones    | 25.00  |
| 2         | 103         | Ana Gómez        | Avenida 456, Ciudad B | Zapatos       | 50.00  |
| 2         | 101         | Ana Gómez        | Avenida 456, Ciudad B | Camiseta      | 20.00  |

Normalización: Segunda forma normal

Pedidos:
| ID_pedido | ID_producto | ID_cliente |
| --------- | ----------- | ---------- |
| 1         | 101         | 1          |
| 1         | 102         | 1          |
| 2         | 103         | 2          |
| 2         | 101         | 2          |

Productos
| ID_producto | Producto   | Precio |
| ----------- | ---------- | ------ |
| 101         | Camiseta   | 20     |
| 102         | Pantalones | 25     |
| 103         | Zapatos    | 50     |

Clientes
| ID_cliente | Cliente    | Dirección             |
| ---------- | ---------- | --------------------- |
| 1          | Juan Pérez | Calle 123, Ciudad A   |
| 2          | Ana Gómex  | Avenida 456, Ciudad B |


**Ejercicio 3: Base de datos de un hospitala**

Punto de partida:

Consultas:
| ID_Consulta | ID_Paciente | Paciente         | Doctor       | Especialidad |
|-------------|-------------|------------------|--------------|--------------|
| 1           | 100         | Juan Pérez       | Dr. Smith    | Cardiología  |
| 2           | 101         | Ana Gómez        | Dr. Johnson  | Neurología   |
| 3           | 100         | Juan Pérez       | Dr. Smith    | Cardiología  |
| 4           | 102         | Maria López      | Dr. Lee      | Pediatría    |


Normalización: Tercera forma normal

Consultas
| ID_consulta | ID_paciente | ID_doctor |
| ----------- | ----------- | --------- |
| 1           | 100         | 1         |
| 2           | 101         | 2         |
| 3           | 100         | 1         |
| 4           | 102         | 3         |

Pacientes
| ID_paciente | Paciente    |
| ----------- | ----------- |
| 100         | Juan Pérez  |
| 101         | Ana Gómez   |
| 100         | Juan Pérez  |
| 102         | Maria López |

Doctores
| ID_doctor | Doctor      | Especialidad |
| --------- | ----------- | ------------ |
| 1         | Dr. Smith   | Cardiología  |
| 2         | Dr. Johnson | Neurología   |
| 3         | Dr. Lee     | Pediatría    |


**Ejercicio 4: Base de datos de proyectos de investigación**

Punto de partida:

Proyectos:
| ID_Proyecto | Nombre_Proyecto    | ID_Profesor | Nombre_Profesor |
|-------------|--------------------|-------------|------------------|
| 1           | IA Avanzada        | 101         | Dr. Smith        |
| 2           | Robótica           | 102         | Dr. Johnson      |
| 3           | IA Aplicada        | 101         | Dr. Smith        |
| 4           | Redes de Computo   | 103         | Dr. Lee          |


Normalización: Forma Normal de Boyce-Codd (BCNF)

Proyectos:
| ID_proyecto | Nombre_Proyecto  |
| ----------- | ---------------- |
| 1           | IA Avanzada      |
| 2           | Robótica         |
| 3           | IA Aplicada      |
| 4           | Redes de Computo |

Profesor:
| ID_profesor | Nombre_Profesor |
| ----------- | --------------- |
| 101         | Dr. Smith       |
| 102         | Dr. Johnson     |
| 103         | Dr. Lee         |

Proyecto_profesor
| ID_proyecto | ID_profesor |
| ----------- | ----------- |
| 1           | 101         |
| 2           | 102         |
| 3           | 101         |
| 4           | 103         |


**Ejercicio 5: Base de datos de proyectos de investigación**

Punto de partida:

Empleado_Habilidades:
| ID_Empleado | Nombre_Empleado | Habilidad                |
|-------------|-----------------|--------------------------|
| 1           | Juan Pérez      | Programación             |
| 1           | Juan Pérez      | Diseño de Bases de Datos |
| 2           | Ana Gómez       | Programación             |
| 2           | Ana Gómez       | Análisis de Datos        |

Normalización: Cuarta forma normal

Empleados
| ID_Empleado | Nombre_Empleado |
| ----------- | --------------- |
| 1           | Juan Pérez      |
| 2           | Ana Gómez       |

Habilidades:
| ID_Habilidad | Habilidad                |
| ------------ | ------------------------ |
| 1            | Programación             |
| 2            | Diseño de Bases de Datos |
| 3            | Análisis de datos        |

Habilidad_empleado
| ID_Habilidad | ID_Empleado |
| ------------ | ----------- |
| 1            | 1           |
| 1            | 2           |
| 2            | 1           |
| 2            | 3           |


**Ejercicio 6: Base de datos de contratos**

Contratos:
| ID_Proyecto | ID_Empleado | ID_Proveedor |
|-------------|-------------|--------------|
| 1           | 1           | 1001         |
| 1           | 2           | 1002         |
| 2           | 1           | 1001         |

Normalización: Quinta forma normal

Proyecto_empleado
| ID_Proyecto | ID_Empleado |
| ----------- | ----------- |
| 1           | 1           |
| 1           | 2           |
| 2           | 1           |

Proyecto_proveedor
| ID_Proyecto | ID_Proveedor |
| ----------- | ------------ |
| 1           | 1001         |
| 1           | 1002         |
| 2           | 1001         |

Empleado_proveedor
| ID_Empleado | ID_Proveedor |
| ----------- | ------------ |
| 1           | 1001         |
| 2           | 1002         |


**Ejercicio 7: Base de datos de ventas**
Punto de partida:

Ventas:
| ID_Venta | Cliente        | Producto     | Precio | Fecha       |
|----------|----------------|--------------|--------|-------------|
| 1        | Juan Pérez     | Camiseta     | 20.00  | 2023-01-01  |
| 2        | Ana Gómez      | Pantalones   | 25.00  | 2023-01-02  |
| 3        | Juan Pérez     | Camiseta     | 20.00  | 2023-01-03  |

Eliminando duplicados

Clientes:
| ID_Cliente | Cliente    |
| ---------- | ---------- |
| 1          | Juan Pérez |
| 2          | Ana Gómez  |

Productos:
| ID_Producto | Producto   | Precio |
| ----------- | ---------- | ------ |
| 1           | Camiseta   | 20     |
| 2           | Pantalones | 25     |

Ventas:
| ID_Venta | ID_Cliente | ID_Producto | Fecha   |
| -------- | ---------- | ----------- | ------- |
| 1        | 1          | 1           | 1/01/23 |
| 2        | 2          | 2           | 2/01/23 |
| 3        | 1          | 1           | 3/01/23 |

**Ejercicio 8: Base de datos de ventas**

Punto de partida:

Inventarios:
| ID_Inventario | Producto         | Cantidad_Ubicaciones           |
|---------------|------------------|--------------------------------|
| 1             | Tornillos        | A1:100, B2:200                 |
| 2             | Clavos           | A3:150, B4:100                 |

Aplicando atomicidad:

Inventario:
| ID_Inventario | Producto  |
| ------------- | --------- |
| 1             | Tornillos |
| 2             | Clavos    |

Detalle_inventario
| ID_Ubicacion | Ubicación | ID_inventario | Cantidad |
| ------------ | --------- | ------------- | -------- |
| 1            | A1        | 1             | 100      |
| 2            | A3        | 2             | 150      |
| 3            | B2        | 1             | 200      |
| 4            | B4        | 2             | 100      |
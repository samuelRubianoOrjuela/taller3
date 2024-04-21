# Taller N°3 Bases de Datos.

1. Realice el proceso de normalizacion de base de datos que permita cumplir hasta la 4fn.

    ```sql
        +-------------------+--------------+------+-----+---------+-------+
        | gama_producto                                                   |
        +-------------------+--------------+------+-----+---------+-------+
        | Field             | Type         | Null | Key | Default | Extra |
        +-------------------+--------------+------+-----+---------+-------+
        | gama              | varchar(50)  | NO   | PRI | NULL    |       |
        | descripcion_texto | text         | YES  |     | NULL    |       |
        | descripcion_html  | text         | YES  |     | NULL    |       |
        | imagen            | varchar(256) | YES  |     | NULL    |       |
        +-------------------+--------------+------+-----+---------+-------+

        +-------------------+---------------+------+-----+---------+-------+
        | producto                                                         |
        +-------------------+---------------+------+-----+---------+-------+
        | Field             | Type          | Null | Key | Default | Extra |
        +-------------------+---------------+------+-----+---------+-------+
        | id_producto       | varchar(15)   | NO   | PRI | NULL    |       |
        | nombre            | varchar(70)   | YES  |     | NULL    |       |
        | gama              | varchar(50)   | YES  |     | NULL    |       |
        | dimensiones       | varchar(25)   | YES  |     | NULL    |       |
        | id_proveedor      | varchar(50)   | YES  | MUL | NULL    |       |
        | descripcion       | text          | YES  |     | NULL    |       |
        | cantidad_en_stock | smallint      | YES  |     | NULL    |       |
        | precio_venta      | decimal(15,2) | YES  |     | NULL    |       |
        | precio_proveedor  | decimal(15,2) | YES  |     | NULL    |       |
        +-------------------+---------------+------+-----+---------+-------+

        +---------------+---------------+------+-----+---------+-------+
        | detalle_pedido                                               |
        +---------------+---------------+------+-----+---------+-------+
        | Field         | Type          | Null | Key | Default | Extra |
        +---------------+---------------+------+-----+---------+-------+
        | id_pedido     | int           | NO   | PRI | NULL    |       |
        | id_producto   | varchar(15)   | NO   | PRI | NULL    |       |
        | cantidad      | int           | YES  |     | NULL    |       |
        | precio_unidad | decimal(15,2) | YES  |     | NULL    |       |
        | numero_linea  | smallint      | YES  |     | NULL    |       |
        +---------------+---------------+------+-----+---------+-------+

        +----------------+-------------+------+-----+---------+-------+
        | pedido                                                      |
        +----------------+-------------+------+-----+---------+-------+
        | Field          | Type        | Null | Key | Default | Extra |
        +----------------+-------------+------+-----+---------+-------+
        | id_pedido      | int         | NO   | PRI | NULL    |       |
        | fecha_pedido   | date        | YES  |     | NULL    |       |
        | fecha_esperada | date        | YES  |     | NULL    |       |
        | fecha_entrega  | date        | YES  |     | NULL    |       |
        | estado         | varchar(15) | YES  |     | NULL    |       |
        | comentarios    | text        | YES  |     | NULL    |       |
        | id_cliente     | int         | YES  | MUL | NULL    |       |
        +----------------+-------------+------+-----+---------+-------+

        +------------------------+---------------+------+-----+---------+-------+
        | cliente                                                               |
        +------------------------+---------------+------+-----+---------+-------+
        | Field                  | Type          | Null | Key | Default | Extra |
        +------------------------+---------------+------+-----+---------+-------+
        | id_cliente             | int           | NO   | PRI | NULL    |       |
        | nombre_cliente         | varchar(50)   | YES  |     | NULL    |       |
        | nombre_contacto        | varchar(30)   | YES  |     | NULL    |       |
        | apellido_contacto      | varchar(30)   | YES  |     | NULL    |       |
        | telefono               | varchar(15)   | YES  |     | NULL    |       |
        | fax                    | varchar(15)   | YES  |     | NULL    |       |
        | id_direccion           | int           | YES  | MUL | NULL    |       |
        | id_ciudad              | int           | YES  | MUL | NULL    |       |
        | id_empleado_rep_ventas | int           | YES  | MUL | NULL    |       |
        | limite_credito         | decimal(15,2) | YES  |     | NULL    |       |
        +------------------------+---------------+------+-----+---------+-------+

        +------------------+---------------+------+-----+---------+-------+
        | pago                                                            |
        +------------------+---------------+------+-----+---------+-------+
        | Field            | Type          | Null | Key | Default | Extra |
        +------------------+---------------+------+-----+---------+-------+
        | id_transaccion   | varchar(50)   | NO   | PRI | NULL    |       |
        | id_cliente       | int           | YES  | MUL | NULL    |       |
        | id_forma_de_pago | int           | YES  | MUL | NULL    |       |
        | fecha_pago       | date          | YES  |     | NULL    |       |
        | total            | decimal(15,2) | YES  |     | NULL    |       |
        +------------------+---------------+------+-----+---------+-------+

        +----------------------+-------------+------+-----+---------+-------+
        | forma_de_pago|
        +----------------------+-------------+------+-----+---------+-------+
        | Field                | Type        | Null | Key | Default | Extra |
        +----------------------+-------------+------+-----+---------+-------+
        | id_forma_de_pago     | int         | NO   | PRI | NULL    |       |
        | nombre_forma_de_pago | varchar(50) | YES  |     | NULL    |       |
        +----------------------+-------------+------+-----+---------+-------+

        +-------------+--------------+------+-----+---------+-------+
        | empleado                                                  |
        +-------------+--------------+------+-----+---------+-------+
        | Field       | Type         | Null | Key | Default | Extra |
        +-------------+--------------+------+-----+---------+-------+
        | id_empleado | int          | NO   | PRI | NULL    |       |
        | nombre      | varchar(50)  | YES  |     | NULL    |       |
        | apellido1   | varchar(50)  | YES  |     | NULL    |       |
        | apellido2   | varchar(50)  | YES  |     | NULL    |       |
        | extension   | varchar(10)  | YES  |     | NULL    |       |
        | email       | varchar(100) | YES  |     | NULL    |       |
        | id_oficina  | varchar(10)  | YES  | MUL | NULL    |       |
        | id_jefe     | int          | YES  | MUL | NULL    |       |
        | puesto      | varchar(50)  | YES  |     | NULL    |       |
        +-------------+--------------+------+-----+---------+-------+

        +--------------+-------------+------+-----+---------+-------+
        | oficina                                                   |
        +--------------+-------------+------+-----+---------+-------+
        | Field        | Type        | Null | Key | Default | Extra |
        +--------------+-------------+------+-----+---------+-------+
        | id_oficina   | varchar(10) | NO   | PRI | NULL    |       |
        | id_ciudad    | int         | YES  | MUL | NULL    |       |
        | telefono     | varchar(20) | YES  |     | NULL    |       |
        | id_direccion | int         | YES  | MUL | NULL    |       |
        +--------------+-------------+------+-----+---------+-------+

        +---------------+-------------+------+-----+---------+-------+
        | ciudad                                                     |
        +---------------+-------------+------+-----+---------+-------+
        | Field         | Type        | Null | Key | Default | Extra |
        +---------------+-------------+------+-----+---------+-------+
        | id_ciudad     | int         | NO   | PRI | NULL    |       |
        | nombre_ciudad | varchar(20) | YES  |     | NULL    |       |
        | codigo_postal | varchar(10) | YES  |     | NULL    |       |
        | id_region     | int         | YES  | MUL | NULL    |       |
        +---------------+-------------+------+-----+---------+-------+

        +---------------+-------------+------+-----+---------+-------+
        | region                                                     |
        +---------------+-------------+------+-----+---------+-------+
        | Field         | Type        | Null | Key | Default | Extra |
        +---------------+-------------+------+-----+---------+-------+
        | id_region     | int         | NO   | PRI | NULL    |       |
        | nombre_region | varchar(20) | YES  |     | NULL    |       |
        | id_pais       | int         | YES  | MUL | NULL    |       |
        +---------------+-------------+------+-----+---------+-------+

        +-------------+-------------+------+-----+---------+-------+
        | pais                                                     |
        +-------------+-------------+------+-----+---------+-------+
        | Field       | Type        | Null | Key | Default | Extra |
        +-------------+-------------+------+-----+---------+-------+
        | id_pais     | int         | NO   | PRI | NULL    |       |
        | nombre_pais | varchar(20) | YES  |     | NULL    |       |
        +-------------+-------------+------+-----+---------+-------+
    ```
    ---
### Consultas sobre una tabla
---

1. Devuelve un listado con el código de oficina y la ciudad donde hay oficinas.
    ```sql
    SELECT o.id_oficina, c.nombre_ciudad
    FROM oficina o
    JOIN ciudad c ON o.id_ciudad = c.id_ciudad;
    
    +------------+---------------+
    | id_oficina | nombre_ciudad |
    +------------+---------------+
    | OF001      | Los Angeles   |
    | OF002      | San Francisco |
    | OF003      | New York      |
    | OF004      | Buffalo       |
    | OF005      | Grenoble      |
    | OF006      | Lyon          |
    | OF007      | Tours         |
    | OF008      | Orléans       |
    | OF009      | Sevilla       |
    | OF010      | Málaga        |
    | OF011      | Barcelona     |
    | OF012      | Girona        |
    | OF013      | Bogotá        |
    | OF014      | Medellín      |
    +------------+---------------+
    ```
    ---
2. Devuelve un listado con la ciudad y el teléfono de las oficinas de España.
    ```sql
    SELECT c.nombre_ciudad, o.telefono
    FROM oficina o
    JOIN ciudad c ON o.id_ciudad = c.id_ciudad
    WHERE c.id_ciudad IN (
    	SELECT c.id_ciudad
    	FROM ciudad c, region r, pais p
    	WHERE c.id_region = r.id_region AND r.id_pais = p.id_pais AND p.id_pais = 3
    );
    
    +---------------+--------------+
    | nombre_ciudad | telefono     |
    +---------------+--------------+
    | Sevilla       | 999-000-1111 |
    | Madrid        | 222-333-4444 |
    | Barcelona     | 555-666-7777 |
    | Girona        | 888-999-0000 |
    +---------------+--------------+
    ```
    ---
3. Devuelve un listado con el nombre, apellidos y email de los empleados cuyo jefe tiene un código de jefe igual a 7.
    ```sql
    SELECT e.nombre, e.apellido1, e.apellido2, e.email
    FROM empleado e
    WHERE e.id_jefe = 7;
    
    +--------+-----------+-----------+-----------------------------+
    | nombre | apellido1 | apellido2 | email                       |
    +--------+-----------+-----------+-----------------------------+
    | Luisa  | Hernández | Sánchez   | luisa.hernandez@example.com |
    +--------+-----------+-----------+-----------------------------+
    ```
    ---
4. Devuelve el nombre del puesto, nombre, apellidos y email del jefe de la empresa.
    ```sql
    SELECT e.puesto, e.nombre, e.apellido1, e.apellido2, e.email
    FROM empleado e
    WHERE e.puesto = 'Gerente';
    
    +---------+--------+-----------+-----------+-------------------------+
    | puesto  | nombre | apellido1 | apellido2 | email                   |
    +---------+--------+-----------+-----------+-------------------------+
    | Gerente | Juan   | García    | López     | juan.garcia@example.com |
    +---------+--------+-----------+-----------+-------------------------+
    ```
    ---
5. Devuelve un listado con el nombre, apellidos y puesto de aquellos empleados que no sean representantes de ventas.
    ```sql
    SELECT e.puesto, e.nombre, e.apellido1, e.apellido2
    FROM empleado e
    WHERE e.puesto <> 'Representante de ventas';
    
    +-----------+--------+-----------+-----------+
    | puesto    | nombre | apellido1 | apellido2 |
    +-----------+--------+-----------+-----------+
    | Gerente   | Juan   | García    | López     |
    | Asistente | Ana    | López     | Gómez     |
    | Asistente | Carlos | Díaz      | Sánchez   |
    | Asistente | Laura  | Rodríguez | Fernández |
    | Asistente | Javier | Gómez     | Martínez  |
    | Asistente | Sofía  | Pérez     | González  |
    | Asistente | Diego  | Fernández | López     |
    | Asistente | Elena  | Sánchez   | Martínez  |
    | Asistente | Pablo  | González  | Hernández |
    | Asistente | Isabel | Gómez     | Rodríguez |
    | Asistente | Andrés | Martínez  | Díaz      |
    | Asistente | Luisa  | Hernández | Sánchez   |
    +-----------+--------+-----------+-----------+
    ```
    ---
6. Devuelve un listado con el nombre de los todos los clientes españoles.
    ```sql
    SELECT cl.nombre_cliente
    FROM cliente cl
    WHERE cl.id_ciudad IN (
    	SELECT c.id_ciudad
    	FROM ciudad c, region r, pais p
        	WHERE c.id_region = r.id_region AND r.id_pais = p.id_pais AND p.id_pais = 3
    );
    
    +----------------+
    | nombre_cliente |
    +----------------+
    | Cliente I      |
    | Cliente J      |
    +----------------+
    ```
    ---
7. Devuelve un listado con los distintos estados por los que puede pasar un pedido.
    ```sql
    SELECT estado
    FROM pedido;
    
    +--------------+
    | estado       |
    +--------------+
    | En proceso   |
    | Entregado    |
    | Entregado    |
    | No entregado |
    | En proceso   |
    +--------------+
    ```
    ---
8. Devuelve un listado con el código de cliente de aquellos clientes que realizaron algún pago en 2008. Tenga en cuenta que deberá eliminar aquellos códigos de cliente que aparezcan repetidos. Resuelva la consulta:
- Utilizando la función YEAR de MySQL.
    ```sql
    SELECT DISTINCT id_cliente
    FROM pago
    WHERE YEAR(fecha_pago) = 2008;
    
    +------------+
    | id_cliente |
    +------------+
    |          3 |
    +------------+
    ```
    ---
- Utilizando la función DATE_FORMAT de MySQL.
    ```sql
    SELECT DISTINCT id_cliente
    FROM pago
    WHERE DATE_FORMAT(fecha_pago, '%Y') = '2008';
    
    +------------+
    | id_cliente |
    +------------+
    |          3 |
    +------------+
    ```
    ---
- Sin utilizar ninguna de las funciones anteriores.
    ```sql
    SELECT DISTINCT id_cliente
    FROM pago
    WHERE fecha_pago BETWEEN '2008-01-01' AND '2008-12-31';
    
    +------------+
    | id_cliente |
    +------------+
    |          3 |
    +------------+
    ```
    ---
9. Devuelve un listado con el código de pedido, código de cliente, fecha esperada y fecha de entrega de los pedidos que no han sido entregados a tiempo.
    ```sql
    SELECT p.id_pedido, p.id_cliente, p.fecha_esperada, p.fecha_entrega
    FROM pedido p
    WHERE p.fecha_esperada = p.fecha_entrega;
    
    +-----------+------------+----------------+---------------+
    | id_pedido | id_cliente | fecha_esperada | fecha_entrega |
    +-----------+------------+----------------+---------------+
    |         3 |          3 | 2008-05-10     | 2008-05-10    |
    +-----------+------------+----------------+---------------+
    ```
    ---
10. Devuelve un listado con el código de pedido, código de cliente, fecha esperada y fecha de entrega de los pedidos cuya fecha de entrega ha sido al menos dos días antes de la fecha esperada.
- Utilizando la función ADDDATE de MySQL.
    ```sql
    SELECT p.id_pedido, p.id_cliente, p.fecha_esperada, p.fecha_entrega
    FROM pedido p
    WHERE p.fecha_entrega = ADDDATE(p.fecha_esperada, -2);
    
    +-----------+------------+----------------+---------------+
    | id_pedido | id_cliente | fecha_esperada | fecha_entrega |
    +-----------+------------+----------------+---------------+
    |         2 |          2 | 2024-01-24     | 2024-01-22    |
    +-----------+------------+----------------+---------------+
    ```
    ---
- Utilizando la función DATEDIFF de MySQL.
    ```sql
    SELECT p.id_pedido, p.id_cliente, p.fecha_esperada, p.fecha_entrega
    FROM pedido p
    WHERE DATEDIFF(p.fecha_esperada, p.fecha_entrega) >= 2;


    +-----------+------------+----------------+---------------+
    | id_pedido | id_cliente | fecha_esperada | fecha_entrega |
    +-----------+------------+----------------+---------------+
    |         2 |          2 | 2024-01-24     | 2024-01-22    |
    +-----------+------------+----------------+---------------+
    ```
    ---
- ¿Sería posible resolver esta consulta utilizando el operador de suma + o resta -?
    ```sql
    SELECT p.id_pedido, p.id_cliente, p.fecha_esperada, p.fecha_entrega
    FROM pedido p
    WHERE p.fecha_entrega = p.fecha_esperada - 2;
    
    +-----------+------------+----------------+---------------+
    | id_pedido | id_cliente | fecha_esperada | fecha_entrega |
    +-----------+------------+----------------+---------------+
    |         2 |          2 | 2024-01-24     | 2024-01-22    |
    +-----------+------------+----------------+---------------+
    ```
    ---
11. Devuelve un listado de todos los pedidos que fueron rechazados en 2009.
    ```sql
    SELECT p.id_pedido, p.id_cliente, p.fecha_pedido, p.fecha_esperada, p.estado
    FROM pedido p
    WHERE p.estado = 'Rechazado' AND YEAR(p.fecha_pedido
    ) = 2009;
    
    +-----------+------------+--------------+----------------+-----------+
    | id_pedido | id_cliente | fecha_pedido | fecha_esperada | estado    |
    +-----------+------------+--------------+----------------+-----------+
    |         4 |          4 | 2009-04-18   | 2009-04-22     | Rechazado |
    +-----------+------------+--------------+----------------+-----------+
    ```
    ---
12. Devuelve un listado de todos los pedidos que han sido entregados en el mes de enero de cualquier año.
    ```sql
    SELECT p.id_pedido, p.id_cliente, p.fecha_pedido, p.fecha_esperada, fecha_entrega, p.estado
    FROM pedido p
    WHERE p.estado = 'Entregado' AND MONTH(p.fecha_entrega
    ) = '01';
    
    +-----------+------------+--------------+----------------+---------------+-----------+
    | id_pedido | id_cliente | fecha_pedido | fecha_esperada | fecha_entrega | estado    |
    +-----------+------------+--------------+----------------+---------------+-----------+
    |         2 |          2 | 2024-01-18   | 2024-01-24     | 2024-01-22    | Entregado |
    +-----------+------------+--------------+----------------+---------------+-----------+
    ```
    ---

13. Devuelve un listado con todos los pagos que se realizaron en el año 2008 mediante Paypal. Ordene el resultado de mayor a menor.
    ```sql
    SELECT p.id_transaccion, p.id_cliente, p.id_forma_de_pago, f.nombre_forma_de_pago, p.fecha_pago, p.total
    FROM pago p
    JOIN forma_de_pago f ON f.id_forma_de_pago = p.id_forma_de_pago
    WHERE p.id_forma_de_pago = 3 AND YEAR(p.fecha_pago) = 2008;
    
    +----------------+------------+------------------+----------------------+------------+--------+
    | id_transaccion | id_cliente | id_forma_de_pago | nombre_forma_de_pago | fecha_pago | total  |
    +----------------+------------+------------------+----------------------+------------+--------+
    | TRX003         |          3 |                3 | Paypal               | 2008-05-04 | 300.00 |
    +----------------+------------+------------------+----------------------+------------+--------+
    ```
    ---
14. Devuelve un listado con todas las formas de pago que aparecen en la tabla pago. Tenga en cuenta que no deben aparecer formas de pago repetidas.
    ```sql
    SELECT DISTINCT p.id_forma_de_pago, f.nombre_forma_de_pago
    FROM pago p
    JOIN forma_de_pago f ON f.id_forma_de_pago = p.id_forma_de_pago;
    
    +------------------+----------------------+
    | id_forma_de_pago | nombre_forma_de_pago |
    +------------------+----------------------+
    |                1 | Efectivo             |
    |                2 | Tarjeta de crédito   |
    |                3 | Paypal               |
    +------------------+----------------------+
    ```
    ---
15. Devuelve un listado con todos los productos que pertenecen a la gama Ornamentales y que tienen más de 100 unidades en stock. El listado deberá estar ordenado por su precio de venta, mostrando en primer lugar los de mayor precio.
    ```sql
    SELECT p.id_producto, p.nombre, p.gama, p.cantidad_en_stock, p.precio_venta
    FROM producto p
    WHERE gama = 'Ornamental' AND cantidad_en_stock > 100
    ORDER BY p.precio_venta ASC;
    
    +-------------+-----------------------+------------+-------------------+--------------+
    | id_producto | nombre                | gama       | cantidad_en_stock | precio_venta |
    +-------------+-----------------------+------------+-------------------+--------------+
    | PROD012     | Producto Ornamental 2 | Ornamental |               150 |        29.99 |
    +-------------+-----------------------+------------+-------------------+--------------+
    ```
    ---
16. Devuelve un listado con todos los clientes que sean de la ciudad de Madrid y cuyo representante de ventas tenga el código de empleado 11 o 30.
    ```sql
    SELECT cl.id_cliente, cl.nombre_cliente, cl.telefono, cl.id_ciudad, c.nombre_ciudad, cl.id_empleado_rep_ventas
    FROM cliente cl
    JOIN ciudad c ON cl.id_ciudad = c.id_ciudad
    WHERE c.nombre_ciudad = 'Madrid' AND cl.id_empleado_rep_ventas IN (11, 30); 
    
    +------------+----------------+-----------+-----------+---------------+------------------------+
    | id_cliente | nombre_cliente | telefono  | id_ciudad | nombre_ciudad | id_empleado_rep_ventas |
    +------------+----------------+-----------+-----------+---------------+------------------------+
    |         11 | Cliente Madrid | 123456789 |        15 | Madrid        |                     11 |
    +------------+----------------+-----------+-----------+---------------+------------------------+
    ```
    ---

### Consultas multitabla (Composición interna)
**Resuelva todas las consultas utilizando la sintaxis de SQL1 y SQL2. Las consultas con sintaxis de SQL2 se deben resolver con INNER JOIN y NATURAL JOIN.**

1. Obtén un listado con el nombre de cada cliente y el nombre y apellido de su representante de ventas.
    ```sql
    SELECT cl.nombre_cliente, e.nombre, e.apellido1, e.apellido2
    FROM cliente cl
    JOIN empleado e ON e.id_empleado = cl.id_empleado_rep_ventas; 

    +----------------+--------+-----------+-----------+
    | nombre_cliente | nombre | apellido1 | apellido2 |
    +----------------+--------+-----------+-----------+
    | Cliente A      | Juan   | García    | López     |
    | Cliente B      | María  | Martínez  | Rodríguez |
    | Cliente C      | Pedro  | Hernández | Pérez     |
    | Cliente D      | Ana    | López     | Gómez     |
    | Cliente E      | Carlos | Díaz      | Sánchez   |
    | Cliente F      | Laura  | Rodríguez | Fernández |
    | Cliente G      | Javier | Gómez     | Martínez  |
    | Cliente H      | Sofía  | Pérez     | González  |
    | Cliente I      | Diego  | Fernández | López     |
    | Cliente J      | Elena  | Sánchez   | Martínez  |
    | Cliente Madrid | Pablo  | González  | Hernández |
    +----------------+--------+-----------+-----------+
    ```
    ---
2. Muestra el nombre de los clientes que hayan realizado pagos junto con el nombre de sus representantes de ventas.
    ```sql
    SELECT cl.nombre_cliente, CONCAT(e.nombre, ' ', e.apellido1, ' ', e.apellido2) AS nombre_rep_ventas
    FROM cliente cl
    JOIN pago p ON cl.id_cliente = p.id_cliente
    JOIN empleado e ON cl.id_empleado_rep_ventas = e.id_empleado;

    +----------------+--------------------------+
    | nombre_cliente | nombre_rep_ventas        |
    +----------------+--------------------------+
    | Cliente A      | Juan García López        |
    | Cliente B      | María Martínez Rodríguez |
    | Cliente C      | Pedro Hernández Pérez    |
    | Cliente D      | Ana López Gómez          |
    | Cliente E      | Carlos Díaz Sánchez      |
    +----------------+--------------------------+
    ```
    ---
3. Muestra el nombre de los clientes que no hayan realizado pagos junto con el nombre de sus representantes de ventas.
    ```sql
    SELECT cl.nombre_cliente, CONCAT(e.nombre, ' ', e.apellido1, ' ', e.apellido2) AS nombre_rep_ventas
    FROM cliente cl
    JOIN empleado e ON e.id_empleado = cl.id_empleado_rep_ventas
    WHERE id_cliente NOT IN (SELECT id_cliente FROM pago);

    +----------------+---------------------------+
    | nombre_cliente | nombre_rep_ventas         |
    +----------------+---------------------------+
    | Cliente F      | Laura Rodríguez Fernández |
    | Cliente G      | Javier Gómez Martínez     |
    | Cliente H      | Sofía Pérez González      |
    | Cliente I      | Diego Fernández López     |
    | Cliente J      | Elena Sánchez Martínez    |
    | Cliente Madrid | Pablo González Hernández  |
    +----------------+---------------------------+
    ```
    ---
4. Devuelve el nombre de los clientes que han hecho pagos y el nombre de sus representantes junto con la ciudad de la oficina a la que pertenece el representante.
    ```sql
    SELECT cl.nombre_cliente, CONCAT(e.nombre, ' ', e.apellido1, ' ', e.apellido2) AS nombre_representante, c.nombre_ciudad AS ciudad_oficina
    FROM cliente cl
    JOIN pago p ON cl.id_cliente = p.id_cliente
    JOIN empleado e ON cl.id_empleado_rep_ventas = e.id_empleado
    JOIN oficina o ON e.id_oficina = o.id_oficina
    JOIN ciudad c ON o.id_ciudad = c.id_ciudad;

    +----------------+--------------------------+----------------+
    | nombre_cliente | nombre_representante     | ciudad_oficina |
    +----------------+--------------------------+----------------+
    | Cliente A      | Juan García López        | Los Angeles    |
    | Cliente B      | María Martínez Rodríguez | San Francisco  |
    | Cliente C      | Pedro Hernández Pérez    | New York       |
    | Cliente D      | Ana López Gómez          | Buffalo        |
    | Cliente E      | Carlos Díaz Sánchez      | Grenoble       |
    +----------------+--------------------------+----------------+
    ```
    ---
5. Devuelve el nombre de los clientes que no hayan hecho pagos y el nombre de sus representantes junto con la ciudad de la oficina a la que pertenece el representante.
    ```sql
    SELECT cl.nombre_cliente, CONCAT(e.nombre, ' ', e.apellido1, ' ', e.apellido2) AS nombre_representante, c.nombre_ciudad AS ciudad_oficina
    FROM cliente cl
    JOIN empleado e ON cl.id_empleado_rep_ventas = e.id_empleado
    JOIN oficina o ON e.id_oficina = o.id_oficina
    JOIN ciudad c ON o.id_ciudad = c.id_ciudad
    WHERE id_cliente NOT IN (SELECT id_cliente FROM pago);

    +----------------+---------------------------+----------------+
    | nombre_cliente | nombre_representante      | ciudad_oficina |
    +----------------+---------------------------+----------------+
    | Cliente F      | Laura Rodríguez Fernández | Lyon           |
    | Cliente G      | Javier Gómez Martínez     | Tours          |
    | Cliente H      | Sofía Pérez González      | Orléans        |
    | Cliente I      | Diego Fernández López     | Sevilla        |
    | Cliente J      | Elena Sánchez Martínez    | Málaga         |
    | Cliente Madrid | Pablo González Hernández  | Barcelona      |
    +----------------+---------------------------+----------------+
    ```
    ---
6. Lista la dirección de las oficinas que tengan clientes en Bogotá.
    ```sql
    SELECT d.direccion
    FROM direccion d
    JOIN oficina o ON d.id_direccion = o.id_direccion 
    JOIN ciudad c ON o.id_ciudad = c.id_ciudad
    WHERE c.nombre_ciudad = 'Bogotá';

    +-------------+
    | direccion   |
    +-------------+
    | 123 Calle 7 |
    +-------------+
    ```
    ---
7. Devuelve el nombre de los clientes y el nombre de sus representantes junto con la ciudad de la oficina a la que pertenece el representante.
    ```sql
    SELECT cl.nombre_cliente, CONCAT(e.nombre, ' ', e.apellido1, ' ', e.apellido2) AS nombre_rep_ventas, c.nombre_ciudad AS ciudad_oficina_rep
    FROM cliente cl
    JOIN empleado e ON cl.id_empleado_rep_ventas = e.id_empleado
    JOIN oficina o ON e.id_oficina = o.id_oficina 
    JOIN ciudad c ON o.id_ciudad = c.id_ciudad;

    +----------------+---------------------------+--------------------+
    | nombre_cliente | nombre_rep_ventas         | ciudad_oficina_rep |
    +----------------+---------------------------+--------------------+
    | Cliente A      | Juan García López         | Los Angeles        |
    | Cliente B      | María Martínez Rodríguez  | San Francisco      |
    | Cliente C      | Pedro Hernández Pérez     | New York           |
    | Cliente D      | Ana López Gómez           | Buffalo            |
    | Cliente E      | Carlos Díaz Sánchez       | Grenoble           |
    | Cliente F      | Laura Rodríguez Fernández | Lyon               |
    | Cliente G      | Javier Gómez Martínez     | Tours              |
    | Cliente H      | Sofía Pérez González      | Orléans            |
    | Cliente I      | Diego Fernández López     | Sevilla            |
    | Cliente J      | Elena Sánchez Martínez    | Málaga             |
    | Cliente Madrid | Pablo González Hernández  | Barcelona          |
    +----------------+---------------------------+--------------------+
    ```
    ---
8. Devuelve un listado con el nombre de los empleados junto con el nombre de sus jefes.
    ```sql
    SELECT CONCAT(e.nombre, ' ', e.apellido1, ' ', e.apellido2) AS nombre_empleado, CONCAT(j.nombre, ' ', j.apellido1, ' ', j.apellido2) AS nombre_jefe
    FROM empleado e
    LEFT JOIN empleado j ON e.id_jefe = j.id_empleado;

    +---------------------------+---------------------------+
    | nombre_empleado           | nombre_jefe               |
    +---------------------------+---------------------------+
    | Juan García López         | NULL                      |
    | María Martínez Rodríguez  | Juan García López         |
    | Pedro Hernández Pérez     | Juan García López         |
    | Ana López Gómez           | María Martínez Rodríguez  |
    | Carlos Díaz Sánchez       | María Martínez Rodríguez  |
    | Laura Rodríguez Fernández | Pedro Hernández Pérez     |
    | Javier Gómez Martínez     | Pedro Hernández Pérez     |
    | Sofía Pérez González      | Ana López Gómez           |
    | Diego Fernández López     | Ana López Gómez           |
    | Elena Sánchez Martínez    | Carlos Díaz Sánchez       |
    | Pablo González Hernández  | Carlos Díaz Sánchez       |
    | Isabel Gómez Rodríguez    | Laura Rodríguez Fernández |
    | Andrés Martínez Díaz      | Laura Rodríguez Fernández |
    | Luisa Hernández Sánchez   | Javier Gómez Martínez     |
    +---------------------------+---------------------------+
    ```
    ---
9. Devuelve un listado que muestre el nombre de cada empleados, el nombre de su jefe y el nombre del jefe de sus jefe.
    ```sql
    SELECT CONCAT(e.nombre, ' ', e.apellido1, ' ', e.apellido2) AS nombre_empleado, CONCAT(j.nombre, ' ', j.apellido1, ' ', j.apellido2) AS nombre_jefe, CONCAT(jj.nombre, ' ', jj.apellido1, ' ', jj.apellido2) AS nombre_jefe_jefe
    FROM empleado e
    LEFT JOIN empleado j ON e.id_jefe = j.id_empleado
    LEFT JOIN empleado jj ON j.id_jefe = jj.id_empleado;

    +---------------------------+---------------------------+--------------------------+
    | nombre_empleado           | nombre_jefe               | nombre_jefe_jefe         |
    +---------------------------+---------------------------+--------------------------+
    | Juan García López         | NULL                      | NULL                     |
    | María Martínez Rodríguez  | Juan García López         | NULL                     |
    | Pedro Hernández Pérez     | Juan García López         | NULL                     |
    | Ana López Gómez           | María Martínez Rodríguez  | Juan García López        |
    | Carlos Díaz Sánchez       | María Martínez Rodríguez  | Juan García López        |
    | Laura Rodríguez Fernández | Pedro Hernández Pérez     | Juan García López        |
    | Javier Gómez Martínez     | Pedro Hernández Pérez     | Juan García López        |
    | Sofía Pérez González      | Ana López Gómez           | María Martínez Rodríguez |
    | Diego Fernández López     | Ana López Gómez           | María Martínez Rodríguez |
    | Elena Sánchez Martínez    | Carlos Díaz Sánchez       | María Martínez Rodríguez |
    | Pablo González Hernández  | Carlos Díaz Sánchez       | María Martínez Rodríguez |
    | Isabel Gómez Rodríguez    | Laura Rodríguez Fernández | Pedro Hernández Pérez    |
    | Andrés Martínez Díaz      | Laura Rodríguez Fernández | Pedro Hernández Pérez    |
    | Luisa Hernández Sánchez   | Javier Gómez Martínez     | Pedro Hernández Pérez    |
    +---------------------------+---------------------------+--------------------------+
    ```
    ---
10. Devuelve el nombre de los clientes a los que no se les ha entregado a tiempo un pedido.
    ```sql
    SELECT cl.nombre_cliente, p.estado AS estado_pedido
    FROM cliente cl
    JOIN pedido p ON cl.id_cliente = p.id_cliente
    WHERE p.estado <> 'Entregado';

    +----------------+---------------+
    | nombre_cliente | estado_pedido |
    +----------------+---------------+
    | Cliente A      | En proceso    |
    | Cliente D      | Rechazado     |
    | Cliente E      | En proceso    |
    +----------------+---------------+
    ```
    ---
11. Devuelve un listado de las diferentes gamas de producto que ha comprado cada cliente.
    ```sql
    SELECT c.nombre_cliente, GROUP_CONCAT(DISTINCT pr.gama) AS gamas_compradas
    FROM cliente c
    JOIN pedido p ON c.id_cliente = p.id_cliente
    JOIN detalle_pedido dp ON p.id_pedido = dp.id_pedido
    JOIN producto pr ON dp.id_producto = pr.id_producto
    GROUP BY c.id_cliente;
    
    
    +----------------+-----------------+
    | nombre_cliente | gamas_compradas |
    +----------------+-----------------+
    | Cliente A      | Lujo,Orgánico   |
    | Cliente B      | Gourmet         |
    | Cliente C      | Orgánico        |
    | Cliente D      | Gourmet         |
    | Cliente E      | Saludable       |
    +----------------+-----------------+
    ```
    ---

### Consultas multitabla (Composición externa)
**Resuelva todas las consultas utilizando las cláusulas LEFT JOIN, RIGHT JOIN, NATURAL LEFT JOIN y NATURAL RIGHT JOIN.**
---

1. Devuelve un listado que muestre solamente los clientes que no han realizado ningún pago.
    ```sql
    SELECT c.nombre_cliente
    FROM cliente c
    LEFT JOIN pago p ON c.id_cliente = p.id_cliente
    WHERE p.id_transaccion IS NULL;

    +----------------+
    | nombre_cliente |
    +----------------+
    | Cliente F      |
    | Cliente G      |
    | Cliente H      |
    | Cliente I      |
    | Cliente J      |
    | Cliente Madrid |
    +----------------+
    ```
    ---
2. Devuelve un listado que muestre solamente los clientes que no han realizado ningún pedido.
    ```sql
    SELECT c.id_cliente, c.nombre_cliente
    FROM cliente c
    LEFT JOIN pedido p ON c.id_cliente = p.id_cliente
    WHERE p.id_pedido IS NULL;

    +------------+----------------+
    | id_cliente | nombre_cliente |
    +------------+----------------+
    |          6 | Cliente F      |
    |          7 | Cliente G      |
    |          8 | Cliente H      |
    |          9 | Cliente I      |
    |         10 | Cliente J      |
    |         11 | Cliente Madrid |
    +------------+----------------+
    ```
    ---
3. Devuelve un listado que muestre los clientes que no han realizado ningún pago y los que no han realizado ningún pedido.
    ```sql
    SELECT c.id_cliente, c.nombre_cliente
    FROM cliente c
    LEFT JOIN pago p ON c.id_cliente = p.id_cliente
    LEFT JOIN pedido pd ON c.id_cliente = pd.id_cliente
    WHERE p.id_transaccion IS NULL AND pd.id_pedido IS NULL;

    +------------+----------------+
    | id_cliente | nombre_cliente |
    +------------+----------------+
    |          6 | Cliente F      |
    |          7 | Cliente G      |
    |          8 | Cliente H      |
    |          9 | Cliente I      |
    |         10 | Cliente J      |
    |         11 | Cliente Madrid |
    +------------+----------------+
    ```
    ---
4. Devuelve un listado que muestre solamente los empleados que no tienen una oficina asociada.
    ```sql
    SELECT e.id_empleado, CONCAT(e.nombre, ' ', e.apellido1, ' ', e.apellido2) AS nombre_empleado
    FROM empleado e
    LEFT JOIN oficina o ON e.id_oficina = o.id_oficina
    WHERE o.id_oficina IS NULL;

    +-------------+------------------------+
    | id_empleado | nombre_empleado        |
    +-------------+------------------------+
    |          15 | Samuel Rubiano Orjuela |
    +-------------+------------------------+
    ```
    ---
5. Devuelve un listado que muestre solamente los empleados que no tienen un cliente asociado.
    ```sql
    SELECT e.id_empleado, CONCAT(e.nombre, ' ', e.apellido1, ' ', e.apellido2) AS nombre_empleado
    FROM empleado e
    LEFT JOIN cliente c ON e.id_empleado = c.id_empleado_rep_ventas
    WHERE c.id_cliente IS NULL;

    +-------------+-------------------------+
    | id_empleado | nombre_empleado         |
    +-------------+-------------------------+
    |          12 | Isabel Gómez Rodríguez  |
    |          13 | Andrés Martínez Díaz    |
    |          14 | Luisa Hernández Sánchez |
    |          15 | Samuel Rubiano Orjuela  |
    +-------------+-------------------------+
    ```
    ---
6. Devuelve un listado que muestre solamente los empleados que no tienen un cliente asociado junto con los datos de la oficina donde trabajan.
    ```sql
    SELECT e.id_empleado, CONCAT(e.nombre, ' ', e.apellido1, ' ', e.apellido2) AS nombre_empleado, d.direccion AS direccion_oficina
    FROM empleado e
    LEFT JOIN cliente cl ON e.id_empleado = cl.id_empleado_rep_ventas
    LEFT JOIN oficina o ON e.id_oficina = o.id_oficina
    LEFT JOIN direccion d ON o.id_direccion = d.id_direccion
    WHERE cl.id_cliente IS NULL;

    +-------------+-------------------------+----------------------+
    | id_empleado | nombre_empleado         | direccion_oficina    |
    +-------------+-------------------------+----------------------+
    |          12 | Isabel Gómez Rodríguez  | 101 Carrer dels Arcs |
    |          13 | Andrés Martínez Díaz    | 123 Calle 7          |
    |          14 | Luisa Hernández Sánchez | 456 Carrera 70       |
    |          15 | Samuel Rubiano Orjuela  | NULL                 |
    +-------------+-------------------------+----------------------+
    ```
    ---
7. Devuelve un listado que muestre los empleados que no tienen una oficina asociada y los que no tienen un cliente asociado.
    ```sql
    SELECT e.id_empleado, CONCAT(e.nombre, ' ', e.apellido1, ' ', e.apellido2) AS nombre_empleado
    FROM empleado e
    LEFT JOIN cliente cl ON e.id_empleado = cl.id_empleado_rep_ventas
    LEFT JOIN oficina o ON e.id_oficina = o.id_oficina
    WHERE cl.id_cliente IS NULL AND o.id_oficina IS NULL;

    +-------------+------------------------+
    | id_empleado | nombre_empleado        |
    +-------------+------------------------+
    |          15 | Samuel Rubiano Orjuela |
    +-------------+------------------------+
    ```
    ---
8. Devuelve un listado de los productos que nunca han aparecido en un pedido.
    ```sql
    SELECT p.id_producto, p.nombre AS nombre_producto
    FROM producto p
    LEFT JOIN detalle_pedido dp ON p.id_producto = dp.id_producto
    WHERE dp.id_producto IS NULL;

    +-------------+------------------------------+
    | id_producto | nombre_producto              |
    +-------------+------------------------------+
    | PROD007     | Artisanal Bread Selection    |
    | PROD008     | Superfood Smoothie Mix       |
    | PROD009     | Farm Fresh Eggs Carton       |
    | PROD010     | Handcrafted Pasta Assortment |
    | PROD012     | Producto Ornamental 2        |
    +-------------+------------------------------+
    ```
    ---
9. Devuelve un listado de los productos que nunca han aparecido en un pedido. El resultado debe mostrar el nombre, la descripción y la imagen del producto.
    ```sql
    SELECT p.nombre AS nombre_producto, g.imagen
    FROM producto p
    LEFT JOIN gama_producto g ON p.gama = g.gama
    LEFT JOIN detalle_pedido dp ON p.id_producto = dp.id_producto
    WHERE dp.id_producto IS NULL;

    +------------------------------+-----------------------+
    | nombre_producto              | imagen                |
    +------------------------------+-----------------------+
    | Artisanal Bread Selection    | NULL                  |
    | Superfood Smoothie Mix       | NULL                  |
    | Farm Fresh Eggs Carton       | NULL                  |
    | Handcrafted Pasta Assortment | NULL                  |
    | Producto Ornamental 2        | imagen_ornamental.jpg |
    +------------------------------+-----------------------+
    ```
    ---
10. Devuelve las oficinas donde no trabajan ninguno de los empleados que hayan sido los representantes de ventas de algún cliente que haya realizado la compra de algún producto de la gama Frutales.
    ```sql
    SELECT e.id_oficina, o.telefono
    FROM empleado e
    LEFT JOIN oficina o ON e.id_oficina = o.id_oficina 
    LEFT JOIN cliente cl ON e.id_empleado = cl.id_empleado_rep_ventas 
    LEFT JOIN pedido p ON cl.id_cliente = p.id_cliente
    LEFT JOIN detalle_pedido dp ON p.id_pedido = dp.id_pedido
    LEFT JOIN producto pr ON dp.id_producto = pr.id_producto
    WHERE pr.gama <> 'Frutales' AND e.id_empleado IS NULL;

    +------------+--------------+
    | id_oficina | telefono     |
    +------------+--------------+
    | OF001      | 123-456-7890 |
    +------------+--------------+
    ```
    ---
11. Devuelve un listado con los clientes que han realizado algún pedido pero no han realizado ningún pago.
    ```sql
    SELECT cl.id_cliente, cl.nombre_cliente
    FROM cliente cl
    LEFT JOIN pedido p ON cl.id_cliente = p.id_cliente
    LEFT JOIN pago pa ON cl.id_cliente = pa.id_cliente
    WHERE p.id_pedido IS NOT NULL AND pa.id_transaccion IS NULL;

    +------------+-----------------+
    | id_cliente | nombre_cliente  |
    +------------+-----------------+
    |         12 | Cliente Nuevo 1 |
    |         13 | Cliente Nuevo 2 |
    +------------+-----------------+
    ```
    ---
12. Devuelve un listado con los datos de los empleados que no tienen clientes asociados y el nombre de su jefe asociado. 
    ```sql
    SELECT e.id_empleado, CONCAT(e.nombre, ' ', e.apellido1, ' ', e.apellido2) AS nombre_empleado, j.id_empleado AS id_jefe, CONCAT(j.nombre, ' ', j.apellido1, ' ', j.apellido2) AS nombre_jefe
    FROM empleado e
    LEFT JOIN empleado j ON e.id_jefe = j.id_empleado
    LEFT JOIN cliente cl ON e.id_empleado = cl.id_empleado_rep_ventas
    WHERE cl.id_empleado_rep_ventas IS NULL;

    +-------------+-------------------------+---------+---------------------------+
    | id_empleado | nombre_empleado         | id_jefe | nombre_jefe               |
    +-------------+-------------------------+---------+---------------------------+
    |          12 | Isabel Gómez Rodríguez  |       6 | Laura Rodríguez Fernández |
    |          13 | Andrés Martínez Díaz    |       6 | Laura Rodríguez Fernández |
    |          14 | Luisa Hernández Sánchez |       7 | Javier Gómez Martínez     |
    |          15 | Samuel Rubiano Orjuela  |    NULL | NULL                      |
    +-------------+-------------------------+---------+---------------------------+
    ```
    ---

### Consultas resumen
---
1. ¿Cuántos empleados hay en la compañía?
	```sql
    SELECT COUNT(id_empleado) AS cantidad_empleados
    FROM empleado;

    +--------------------+
    | cantidad_empleados |
    +--------------------+
    |                 15 |
    +--------------------+
	```
	---
2. ¿Cuántos clientes tiene cada país?
	```sql
    SELECT p.id_pais, p.nombre_pais, COUNT(cl.id_cliente) AS cantidad_clientes
    FROM cliente cl
    JOIN ciudad c ON cl.id_ciudad = c.id_ciudad
    JOIN region r ON c.id_region = r.id_region
    JOIN pais p ON r.id_pais = p.id_pais
    GROUP BY p.nombre_pais;

    +----------------+-------------------+
    | nombre_pais    | cantidad_clientes |
    +----------------+-------------------+
    | Estados Unidos |                 7 |
    | Francia        |                 4 |
    | España         |                 2 |
    +----------------+-------------------+
	```
	---
3. ¿Cuál fue el pago medio en 2009?
	```sql
    SELECT CONCAT('$',ROUND(SUM(total) / COUNT(total), 2)) AS promedio_pagos_2009
    FROM pago
    WHERE YEAR(fecha_pago) = 2009;

    +---------------------+
    | promedio_pagos_2009 |
    +---------------------+
    | $200.00             |
    +---------------------+
	```
	---
4. ¿Cuántos pedidos hay en cada estado? Ordena el resultado de forma descendente por el número de pedidos.
	```sql
    SELECT r.nombre_region, COUNT(id_pedido) AS cantidad_pedidos_region
    FROM pedido p
    JOIN cliente cl ON p.id_cliente = cl.id_cliente
    JOIN ciudad c ON cl.id_ciudad = c.id_ciudad
    JOIN region r ON c.id_region = r.id_region
    GROUP BY r.nombre_region
    ORDER BY cantidad_pedidos_region DESC;

    +---------------+-------------------------+
    | nombre_region | cantidad_pedidos_region |
    +---------------+-------------------------+
    | California    |                       4 |
    | Nueva York    |                       2 |
    | Isère         |                       1 |
    +---------------+-------------------------+
	```
	---
5. Calcula el precio de venta del producto más caro y más barato en una misma consulta.
	```sql
    SELECT MAX(precio_venta) AS precio_mas_caro, MIN(precio_venta) AS precio_mas_barato
    FROM producto;

    +-----------------+-------------------+
    | precio_mas_caro | precio_mas_barato |
    +-----------------+-------------------+
    |           49.99 |              7.99 |
    +-----------------+-------------------+
	```
	---
6. Calcula el número de clientes que tiene la empresa.
	```sql
    SELECT COUNT(id_cliente) AS cantidad_clientes
    FROM cliente;

    +-------------------+
    | cantidad_clientes |
    +-------------------+
    |                13 |
    +-------------------+
	```
	---
7. ¿Cuántos clientes existen con domicilio en la ciudad de Madrid?
	```sql
    SELECT COUNT(cl.id_cliente) AS cantidad_clientes_madrid
    FROM cliente cl
    JOIN ciudad c ON cl.id_ciudad = c.id_ciudad
    WHERE c.nombre_ciudad = 'Madrid';

    +--------------------------+
    | cantidad_clientes_madrid |
    +--------------------------+
    |                        1 |
    +--------------------------+
	```
	---
8. ¿Calcula cuántos clientes tiene cada una de las ciudades que empiezan por M?
	```sql
    SELECT COUNT(cl.id_cliente) AS cantidad_clientes_M
    FROM cliente cl
    JOIN ciudad c ON cl.id_ciudad = c.id_ciudad
    WHERE LEFT(c.nombre_ciudad, 1) = 'M';

    +---------------------+
    | cantidad_clientes_M |
    +---------------------+
    |                   2 |
    +---------------------+
	```
	---
9. Devuelve el nombre de los representantes de ventas y el número de clientes al que atiende cada uno.
	```sql
    SELECT CONCAT(nombre, ' ', apellido1, ' ', apellido2) AS nombre_rep_ventas,
    COUNT(cl.id_cliente) AS cant_clientes_encargados
    FROM empleado e
    JOIN cliente cl ON e.id_empleado = cl.id_empleado_rep_ventas
    GROUP BY nombre_rep_ventas;

    +---------------------------+--------------------------+
    | nombre_rep_ventas         | cant_clientes_encargados |
    +---------------------------+--------------------------+
    | Juan García López         |                        2 |
    | María Martínez Rodríguez  |                        2 |
    | Pedro Hernández Pérez     |                        1 |
    | Ana López Gómez           |                        1 |
    | Carlos Díaz Sánchez       |                        1 |
    | Laura Rodríguez Fernández |                        1 |
    | Javier Gómez Martínez     |                        1 |
    | Sofía Pérez González      |                        1 |
    | Diego Fernández López     |                        1 |
    | Elena Sánchez Martínez    |                        1 |
    | Pablo González Hernández  |                        1 |
    +---------------------------+--------------------------+
	```
	---
10. Calcula el número de clientes que no tiene asignado representante de ventas.
	```sql
    SELECT telefono
    FROM cliente cl
    LEFT JOIN empleado e ON cl.id_empleado_rep_ventas = e.id_empleado
    WHERE cl.id_empleado_rep_ventas IS NULL;

    +----------+
    | telefono |
    +----------+
    | 66061005 |
    | 66161516 |
    +----------+
	```
	---
11. Calcula la fecha del primer y último pago realizado por cada uno de los clientes. El listado deberá mostrar el nombre y los apellidos de cada cliente.
	```sql
    SELECT CONCAT(cl.nombre_contacto, ' ',cl.apellido_contacto) AS nombre_cliente,
    MIN(p.fecha_pago) AS primer_pago,
    MAX(p.fecha_pago) AS ultimo_pago
    FROM cliente cl
    LEFT JOIN pago p ON cl.id_cliente = p.id_cliente
    GROUP BY cl.nombre_contacto, cl.apellido_contacto;
    
    +-------------------+-------------+-------------+
    | nombre_cliente    | primer_pago | ultimo_pago |
    +-------------------+-------------+-------------+
    | Juan Pérez        | 2024-04-19  | 2024-04-19  |
    | María Gómez       | 2024-01-18  | 2024-01-18  |
    | Pedro Rodríguez   | 2008-05-04  | 2008-05-04  |
    | Ana López         | 2009-04-18  | 2009-04-18  |
    | Carlos Martínez   | 2024-04-15  | 2024-04-15  |
    | Laura Fernández   | NULL        | NULL        |
    | Javier Gómez      | NULL        | NULL        |
    | Sofía Pérez       | NULL        | NULL        |
    | Diego Hernández   | NULL        | NULL        |
    | Elena Sánchez     | NULL        | NULL        |
    | Juan López        | NULL        | NULL        |
    | Angel Gomez       | NULL        | NULL        |
    | Claudia Rodriguez | NULL        | NULL        |
    | Juan Ramirez      | NULL        | NULL        |
    | Mario Bros        | NULL        | NULL        |
    +-------------------+-------------+-------------+
	```
	---
12. Calcula el número de productos diferentes que hay en cada uno de los pedidos. 
	```sql

	```
	---
13. Calcula la suma de la cantidad total de todos los productos que aparecen en cada uno de los pedidos.
	```sql

	```
	---
14. Devuelve un listado de los 20 productos más vendidos y el número total de unidades que se han vendido de cada uno. El listado deberá estar ordenado por el número total de unidades vendidas.
	```sql

	```
	---
15. La facturación que ha tenido la empresa en toda la historia, indicando la base imponible, el IVA y el total facturado. La base imponible se calcula sumando el coste del producto por el número de unidades vendidas de la tabla detalle_pedido. El IVA es el 21 % de la base imponible, y el total la suma de los dos campos anteriores.
	```sql

	```
	---
16. La misma información que en la pregunta anterior, pero agrupada por código de producto.
	```sql

	```
	---
17. La misma información que en la pregunta anterior, pero agrupada por código de producto filtrada por los códigos que empiecen por OR.
	```sql

	```
	---
18. Lista las ventas totales de los productos que hayan facturado más de 3000 euros. Se mostrará el nombre, unidades vendidas, total facturado y total facturado con impuestos (21% IVA).
	```sql

	```
	---
19. Muestre la suma total de todos los pagos que se realizaron para cada uno de los años que aparecen en la tabla pagos.
	```sql

	```
	---
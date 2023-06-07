
## Base de datos.
> *Iniciar sesión desde la consola*.
<pre>
<code>
psql --username=postgres --dbname=postgres
</code>
</pre>
___

> *Ver la lista de las base de datos*.
```sql
postgres=> \l
```
___
>*Crear una nueva base dato*.
```sql
postgres=> CREATE DATABASE sis_venta;
```
___
>*Usar una base de datos*.
```sql
postgres=> \c sis_venta;
//se cambio la base de datos
sis_venta=>
```
___
>*Renombrar una base de datos.*
```sql
sis_venta=> ALTER DATABASE first_database RENAME TO mario_database;
```
*``NOTA: ``no puedes renombrar la base de datos que estas usando. Para cambiar su nombre debes de pasarte a otra base de datos y manipularla desde ahí o tambien puedes desconectarte de ella.*
___
>Eliminar una base de datos especifica.
```sql
sis_venta=> DROP DATABASE mario_database;
```
___
# Tablas.

> *Mostrar tablas de la base de datos.*

```sql
sis_venta=> \d
```
___

>*Crear una tabla vacia*.

```sql
sis_venta=> CREATE TABLE clientes();
```
___
>*Mostrar la estructura de una tabla especifica*.
```sql
sis_venta=> \d clientes
```
___
>*Agregar una columna dentro de la tabla*.

```sql
sis_venta=> ALTER TABLE characters ADD COLUMN cliente_id SERIAL;
```
*el comando `SERIAL` al final de una columna la convierte en tipo `INT` haciendo que su valor no sea vacio y que este se autoincremente*.
```sql
sis_venta=> ALTER TABLE clientes ADD COLUMN nombre VARCHAR(30) NOT NULL;
```
*y con el comando `NOT NULL` hacemos que nuestra columna nunca se encuentre vacia.*
___
>*Eliminar una columna especifica de la tabla*.
```sql
sis_venta=> ALTER TABLE clientes DROP COLUMN nombre;
```
___
>*Renombrar una columna especifica de la tabla*.
```sql
sis_venta=> ALTER TABLE clientes RENAME COLUMN nombre TO nombre_completo;
```
___

> *Mostrar los datos de una tabla.*
```sql
sis_venta=> SELECT * FROM clientes;
```
___
>*Insertar datos en una columna*.
```sql
sis_venta=> INSERT INTO clientes(nombre_completo) VALUES('Escudero');
``` 
*cuando la columna sea de tipo ``INT`` se debe asignar el valor sin las ``''`` doble y no le asignasmos un valor al campo `cliente_id` porque este se le asigno el comando `SERIAL` donde hace  que su valor sea autoincrementable*.
___

>Ordenar datos en base a una columna.
```sql
SELECT * FROM characters ORDER BY character_id; --ascendente
SELECT * FROM characters ORDER BY character_id DESC; --descendente
```
*La cláusula "ORDER BY character_id" ordena los resultados en base a la columna "character_id". En este caso, los resultados se ordenarán de forma ascendente, es decir, de menor a mayor valor de "character_id".*
___

>*Actualizar datos de una columna.*
```sql
UPDATE characters SET favorite_color='Orange' WHERE id=1;
```
___

>*Eliminar datos de una tabla.*

```sql
sis_venta=> DELETE FROM cliente WHERE nombre_completo='Escudero';
```

*Debemos de tener demasiado cuidado a la hora de querer eliminar los datos de una tabla. Ya que si no especificamos muy bien lo que queremos eliminar con el `WHERE` podemos cometer el error de limpiar toda la tabla con el comando `DELETE FROM cliente`.*
___
>*Eliminar una tabla en especifica.*
```sql
sis_venta=> DROP TABLE cliente;
```
___

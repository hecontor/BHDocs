# DOCUMENTACIÓN BHD 
Para identificar rapidamente tablas, estructuras y campos en multiples bases de datos con los cuales he trabajado en BHD.


## INFORMACION DE CLIENTES
> FENÍX

Actualmente los datos en `Fenix` son los recomendados a la hora de realizar algun reporte, el esquema `DT_CONTACTOS`

| ESQUEMA        | TABLA          | DESCRIPCIÓN                                                                              |
| -------------- | -------------- | -----------------------------------------------------------------------------------------|
| `DT_CONTACTOS` | `CLIENTES`     | ESTA TABLA CONTIENE TODOS LOS CLIENTES TANTO PERSONAS FISICAS COMO PERSONAS JURIDICAS |
| `DT_CONTACTOS` | `PERSONAS`     | ESTA TABLA CONTIENE LA INFORMACIÓN DEL CLIENTE E INFO DE PERONSAS RELACIONADAS CON EL CLIENTE |                         
| `DT_CONTACTOS` | `EMPRESAS`     | ESTA TABLA CONTIENE INFORMACION DE CADA EMPRESA, CLIENTES DE BANCO |

Desde <sub>ORCL</sub> puedes acceder a los datos de producción en fenix sí le agregas el Dblink `@DHW_PREMISA.REGRESS.RDBMS.DEV.US.ORACLE.COM` y en ORCL puedes ver todos los Dblink de orcl en la siguiente tabla : 
``` 
select * from all_db_links;
```
> ORCL

| ESQUEMA        | TABLA          | DESCRIPCIÓN                                                                              |
| -------------- | -------------- | -----------------------------------------------------------------------------------------|
| `EDWIN`        | `TMP_CARTERA`  | ESTA TABLA CONTIENE INFORMACIÓN DEL <sub>CARTERIZADO</sub> y <sub>OFICINA</sub> DE TODOS LOS CLIENTES |
| `DWADMIN`      | `CLIENTES`     | CONTIENE TODOS LOS CLIENTES DE BANCO SIN DINTINCIÓN ALGUNA Y CONSIDERA CLIENTES CONCOMUNADOS, AUNQUE TIENE MENOS COLUMNAS|
| `DWADMIN`      | `PERSONA`      | CONTIENE TODOS INFORMACIÓN PERSONAL DE CADA CLIENTE CON RELACIÓN A LA TABLA `DWADMIN.CLIENTES` (No. Telefonos, Direcciones, Profesión , etc)|




## TRANSACCIONES  
> AS400

Hay muchos de los archivos de AS400 han sido cargados a `ORCL` principalmente al esquema `DWADMIN`, sí consultas con el esquema (dwadmin) y el nombre de la tabla no deberias de tener problemas para conseguirla.

| ESQUEMA     | TABLA          | DESCRIPCIÓN                                                                              |
| ----------- | -------------- | -----------------------------------------------------------------------------------------|
| `BHDPASFIL` | `ACHTRAN`      | ESTA TABLA CONTIENE TODOS LAS TRANSACCIONES <sub>ACH</sub>                               |
| `CAMBIOTRAN`| `FNCPLOG`      | ESTA TABLA CONTIENE TODOS LAS TRANSACCIONES <sub> INTERNA </sub>                         |
| `BHDBREFIL` | `BRTRAN`       | ESTA TABLA CONTIENE TODOS LAS TRANSACCIONES <sub> BANKOFFICE </sub>                      |


Puedes utilizar el siguiente codigo para conocer la estructura de un archivo o tabla de AS400, conocer sus campos, tipos de datos y longitud de los mismos : 

```
select * 
  from DICCIONARIO_AS400
  where trim(long_table_name)='BRTRAN' and TRIM(LIBRARY)='BHDBREFIL';
```
Donde `BRTRAN` es el nombre de archvo o tabla y `BHDBREFIL` el  nombre del esquema.

> ORCL

| ESQUEMA     | TABLA          | DESCRIPCIÓN                                                                              |
| ----------- | -------------- | -----------------------------------------------------------------------------------------|
| `DWADMIN` | `NEPT_REPOSITORIO_TRANSACCIONES`      | CONTIENE TODAS LAS TRANSACCIONES POR CANALES IBP/MBP |
| `CAMBIOTRAN`| `FNCPLOG`      | ESTA TABLA CONTIENE TODOS LAS TRANSACCIONES <sub> INTERNA </sub>                         |
| `BHDBREFIL` | `BRTRAN`       | ESTA TABLA CONTIENE TODOS LAS TRANSACCIONES <sub> BANKOFFICE </sub>                      |


## TABLAS DE DIMENSIONES
>ORCL

| ESQUEMA     | TABLA          | DESCRIPCIÓN                                                                              |
| ----------- | -------------- | -----------------------------------------------------------------------------------------|
| `DWADMIN` | `OFICINA` | CONTIENE INFORMACIÓN REFERENTE A LAS OFICINAS/SUCURSALES |
| `DWADMIN` | `CARTERA` | CONTIENE INFORMACION DE LAS <sub>CARTERAS</sub>  <sub> INTERNA </sub>                         |
| `DWADMIN` | `BRTRAN`  |  <sub> BANKOFFICE </sub>                      |

# DOCUMENTACIÓN BHD 
Para identificar rapidamente tablas, estructuras y campos en multiples bases de datos con los cuales he trabajado en BHD.

## FENÍX
Actualmente los datos en `Fenix` son los recomendados a la hora de realizar algun reporte, el esquema `DT_CONTACTOS`

#### INFORMACION DE CLIENTES
*Investigar origen de esta data*

| ESQUEMA        | TABLA      | DESCRIPCIÓN                                                                                  |
| -------------- | -----------| -------------------------------------------------------------------------------------------- |
| `DT_CONTACTOS` | `CLIENTES` | CONTIENE TODOS LOS CLIENTES TANTO PERSONAS FISICAS COMO PERSONAS JURIDICAS                   |
| `DT_CONTACTOS` | `PERSONAS` | CONTIENE LA INFORMACIÓN DEL CLIENTE E INFO DE PERONSAS RELACIONADAS CON EL CLIENTE           |                         
| `DT_CONTACTOS` | `EMPRESAS` | CONTIENE INFORMACION DE CADA EMPRESA, CLIENTES DE BANCO                                      |

Desde <sub>ORCL</sub> puedes acceder a los datos de producción en fenix sí le agregas el Dblink `@DHW_PREMISA.REGRESS.RDBMS.DEV.US.ORACLE.COM` y en ORCL puedes ver todos los Dblink de orcl en la siguiente tabla : 
``` 
select * from all_db_links;
```
#### DIMENSIONES 
*Investigar origen de esta data*

| ESQUEMA          | TABLA          | DESCRIPCIÓN                                                                                                |
| ---------------- | -------------- | ---------------------------------------------------------------------------------------------------------- |
| `DT_DIMENSIONES` | `DIM_OFICINAS` | CONTIENE INFORMACIÓN REFERENTE A LAS OFICINAS/SUCURSALES                                                   |
| `DT_DIMENSIONES` | `DIM_OFICIALES`| CONTIENE INFORMACIÓN REFERENTE A LOS OFICIALES/GERENTES DE SUCURSALES                                      |


## ORCL
*AGREGAR DESCRIPCION DE ORCL*

#### INFORMACION DE CLIENTES
*Investigar origen de esta data*

| ESQUEMA    | TABLA          | DESCRIPCIÓN                                                                                                                          |
| ---------- | -------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `EDWIN`    | `TMP_CARTERA`  | ESTA TABLA CONTIENE INFORMACIÓN DEL **CARTERIZADO** y **OFICINA** DE TODOS LOS CLIENTES                                               |
| `DWADMIN`  | `CLIENTES`     | CONTIENE TODOS LOS CLIENTES DE BANCO SIN DINTINCIÓN ALGUNA Y CONSIDERA CLIENTES CONCOMUNADOS, AUNQUE TIENE MENOS COLUMNAS             |
| `DWADMIN`  | `PERSONA`      | CONTIENE TODOS INFORMACIÓN PERSONAL DE CADA CLIENTE CON RELACIÓN A LA TABLA `DWADMIN.CLIENTES`(Telefonos, Direcciones, Profesión, etc)|

#### DIMENSIONES
*Investigar origen de esta data*

| ESQUEMA   | TABLA          | DESCRIPCIÓN                                                                                                |
| --------- | -------------- | ---------------------------------------------------------------------------------------------------------- |
| `DWADMIN` | `OFICINA`      | CONTIENE INFORMACIÓN REFERENTE A LAS OFICINAS/SUCURSALES                                                   |
| `DWADMIN` | `OFICIALES`    | CONTIENE INFORMACIÓN REFERENTE A LOS OFICIALES/GERENTES DE SUCURSALES                                      | 
| `DWADMIN` | `UNIDADES`     | *LEVANTAR INFORMACIÓN*                                                                                     |
| `DWADMIN` | `CARTERA`      | CONTIENE INFORMACION DE LAS <sub>CARTERAS</sub>  <sub> INTERNA </sub>                                      | 
| `DWADMIN` | `CAJEROS_ATM`  | DIMENSIÓN DE CADA CAJERO ACTIVO                                                                            |

> TESORERIA
La gestion de La información de ATMs en `ORCL` es manual

| ESQUEMA     | TABLA          | DESCRIPCIÓN                                                                                                |
| ----------- | -------------- | -----------------------------------------------------------------------------------------------------------|
| `TESORERIA` | `CAJEROS`      | DIMENSIÓN HISTORICO DE CADA CAJERO                                                                         |


#### TRANSACCIONES
*Investigar origen de esta data*

| ESQUEMA     | TABLA                            | DESCRIPCIÓN                                                                              |
| ----------- | ---------------------------------| -----------------------------------------------------------------------------------------|
| `DWADMIN`   | `NEPT_REPOSITORIO_TRANSACCIONES` | CONTIENE TODAS LAS TRANSACCIONES POR CANALES IBP/MBP                                     |
| `DWADMIN`   | `TRANSACCIONES_CUENTAS`          | *LEVANTAR INFORMACIÓN*                                                                   |

> TESORERIA
> *Investigar origen de esta data*

| ESQUEMA     | TABLA                            | DESCRIPCIÓN                                                                              |
| ----------- | ---------------------------------| -----------------------------------------------------------------------------------------|
| `TESORERIA` | `TRANSACCIONES_CAJERO`           | CONTIENE LAS TRANSACCIONES POR CAJERO O<sub> ATMs </sub>                                 |

#### PRODUCTOS [TARJETA DE CREDITOS/DEBITO,PRESTAMOS, CERTIDICADOS]
En `SAT` podremos encontrar todo lo referente a ... Y con el Dblink de `Sunrise` podremos acceder a data verificada
*Investigar origen de esta data*

| ESQUEMA     | TABLA          | DESCRIPCIÓN                                                                                                |
| ----------- | -------------- | -----------------------------------------------------------------------------------------------------------|
| `DWADMIN`   | `SAT_TARJETA`  | CONTIENE TODAS LAS TARJETAS YA SEA `TD, TC O TP`, TIPO DE TARJETA EN EL CAMPO `TIPOTARJ`, EL NUMEROD DE CONTRATO ES LA CONCATENACIÓN DE `CENTALTA` Y  `CUENTA` Y ESTÁ HOMOLOGADA CON CLIENTES POR EL CAMPO `NUMDOC` (ES EL DOCUMENTO DEL CLIENTE)|
| `DWADMIN`   | `SAT_CONTRATO` | CONTIENE TODOS LOS CONTRATOS |
| `DWADMIN`   | `TARJETA_CLAVE`| CONTIENE TODAS LAS TARJETAS DE CLAVE DE LOS CLIENTES, HOLOGADAS CON LOS CLIENTES POR EL CAMPO `TJPERS`     |

#### SISTEMAS DE NOMINAS
*Investigar origen de esta data*

| ESQUEMA     | TABLA           | DESCRIPCIÓN                                                                                                                         |
| ----------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `SIEBEL8`   | `S_SRV_REQ`     | `SERVICES REQUEST`, TIENE CADA SOLICITUD DE NOMINA EN **SIEBEL**, ES UN REGISTRO UNICO POR SOLICITUD EL NUMERO DE SOLICITUD `SR_NUM`|
| `SIEBEL8`   | `CX_SR_NOMINA`  | CONTIENE CADA CANDIDATO DE CADA SOLICITÚD EN `SERVICES REQUEST`,SE HOMOLOGAN CON `CX_SR_NOMINA.PAR_ROW_ID = S_SRV_REQ.ROW_ID`       |

## AS400
Hay muchos de los archivos de AS400 han sido cargados a `ORCL` principalmente al esquema `DWADMIN`, sí consultas con el esquema (dwadmin) y el nombre de la tabla no deberias de tener problemas para conseguirla. Esta información proviene directamente de los sistema de `AS400`.

#### TRANSACCIONES 
Esta información proviene directamente de los sistema de `AS400`.

| ESQUEMA     | TABLA          | DESCRIPCIÓN                                                                              |
| ----------- | -------------- | -----------------------------------------------------------------------------------------|
| `BHDPASFIL` | `ACHTRAN`      | ESTA TABLA CONTIENE TODOS LAS TRANSACCIONES **ACH**                                      |
| `CAMBIOTRAN`| `FNCPLOG`      | ESTA TABLA CONTIENE TODOS LAS TRANSACCIONES **INTERNA**                                  |
| `BHDBREFIL` | `BRTRAN`       | ESTA TABLA CONTIENE TODOS LAS TRANSACCIONES **BANKOFFICE**                               |

Puedes utilizar el siguiente codigo para conocer la estructura de un archivo o tabla de AS400, conocer sus campos, tipos de datos y longitud de los mismos : 

```
SELECT * 
  FROM DICCIONARIO_AS400
  WHERE trim(LONG_TABLE_NAME)='BRTRAN';
```
Donde `BRTRAN` es el nombre de *archivo/tabla*, el nombre de la tabla puede repetirse en diferentes *esquemas/librerias*, sí se quiere ser mas preciso puede agregar la libreria : 
``` 
SELECT * 
  FROM DICCIONARIO_AS400
  WHERE TRIM(LONG_TABLE_NAME)='BRTRAN' AND TRIM(LIBRARY)='BHDBREFIL';
``` 
Donde `BHDBREFIL` el  nombre del esquema/libreria.





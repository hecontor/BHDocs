# DOCUMENTACIÓN BHD 
Para identificar rapidamente tablas, estructuras y campos en multiples bases de datos con los cuales he trabajado en BHD.


## INFORMACION DE CLIENTES
> FENÍX

Actualmente los datos en `Fenix` son los recomendados a la hora de realizar algun reporte, el esquema `DT_CONTACTOS`
| TABLA          | DESCRIPCIÓN                                                                              |
| -------------- | -----------------------------------------------------------------------------------------|
| `CLIENTES`     | ESTA TABLA ES CONTIENE TODOS LOS CLIENTES TANTO PERSONAS FISICAS COMO PERSONAS JURIDICAS |
| `PERSONAS`     |                                                     
| `EMPRESAS`     |



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



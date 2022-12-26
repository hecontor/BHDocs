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

Hay muchos de los archivos de AS400 han sido cargados a `ORCL` principalmente al esquema `DWADMIN` 

| TABLA          | DESCRIPCIÓN                                                                              |
| -------------- | -----------------------------------------------------------------------------------------|
| `ACHTRAN`      | ESTA TABLA CONTIENE TODOS LAS TRANSACCIONES ACH                                          |
| `FNCPLOG`      | ESTA TABLA CONTIENE TODOS LAS TRANSACCIONES DE <sub> INTERNA </sub>                      |                                                      
| `BRTRAN`       | ESTA TABLA CONTIENE TODOS LAS TRANSACCIONES DE <sub> BANKOFFICE </sub>                   |


Puedes utilizar el siguiente codigo para conocer la estructura de un archivo o tabla de AS400, conocer sus campos, tipos de datos y longitud de los mismos : 

```
select * 
  from DICCIONARIO_AS400
  where trim(long_table_name)='BRTRAN' and TRIM(LIBRARY)='BHDBREFIL';
```

Donde `BRTRAN` es el nombre de archvo o tabla y `BHDBREFIL` el  nombre del esquema.



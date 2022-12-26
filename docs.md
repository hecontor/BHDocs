# DOCUEMNTACIÓN BHD 
Para identificar rapidamente tablas, estructuras y campos en multiples bases de datos con los cuales he trabajado en BHD.
## INFORMACION DE CLIENTES
> ORCL

Actualmente los datos en `Fenix` son los recomendados a la hora de realizar algun reporte, el esquema `DT_CONTACTOS`
| TABLE NAME     | DESCRIPCIÓN                                                                              |
| -------------- | -----------------------------------------------------------------------------------------|
| `CLIENTES`     | ESTA TABLA ES CONTIENE TODOS LOS CLIENTES TANTO PERSONAS FISICAS COMO PERSONAS JURIDICAS |
```
select * 
  from DICCIONARIO_AS400
  where  trim(long_table_name)='TABLE_NAME_IN_AS400';
```




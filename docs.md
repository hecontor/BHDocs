# DOCUEMNTACIÓN BHD 
Para identificar rapidamente tablas, estructuras y campos en multiples bases de datos con los cuales he trabajado en BHD.
## TARJETAS DE CRÉDITO
###### ORCL
```
select * 
  from DICCIONARIO_AS400
  where  trim(long_table_name)='TABLE_NAME_IN_AS400';
```




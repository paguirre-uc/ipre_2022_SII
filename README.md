# Analisis de datos del SII

**Descripcion: Archivo Jupyter Notebook para analizar las superficies construidas con y sin libneas de construcciones. Solo se necesita poner los path relativos de cada archivo. Si bien esta pensado especificamente para los años 2018 y 2022, el codigo tambien permite analizar cualquier base de datos tipo N_NAC y NL_NAC.**

-------
### Nota 1: Se necesita tener las librerias descargadas de pandas, datatable y numpy
### Nota 2: Todas las funciones tienen un parametro "nombre", prestablecido en False. Si ese parametro se define como un booleano True entonces se reemplazan los codigos de las comunas por sus respectivos nombres. Esto es para hacer los analisis por comuna mas simples al no ser necesario abrir el archivo "estructura_detalle_catastral" y buscar el codigo de comuna con su correspondiente comuna.
-------
### Funciones Definidas:
Funciones definidas para poder hacer mas simple el analisis:

1. ```superficie_nac```: parametros: ```data (tipo datatable, debe ser N_NAC)```, ```fecha```, ```nombre = False```. 
Funcion que deja solo las comunas junto con la suma de las superficies.
2. ```man_pre```: parametros: ```data (tipo datatable, debe ser N_NAC)```, ```fecha```, ```nombre = False```, ```destino = False```. Deja las columnas de Comuna, manzana, predio, direccion, codigo de rol y superficie del terreno. La idea es poder buscar la direccion de un predio, rol y superficie a partir de la comuna, manzana y predio. Si el parametro destino se pone como un booleano True, entonces se remplazan los codigos de rol por sus respectivos nombres.
3. ```codigo_lc```: parametros: ```data (tipo datatable, debe ser NL_NAC)```, ```año```, ```nombre = False```. Muestra la visualizacion de un archivo tipo NL_NAC con los codigos de las lineas de contruccion como columnas, con una columna extra con las sumas de las areas de cada comuna. los datos son metros cuadrados de predio construido por rol
4. ```comparacion_comuna```: parametros: ```data_1 (tipo datatable, debe ser N_NAC)```, ```data_2 (tipo datatable, debe ser N_NAC)```, ```a_a (año de la base mas antigua)```, ```a_n (año de la base mas nueva)```, ```nombre = False```. Agrupa las areas de las superficies por comuna y año, y ademas agrega una columna con una diferencia entre los años.
5. ```comparacion_lc```: parametros: ```data_1 (tipo datatable, debe ser NL_NAC)```, ```data_2 (tipo datatable, debe ser NL_NAC)```, ```a_a (año de la base mas antigua)```, ```a_n (año de la base mas nueva)```, ```nombre = False```, ```negativos = False```. Si el parametro negativos es False, entonces muestra la diferencia entre las areas por rol y comuna de los años especificos. Si el parametro neagtivos es True, entonces muestra las comunas que por lo menos tienen una diferencia entre los años negativa, osea un rol disminuyo con el paso del tiempo.
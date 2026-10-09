## PRESENTACION: DIEGO MONTES

# CASO PRACTIVO
Insumos para Proyecto final de Data Academy Latam - Python
# PAS0 1
Se procedio a cargar los arvichos CSV en un dataframe 
Luego se procedio a cargar un dataframe final "df_restaurantes" y "df_menus"
# PASO 2
En df_restaurantes: 
1. Mapeo de Precios: La columna rango_de_precios contiene símbolos ($, $$, 
etc.). Se utilizó la función .replace() para transformarlos a 
texto legible: 
○ $ -> "Económico" 
○ $$ -> "Moderadamente caro" 
○ $$$ -> "Caro" 
○ $$$$ -> "Muy caro" 
2. Desanidado de Ubicaciones (Split): La columna dirección_completa contiene 
la calle, ciudad, estado y código postal separados por comas. 
Se utilizó el metodo .str.split(',', expand=True) 
Se crearon 3 columnas: calle, ciudad y estado_zip.
Metodo .str.strip() en el campo ciudad para quitar espacios ocultos. 
4. Se eliminó los restaurantes que no tengan puntaje (score nulo) o 
cuyo puntaje sea 0 y estandarizó la columna category a minúsculas.
En df_menus: 
1. La columna price se utilizó la funcion .str.replace() para eliminar el texto " USD",se reemplazo la "," por un punto, 
y casteó el resultado a formato decimal (float). 
2. Se eliminó los ítems del menú con precio igual a 0.0 o nulos.

# Optimización y Cruce (Control de Memoria RAM): 
1. Se filtró df_restaurantes para quedarse únicamente con aquellos que 
tengan más de 100 calificaciones (ratings). 
2. Usando (pd.merge) entre su df_restaurantes filtrado y df_menus 
utilizando el ID del restaurante del cruce se obtuvo DataFrame llamado df_master. 

# Parte 3 - Carga a Base de Datos (Load) 
1. Se importó la librería sqlalchemy y genere un motor (create_engine) para una base de 
datos SQLite local llamada delivery_insights.db. 
2. Se utilizo df_master.to_sql() para cargar su tabla final a la base de datos con el nombre 
master_food_data. Use if_exists="replace" y index=False. 

# Parte 4 - Business Intelligence: Reporte al CEO (SQL + Visualización) 
Se procedió a crear los graficos necesarios para la presentación.

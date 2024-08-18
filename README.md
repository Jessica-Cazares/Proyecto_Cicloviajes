# Análisis Descriptivo de Datos 

# Proyecto Cicloviajes :bike:

El análisis descriptivo de datos es una técnica utilizada en la ciencia de datos para resumir y comprender las características principales de un conjunto de datos. Se enfoca en proporcionar una descripción clara de lo que muestran los datos.

Esto es crucial para el análisis exploratorio inicial, ya que ayuda a los analistas a entender mejor los datos antes de aplicar técnicas más complejas como análisis predictivo o inferencial.


# Temas :bulb:

- [Introducción](#Introducción)
- [Objetivo](#Objetivo)
- [Procesamiento y análisis](#Procesamiento-y-análisis)
- [Herramientas](#Herramientas)
- [Lenguajes](#Lenguajes)
- [Ficha técnica](/Ficha_técnica/README.md)
- [Dashboard](/Dashboard/README.md)
- [Presentación](/Presentación/README.md)


## Introducción 

En este proyecto se realizó un análisis exploratorio de datos a partir de un conjunto de datos (dataset) sobre el uso de un programa de bicicletas compartidas. Para responder las preguntas del negocio.

## Objetivo

**1. Realizar un análisis descriptivo de datos.**

**2. Calcular métricas de uso de un día promedio.**
   * Número de viajes que se realizan en promedio en un día.
   * Calcular las medidas de dispersión: valor máximo, valor mínimo, promedio y desviación estándar de la duración de un viaje.

**3. Calcular métricas históricas.**
   * Calcular el total de viajes realizados.
   * Analizar el crecimiento del número de viajes diarios a lo largo del tiempo.
   * Analizar el total de viajes por usuarios, según género, edad y/o tipo de suscripción.

**4. Crear reporte, dashboard con visualizaciones del resumen del análisis.**

**5. Presentar conclusiones generales, patrones y recomendaciones al nuevo CEO.**

## Procesamiento y análisis

__Conectar/Importar Datos a Otras Herramientas__
- Se creó el proyecto reto-tecnico y el conjunto de datos **Dataset** en **BigQuery**.
- Tablas importadas: `citi_bike_trip`.

__1. Identificar y Manejar Valores Nulos__
- Se identifican valores nulos a través de comandos SQL `COUNTIF`, `IS NULL`.
  - **birth_year**: Se identificaron 4,639 valores nulos. Estos datos representan el 9.27% del total, por lo que no serán considerados en el análisis.
  - **customer_plan**: Se identificaron 50,000 valores nulos. Esta variable tiene el 100% de datos nulos, por lo que será excluida del análisis.

__2. Identificar y Manejar Valores Duplicados__
- Se identifican duplicados a través de comandos SQL `COUNT`, `GROUP BY`, `HAVING`.
  - No se encontraron valores duplicados en las variables.

__3. Identificar y Manejar Datos Fuera del Alcance del Análisis__
- Se manejan variables que no son útiles para el análisis a través de comandos SQL `SELECT EXCEPT`.
  - Se excluye la variable **customer_plan**.
  - Al analizar la variable **birth_year**, se observó que hay 32 usuarios con un rango de edad entre 103 - 139 años, por lo que no serán considerados en el análisis.

- Se creó una nueva consulta para excluir los valores nulos de la variable **birth_year** y excluir la variable **customer_plan**, quedando un total de 42,651 registros.

__4. Crear Nuevas Variables__
- Se creó la variable `tripduration_min` transformando la variable `tripduration` de segundos a minutos.
- Se creó la variable `stopdate` extrayendo la fecha de la variable `stoptime` usando el comando `DATE`.
- Se creó la variable `age` para los usuarios, usando los comandos `EXTRACT(YEAR FROM CURRENT_DATE()) - birth_year`.

__5. Unir Tablas__
- Se creó una vista con la unión de las consultas anteriores, considerando las variables que se crearon y excluyendo las que no son relevantes para el análisis.

Este proceso es fundamental para asegurar la calidad y precisión del análisis subsiguiente. 

## Herramientas

* Google BigQuery
* Google Looker Studio
* Google Docs
* Google Slide

## Lenguajes

* SQL

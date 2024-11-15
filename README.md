**Proyecto de Limpieza de Datos de Airbnb NYC 2019**

**Realizado por: Carolina Pérez Molina**

Este proyecto tiene como objetivo realizar una limpieza exhaustiva del dataset de Airbnb de Nueva York de 2019, eliminando inconsistencias, valores nulos y valores atípicos para poder realizar un análisis más preciso y confiable.

**Descripción del Dataset**

El dataset contiene listados de Airbnb en Nueva York y está compuesto por 16 columnas que incluyen información sobre la ubicación, precios, disponibilidad y reseñas de cada propiedad.

**Columnas Principales**
- **id**: Identificador único de la propiedad.
- **name**: Nombre de la propiedad.
- **host_id** y **host_name**: Identificador y nombre del anfitrión.
- **neighbourhood_group** y **neighbourhood**: Ubicación general y específica de la propiedad.
- **latitude** y **longitude**: Coordenadas geográficas.
- **room_type**: Tipo de habitación.
- **price**: Precio por noche.
- **availability_365**: Días de disponibilidad al año.

**Problemas Detectados**

Durante la revisión del dataset, se identificaron los siguientes problemas:
1. Valores nulos en columnas como `name`, `host_name`, y `reviews_per_month`.
2. Valores extremos en la columna `price`, lo que afecta los análisis de precios.
3. Duplicados en el nombre de propiedades (`name`).
4. Valores de `availability_365` igual a 0 en múltiples registros.
5. Formato de fecha inconsistente en la columna `last_review`.

**Pasos de Limpieza Realizados**

1. **Relleno de valores nulos**:
   - Los valores nulos en `name` y `host_name` fueron rellenados con `"Unknown"`.
   - Los valores nulos en `reviews_per_month` se rellenaron con `0` para indicar listados sin reseñas.

2. **Filtrado de valores extremos**:
   - Se estableció un límite superior en `price` para eliminar valores extremos (por encima del percentil 99).

3. **Eliminación de duplicados**:
   - Se eliminaron duplicados en `name`, reteniendo el primer registro de cada nombre.

4. **Revisión de disponibilidad**:
   - Se analizó la columna `availability_365` para identificar propiedades con disponibilidad igual a 0, lo cual se documentó para análisis adicionales.
   - Durante la limpieza, se agregó una nueva columna llamada `is_available` en el DataFrame `data_clean`. Esta columna es de tipo binario y marca si una propiedad está disponible o no en función del valor de `availability_365`. Las propiedades con `availability_365` igual a `0` se consideran "No Disponibles", mientras que las demás se consideran "Disponibles".
   
5. **Conversión de `last_review` a formato de fecha**:
   - La columna `last_review` fue convertida al formato de fecha (`datetime`) para facilitar el análisis temporal.

**Resultados**

Después de la limpieza, el dataset contiene datos consistentes y está listo para análisis más profundos. Esta limpieza permite explorar la relación entre precio, disponibilidad y otros factores sin que los valores faltantes o extremos distorsionen los resultados.

**Conclusión**

Este trabajo proporciona una base sólida para el análisis de los listados de Airbnb en Nueva York en 2019. Con el dataset limpio, se puede continuar explorando tendencias de precios, patrones de disponibilidad, y otros insights relevantes del mercado de alquileres temporales en la ciudad.
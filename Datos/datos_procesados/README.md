# Datos procesados

Salida de cada etapa del análisis, una subcarpeta por etapa. Cada una tiene su `diccionario.txt` con la descripción de cada columna.

| Carpeta | Archivo | Qué es | Notebook que lo genera |
|---|---|---|---|
| `concatenacion/` | `concatenacion_2009-2024.zip.001` a `.003` | Las seis elecciones en un solo archivo (3.1 GB), comprimido y partido en tres partes | `notebooks/concatenacion/` |
| `limpieza/` | `base_limpia.zip` | Una fila por elección, municipio, sexo, rango de edad y tipo de sección (540,024 filas, 2,475 municipios) | `notebooks/limpieza/` |
| `tratamiento/` | `base_tratada.zip` | La base limpia con variables de texto convertidas a columnas de 0 y 1; es la que leen los modelos | `notebooks/tratamiento/` |
| `modelo/` | `pronostico_2027.csv` | Abstención pronosticada 2027, semáforo y confianza por municipio | `notebooks/modelo/pronostico_2027.ipynb` |
| `modelo/` | `escenarios_2027.csv` | Escenarios con intervención de 1 a 5 puntos, prioridad y personas adicionales | `notebooks/modelo/escenarios_2027.ipynb` |

Los `.zip` contienen un `.csv` con el mismo nombre; se comprimen porque cada CSV pesa unos 49 MB.

Las tres partes de `concatenacion/` deben unirse antes de descomprimir (el comando está en el [README principal](../../README.md#archivos-grandes)).

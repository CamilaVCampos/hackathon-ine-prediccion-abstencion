# Hackea la participación: Reto 2, Predicción y escenarios de riesgo de abstención

Proyecto del equipo **CamposB** para el hackatón *Hackea la participación: Datos que construyen democracia* (INE-DECEyEC, 2026).
Modelo simple que pronostica la abstención de cada municipio para la elección federal de 2027, la traduce en un semáforo de riesgo y compara escenarios sin y con una intervención hipotética.

Tablero interactivo: <https://public.tableau.com/views/RiesgodeAbstencin2027/Dashboard1>

## Estructura
| Carpeta | Contenido |
|---|---|
| `Datos/datos_ine/` | Conteos Censales de Participación Ciudadana 2009-2024, un `.zip` por elección (ver su [README](Datos/datos_ine/README.md)) |
| `Datos/datos_procesados/` | Tablas de cada etapa (`concatenacion/`, `limpieza/`, `tratamiento/`, `modelo/`), cada una con su `diccionario.txt` |
| `Datos/mapa/` | Marco Geoestadístico 2025 de INEGI (se descarga aparte; no se versiona) |
| `notebooks/` | Código, una subcarpeta por etapa (ver el orden abajo) |
| `Entregables/` | Lo que se entrega al INE, una subcarpeta por entregable (ver abajo) |
| `Administrativo/` | Convocatoria, rúbrica, cartas firmadas y copia del reporte en Word. Es privada y no se sube a git |

## Entregables
| Carpeta | Contenido |
|---|---|
| `Entregables/reporte/` | Reporte metodológico y preventivo (`reporte.pdf`, 15 páginas) |
| `Entregables/presentacion/` | Presentación ejecutiva en PDF (10 diapositivas) |
| `Entregables/mapa_escenarios/` | Mapa de escenarios: `mapa_escenarios_2027.geojson` y `diccionario_mapa_2027.csv` (el tablero está en el enlace de arriba) |
| `Entregables/base_anonimizada/` | Base anonimizada: `base_limpia.zip` (contiene `base_limpia.csv`), `escenarios_2027.csv` y sus diccionarios (`diccionario_base_limpia.txt` y `diccionario_escenarios_2027.txt`) |

Son copias de los archivos de `Datos/datos_procesados/`. Los datos son conteos agregados por grupo (municipio, sexo, rango de edad y tipo de sección) y no permiten identificar a ninguna persona.

## Datos del INE
Los datos originales vienen de la
[Plataforma CCPC](https://ine.mx/transparencia/datos-abiertos/visualizacion-datos/conteos-censales-participacion/).
Están en `Datos/datos_ine/` como un `.zip` por elección (291 MB en total, 3.5 GB sin comprimir).
Para usarlos, descomprímelos en esa misma carpeta; las instrucciones y la descripción de los campos están en
[Datos/datos_ine/README.md](Datos/datos_ine/README.md).

## Orden de los notebooks
Cada notebook lee la salida del anterior. Las rutas se calculan desde la raíz del proyecto, así que pueden ejecutarse desde cualquier carpeta.

| # | Notebook | Qué hace | Salida |
|---|---|---|---|
| 1 | `notebooks/concatenacion/concatenacion_2009-2024.ipynb` | Une los CSV de las seis elecciones | `Datos/datos_procesados/concatenacion/concatenacion_2009-2024.csv` |
| 2 | `notebooks/eda/eda.ipynb` | Exploración de los datos | (gráficas) |
| 3 | `notebooks/limpieza/limpieza.ipynb` | Limpieza, nombres de municipios unificados y abstención | `Datos/datos_procesados/limpieza/base_limpia.csv` |
| 4 | `notebooks/series/series.ipynb` | Series por municipio: persistencia y volatilidad | (gráficas) |
| 5 | `notebooks/tratamiento/tratamiento.ipynb` | Variables de texto a columnas de 0 y 1 | `Datos/datos_procesados/tratamiento/base_tratada.csv` |
| 6 | `notebooks/pruebas/comparacion_modelos.ipynb` | Comparación de 13 modelos y reglas con validación hacia atrás | (tablas) |
| 7 | `notebooks/modelo/pronostico_2027.ipynb` | Pronóstico 2027, semáforo y confianza | `Datos/datos_procesados/modelo/pronostico_2027.csv` |
| 8 | `notebooks/modelo/escenarios_2027.ipynb` | Escenarios con intervención de 1 a 5 puntos | `Datos/datos_procesados/modelo/escenarios_2027.csv` |
| 9 | `notebooks/modelo/mapa_geojson.ipynb` | Une los escenarios con los polígonos municipales de INEGI | `Entregables/mapa_escenarios/mapa_escenarios_2027.geojson` |

El notebook 9 necesita el archivo `mg_2025_integrado.zip` del Marco Geoestadístico Integrado 2025 de INEGI en `Datos/mapa/`.

## Archivos grandes
- `base_limpia.csv` y `base_tratada.csv` pesan unos 49 MB cada uno, así que en el repositorio están comprimidos: `Datos/datos_procesados/limpieza/base_limpia.zip`, `Datos/datos_procesados/tratamiento/base_tratada.zip` y `Entregables/base_anonimizada/base_limpia.zip`. Descomprímelos en su misma carpeta para usarlos. Los notebooks también los regeneran.
- `concatenacion_2009-2024.csv` (3.1 GB) y `Datos/mapa/` (5.6 GB) no se suben; el primero se regenera con el notebook 1 y el segundo se descarga de INEGI.
- Las rutas que aparecían en las salidas de los notebooks se reemplazaron por `<raiz>`.

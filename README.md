# Hackea la participación: Reto 2, Predicción y escenarios de riesgo de abstención

Proyecto para el hackatón *Hackea la participación: Datos que construyen democracia* (INE-DECEyEC, 2026).
Modelo simple de riesgo de abstención por territorio, con escenarios sin y con intervención.

## Estructura
| Carpeta | Contenido |
|---|---|
| `Datos/datos_ine/` | Conteos Censales de Participación Ciudadana 2009-2024, un `.zip` por elección (ver su [README](Datos/datos_ine/README.md)) |
| `Datos/datos_procesados/` | Tablas intermedias (CSV concatenado y diccionario de municipios) |
| `notebooks/concatenacion/` | Une los CSV del INE en un solo archivo |
| `notebooks/eda/` | Exploración de los datos |
| `notebooks/limpieza/` | Limpieza y agregación por municipio |
| `Entregables/` | Lo que se entrega al INE, una subcarpeta por entregable (ver abajo) |

## Entregables
| Carpeta | Contenido |
|---|---|
| `Entregables/1_reporte/` | Reporte metodológico y preventivo (PDF, 10 a 15 cuartillas) |
| `Entregables/2_presentacion/` | Presentación ejecutiva (máximo 10 diapositivas) |
| `Entregables/3_mapa_escenarios/` | Mapa de escenarios con y sin intervención (tablero o SHP/GeoJSON/GPKG) |
| `Entregables/4_base_anonimizada/` | Base de datos anonimizada empleada en el análisis (CSV) |

El código es el de `notebooks/`. Las cartas firmadas se guardan en `administrativo/` (privada, no se sube) y se agregan al `.zip` final.

## Datos del INE
Los datos originales vienen de la
[Plataforma CCPC](https://ine.mx/transparencia/datos-abiertos/visualizacion-datos/conteos-censales-participacion/).
Están en `Datos/datos_ine/` como un `.zip` por elección (291 MB en total, 3.5 GB sin comprimir).
Para usarlos, descomprímelos en esa misma carpeta; las instrucciones y la descripción de los campos están en
[Datos/datos_ine/README.md](Datos/datos_ine/README.md).

## Orden de los notebooks
1. `notebooks/concatenacion/concatenacion_2009-2024.ipynb`: genera `Datos/datos_procesados/concatenacion_2009-2024.csv`.
2. `notebooks/eda/eda.ipynb`: exploración de ese CSV.
3. `notebooks/limpieza/limpieza.ipynb`: genera la base anonimizada por municipio (`Entregables/4_base_anonimizada/base_anonimizada_abstencion.csv`) y el diccionario de municipios (`Datos/datos_procesados/diccionario_municipios.csv`).

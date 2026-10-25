# Hackea la participación: Reto 2, Predicción y escenarios de riesgo de abstención

Proyecto para el hackatón *Hackea la participación: Datos que construyen democracia* (INE-DECEyEC, 2026).
Modelo simple de riesgo de abstención por territorio, con escenarios sin y con intervención.

## Estructura
| Carpeta | Contenido |
|---|---|
| `Datos/datos_ine/` | Conteos Censales de Participación Ciudadana 2009-2024, un `.zip` por elección (ver su [README](Datos/datos_ine/README.md)) |
| `Datos/datos_procesados/` | Tablas consolidadas y base anonimizada |
| `notebooks/concatenacion/` | Une los CSV del INE en un solo archivo |
| `notebooks/eda/` | Exploración de los datos |
| `notebooks/limpieza/` | Limpieza y agregación por municipio |
| `src/` | Código reproducible |
| `salidas/` | Mapas y tablas de resultados |
| `reporte/`, `presentacion/` | Documentos de entrega |

## Datos del INE
Los datos originales vienen de la
[Plataforma CCPC](https://ine.mx/transparencia/datos-abiertos/visualizacion-datos/conteos-censales-participacion/).
Están en `Datos/datos_ine/` como un `.zip` por elección (291 MB en total, 3.5 GB sin comprimir).
Para usarlos, descomprímelos en esa misma carpeta; las instrucciones y la descripción de los campos están en
[Datos/datos_ine/README.md](Datos/datos_ine/README.md).

## Orden de los notebooks
1. `notebooks/concatenacion/concatenacion_2009-2024.ipynb`: genera `Datos/datos_procesados/concatenacion_2009-2024.csv`.
2. `notebooks/eda/eda.ipynb`: exploración de ese CSV.
3. `notebooks/limpieza/limpieza.ipynb`: genera la base limpia por municipio (`base_limpia.csv`) y el diccionario de municipios.

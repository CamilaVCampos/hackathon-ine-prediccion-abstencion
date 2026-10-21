# Hackea la participación: Reto 2, Predicción y escenarios de riesgo de abstención

Proyecto para el hackatón *Hackea la participación: Datos que construyen democracia* (INE-DECEyEC, 2026).
Modelo simple de riesgo de abstención por territorio, con escenarios sin y con intervención.

## Estructura
| Carpeta | Contenido |
|---|---|
| `Datos/datos_ine/` | Conteos Censales de Participación Ciudadana 2009-2024 y PJ 2025 (no se versionan; ver abajo) |
| `Datos/datos_externos/` | Fuentes públicas adicionales (Censo 2020, CONEVAL, límites municipales) |
| `Datos/datos_procesados/` | Tablas consolidadas y base anonimizada |
| `notebooks/` | Exploración y pruebas del modelo |
| `src/` | Código reproducible |
| `salidas/` | Mapas y tablas de resultados |
| `reporte/`, `presentacion/` | Documentos de entrega |

## Datos del INE
Los datos originales se descargan de la
[Plataforma CCPC](https://ine.mx/transparencia/datos-abiertos/visualizacion-datos/conteos-censales-participacion/)
y se colocan en `Datos/datos_ine/`, una subcarpeta por elección.

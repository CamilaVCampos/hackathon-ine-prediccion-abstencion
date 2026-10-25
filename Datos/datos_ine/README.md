# Datos del INE: Conteos Censales de Participación Ciudadana 2009-2024

Datos abiertos del INE (DECEyEC) sobre la participación en las elecciones federales de 2009, 2012, 2015, 2018, 2021 y 2024, construidos a partir de los cuadernillos de la lista nominal de las casillas. Fuente original:
[Plataforma CCPC](https://ine.mx/transparencia/datos-abiertos/visualizacion-datos/conteos-censales-participacion/).

Los archivos son los originales del INE, sin modificar, comprimidos por elección para que quepan en el repositorio (sin comprimir pesan 3.5 GB).

## Contenido
| Archivo | Elección | Tamaño comprimido | Tamaño sin comprimir |
|---|---|---|---|
| `DatosAbiertos_DECEyEC_ConteosCensales2009.zip` | 5 de julio de 2009 | 41 MB | 587 MB |
| `DatosAbiertos_DECEyEC_ConteosCensales2012.zip` | 1 de julio de 2012 | 40 MB | 580 MB |
| `DatosAbiertos_DECEyEC_ConteosCensales2015.zip` | 7 de junio de 2015 | 43 MB | 613 MB |
| `DatosAbiertos_DECEyEC_ConteosCensales2018.zip` | 1 de julio de 2018 | 43 MB | 623 MB |
| `DatosAbiertos_DECEyEC_ConteosCensales2021.zip` | 6 de junio de 2021 | 45 MB | 635 MB |
| `DatosAbiertos_DECEyEC_ConteosCensales2024.zip` | 2 de junio de 2024 | 80 MB | 688 MB |

Cada zip contiene una carpeta con 33 archivos: 32 CSV (uno por entidad federativa) y un `.txt` con la descripción de los campos.

## Cómo usarlos
Descomprime los seis zips **dentro de esta misma carpeta** (`Datos/datos_ine/`, "Extraer aquí"). Quedará una subcarpeta por elección, que es la estructura que lee
`notebooks/concatenacion/concatenacion_2009-2024.ipynb` (`Datos/datos_ine/*/*.csv`):

```
Datos/datos_ine/
├── DatosAbiertos_DECEyEC_ConteosCensales2009/
│   ├── 01_descripcioncampos_conteoscensales2009.txt
│   ├── datosabiertos_deceyec_conteoscensales2009_ags.csv
│   └── ... (32 entidades)
├── DatosAbiertos_DECEyEC_ConteosCensales2012/
└── ... (2015, 2018, 2021, 2024)
```

Las carpetas descomprimidas no se versionan (están en `.gitignore`); solo los `.zip`.

## Campos
Cada fila es un grupo de personas: sección electoral × sexo × edad × elección.

| Campo | Descripción |
|---|---|
| `AELEC` | Año de la elección |
| `FELECCION` | Fecha de la jornada electoral (formato corto) |
| `EDOCVE`, `EDONOM` | Clave y nombre de la entidad federativa |
| `MPIOCVE`, `MPIONOM` | Clave y nombre del municipio |
| `SECCION` | Sección electoral en el año correspondiente |
| `TIPOSEC` | Tipo de sección: U urbana, M mixta, R rural |
| `DEF` | Distrito Electoral Federal (marco cartográfico de la DERFE 2023) |
| `DEL` | Distrito Electoral Local (marco cartográfico de la DERFE 2023) |
| `SEXO` | 0 hombres, 1 mujeres, 2 no binario |
| `EDAD` | Años cumplidos al día de la elección |
| `LN` | Lista nominal de los cuadernillos de todas las casillas catalogadas |
| `SV` | Registros con marca de voto |
| `NV` | Registros sin marca de voto |
| `NS` | Registros no especificados (cuadernillo sin marcas, cuadernillo no disponible o página no disponible) |

`LN = SV + NV + NS`. La descripción oficial completa está en el `.txt` de cada carpeta.

## Cosas a tener en cuenta
- La participación se calcula de los cuadernillos de las casillas aprobadas: **no incluye** a quienes votaron en casillas especiales ni a las y los mexicanos residentes en el extranjero.
- La sección corresponde al domicilio de la credencial, por lo que los datos pueden diferir de los cómputos distritales.
- `FELECCION` no tiene el mismo formato en todos los años: 2009 a 2021 vienen día/mes/año y 2024 viene mes/día/año.
- `DEF` viene vacío (un espacio en blanco) en algunas secciones de 2009 y 2012.
- La Ciudad de México aparece como `DISTRITO FEDERAL` en 2009-2018 y como `CIUDAD DE MEXICO` en 2021 y 2024.
- Los nombres de algunos municipios cambian o tienen errores de escritura entre años. El diccionario de unificación está en `notebooks/limpieza/limpieza.ipynb`.

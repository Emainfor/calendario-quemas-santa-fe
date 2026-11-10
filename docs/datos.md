# Datos

Los datos **no** se incluyen en el repositorio. Este documento indica su origen, cómo reproducir la
descarga y cómo ubicarlos para trabajar.

## Fuente

NASA FIRMS, descarga de archivo: <https://firms.modaps.eosdis.nasa.gov/download/>
(requiere una cuenta gratuita de Earthdata Login).

## Parámetros de la descarga

- **Área:** polígono personalizado sobre la provincia de Santa Fe (coordenadas más abajo).
- **Período:** 2012-01-01 a 2026-10-01 (NOAA-21: pedido hasta 2026-11-01; se recorta al mismo período).
- **Formato:** CSV.

| Fuente en FIRMS | Instrumento / satélite | Prefijo del archivo dentro del ZIP |
|---|---|---|
| MODIS C6.1 | Terra y Aqua combinados (1 km) | `DL_FIRE_M-C61_<id>` |
| J1 VIIRS C2 | NOAA-20 (375 m) | `DL_FIRE_J1V-C2_<id>` |
| SUOMI VIIRS C2 | S-NPP (375 m) | `DL_FIRE_SV-C2_<id>` |
| J2 VIIRS C2 | NOAA-21 (375 m) | `DL_FIRE_J2V-C2_<id>` |

`<id>` es el identificador del pedido en la cuenta de quien descarga; cambia en cada pedido.

### Polígono (WKT, longitud latitud)

```
POLYGON((-58.90715 -28.03968,-58.92912 -28.13856,-59.78605 -30.94007,-60.24748 -31.4784,
-60.57707 -31.76405,-60.71989 -32.76381,-60.08268 -32.98353,-60.46721 -33.63173,
-60.85173 -33.55482,-61.69767 -34.3788,-62.90617 -34.32386,-61.74162 -32.86268,
-62.33488 -31.82997,-61.81852 -30.76429,-62.14811 -30.41273,-61.68669 -27.95179,
-58.90715 -28.03968))
```

Rectángulo envolvente: latitud −34,38 a −27,95; longitud −62,91 a −58,91. El polígono es una
aproximación de la provincia y no coincide exactamente con su límite oficial. Las zonas de análisis
se recortan después, en el procesamiento.

## Ubicación local

Descomprimir cada ZIP en su propia subcarpeta de `datos/` (ignorada por Git):

```
datos/
  modis/
  viirs_noaa20/
  viirs_noaa21/
  viirs_snpp/
```

## Contenido de cada ZIP

- `fire_archive_*`: datos estándar, de calidad científica.
- `fire_nrt_*`: datos en tiempo casi real (NRT) para los meses más recientes.
- `Readme.txt`: aviso de NASA, forma de cita y descargo de responsabilidad.

## Columnas

Archivo estándar de VIIRS:

`latitude, longitude, brightness, scan, track, acq_date, acq_time, satellite, instrument,
confidence, version, bright_t31, frp, daynight, type`

Observaciones verificadas sobre los archivos descargados:

- El archivo **NRT no incluye la columna `type`**; el estándar sí.
- `acq_time` es texto `HHMM` en hora UTC; debe leerse como texto para conservar los ceros iniciales.
- En VIIRS, `confidence` es una letra (`l`, `n`, `h`); en MODIS es un valor numérico de 0 a 100.
- En MODIS, `satellite` indica `Terra` o `Aqua`; en VIIRS, `SNPP`, `N20` o `N21`.
- El estándar tiene un retraso de unos 5 meses; los meses recientes provienen del archivo NRT.

## Advertencias de NASA (resumen)

- Puede haber huecos y algún dato erróneo.
- Los datos no se recomiendan para decisiones tácticas ni a escala local.
- Los datos NRT se reemplazan por datos estándar con el tiempo.

El texto completo figura en el `Readme.txt` de cada ZIP.

## Credenciales

La clave de la API de FIRMS (`MAP_KEY`) y las credenciales de Earthdata **no** se versionan nunca.
Se mantienen fuera del repositorio o en archivos ignorados por Git (`.env`, `clave_firms.txt`).

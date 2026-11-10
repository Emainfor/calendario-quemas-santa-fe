# Datos

Los datos **no** se suben al repositorio. Este documento explica de dónde vienen y cómo
colocarlos para trabajar.

## Fuente

NASA FIRMS — descarga de archivo: <https://firms.modaps.eosdis.nasa.gov/download/>
(requiere cuenta gratuita de Earthdata Login).

## Pedidos realizados

Área: polígono personalizado sobre la provincia de Santa Fe.
Período solicitado: 2012-01-01 a 2026-10-01. Formato: CSV.

| Fuente en FIRMS | Sensor | Nombre del archivo dentro del ZIP |
|---|---|---|
| MODIS C6.1 | Terra y Aqua combinados | `DL_FIRE_M-C61_<id>` |
| J1 VIIRS C2 | NOAA-20 (375 m) | `DL_FIRE_J1V-C2_<id>` |
| SUOMI VIIRS C2 | S-NPP (375 m) | `DL_FIRE_SV-C2_<id>` |

## Cómo colocarlos

Descomprimir cada ZIP en su propia subcarpeta, dentro de `datos/` (carpeta ignorada por Git):

```
datos/
  modis/
  viirs_noaa20/
  viirs_snpp/
```

## Qué trae cada ZIP

- `fire_archive_*`: datos de calidad científica (estándar).
- `fire_nrt_*`: datos en tiempo casi real (NRT) para los meses más recientes.
- `Readme.txt`: aviso de NASA, cita y descargo de responsabilidad.

## Columnas (VIIRS, archivo estándar)

`latitude, longitude, brightness, scan, track, acq_date, acq_time, satellite, instrument,
confidence, version, bright_t31, frp, daynight, type`

Notas verificadas sobre los archivos descargados:

- El archivo **NRT no trae la columna `type`**; el estándar sí.
- `acq_time` viene como texto `HHMM` (hora UTC). Hay que leerlo como texto para no perder ceros.
- En VIIRS, `confidence` es una letra (`l`, `n`, `h`). En MODIS se espera un valor numérico de
  0 a 100 *(a confirmar al abrir el archivo de MODIS)*.
- El polígono descargado cubre más área que la zona de interés, por lo que hay que recortar.

## Advertencias de NASA (resumen)

- Puede haber huecos de datos y algún dato erróneo.
- Los datos no se recomiendan para decisiones tácticas ni a escala local.
- Los datos NRT se reemplazan por datos estándar con un retraso de unos 5 meses.

Texto completo en el `Readme.txt` incluido en cada ZIP.

## Claves y credenciales

La clave de la API de FIRMS (`MAP_KEY`) y las credenciales de Earthdata **nunca** se suben al
repositorio. Se guardan fuera del repositorio o en `clave_firms.txt` (ignorado por Git).

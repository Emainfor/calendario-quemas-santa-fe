# Calendario de actividad de quemas armonizado — Santa Fe (MODIS + VIIRS)

**NASA Space Apps Challenge 2026 · Sede Rosario (Argentina) · Desafío: *Harmonization of MODIS and VIIRS Hot Spots***

> **Estado: preparación.** Este repositorio contiene documentación y estructura. No contiene código de
> análisis ni de aplicación: ese trabajo se realiza durante el evento (14 y 15 de noviembre de 2026).
>
> **Status: preparation.** This repository contains documentation and structure only. No analysis or
> application code is included; that work is carried out during the event (14–15 November 2026).

---

## Contenido / Contents

1. [El problema](#1-el-problema--the-problem)
2. [Qué se construirá](#2-qué-se-construirá--what-will-be-built)
3. [Área de interés](#3-área-de-interés--area-of-interest)
4. [Datos](#4-datos--data)
5. [Método](#5-método--method)
6. [Cómo ejecutarlo](#6-cómo-ejecutarlo--how-to-run)
7. [Limitaciones](#7-limitaciones--limitations)
8. [Uso previsto](#8-uso-previsto--intended-use)
9. [Uso de inteligencia artificial](#9-uso-de-inteligencia-artificial--ai-use)
10. [Créditos y licencia](#10-créditos-y-licencia--credits-and-license)

## 1. El problema / The problem

Los satélites de la NASA registran focos de calor activos desde hace más de dos décadas, pero el
registro está repartido entre instrumentos distintos (MODIS, de 1 km de resolución, y VIIRS, de 375 m)
cuyos conteos no son directamente comparables. Si se unen sin corregir, la actividad de quemas puede
parecer aumentar solo porque cambió el instrumento.

NASA satellites have tracked active fire hotspots for over two decades, but the record is split across
instruments (MODIS, 1 km; VIIRS, 375 m) whose counts are not directly comparable. Joining them without
correction can make burning activity appear to rise simply because the instrument changed.

## 2. Qué se construirá / What will be built

Una aplicación web que armonice ambos registros en un **calendario de actividad de quemas** para un
área de interés, que permita:

- explorar patrones históricos;
- identificar días y semanas inusuales respecto de una línea base;
- detectar períodos críticos, con la incertidumbre siempre visible.

*A web application that harmonizes both records into a burning-activity calendar for an area of
interest, supporting historical exploration, detection of unusual days or weeks against a baseline,
and identification of critical periods, with uncertainty always shown.*

## 3. Área de interés / Area of interest

Provincia de Santa Fe (Argentina). Los datos se descargaron con un polígono que cubre la provincia
(ver [`docs/datos.md`](docs/datos.md)); las zonas de análisis (por ejemplo, Zona Núcleo y norte
santafesino) se recortan después, durante el desarrollo.

**Limitación conocida:** el contorno del polígono es una aproximación y puede no coincidir con el
límite provincial. La cobertura del Delta del Paraná, del lado entrerriano, no está garantizada.

## 4. Datos / Data

Fuente: **NASA FIRMS** (Fire Information for Resource Management System). Detecciones activas de
incendios de MODIS Collection 6.1 (Terra y Aqua) y VIIRS 375 m (S-NPP y NOAA-20), período
2012-01-01 a 2026-10-01.

Columnas, advertencias y forma de reproducir la descarga: [`docs/datos.md`](docs/datos.md).

**Cita / Citation:** se sigue la política de uso de datos de Earthdata
(<https://www.earthdata.nasa.gov/engage/open-data-services-software-policies/data-use-policy>).

> Los datos **no** se incluyen en este repositorio. Se descargan desde FIRMS y se ubican en la carpeta
> local `datos/`, ignorada por Git.

## 5. Método / Method

*A completar durante el evento. / To be completed during the event.*

## 6. Cómo ejecutarlo / How to run

*A completar durante el evento. / To be completed during the event.*

Entorno previsto: Python 3.13 con pandas, pyarrow, plotly y streamlit.

## 7. Limitaciones / Limitations

Se conocen de antemano y se mantendrán visibles en la aplicación:

- **La ausencia de observación no equivale a ausencia de fuego.** Los huecos en los datos no son ceros.
- **Los valores armonizados son estimaciones**, con un margen de incertidumbre, no mediciones directas.
- **S-NPP dejó de entregar datos nuevos el 2 de noviembre de 2026**, y las misiones MODIS (Terra y
  Aqua) se acercan al final de su vida útil; NOAA-20 aporta continuidad.
- **Los meses más recientes provienen de datos en tiempo casi real (NRT)**, que luego son reemplazados
  por datos estándar y pueden cambiar.
- NASA indica que, por su resolución espacial, estos datos **no son recomendables para decisiones
  tácticas ni para condiciones a escala local**. La herramienta apunta a la **planificación estacional
  y regional**, no a alertas por parcela.

## 8. Uso previsto / Intended use

Apoyo a la planificación estacional (cosecha, logística y transporte) en zonas agroindustriales de la
región. *Este uso está pendiente de validación con actores del sector; no constituye un requerimiento
confirmado.*

## 9. Uso de inteligencia artificial / AI use

Durante la preparación se utilizó un asistente de IA (Claude, de Anthropic) para organizar el plan de
trabajo y redactar la documentación y la estructura de este repositorio. Las decisiones de alcance y
los datos descargados corresponden al autor, que revisó el contenido.

*La declaración completa, con el uso de IA durante el evento, se publica al cierre de la entrega.*

During preparation, an AI assistant (Claude, by Anthropic) was used to organize the work plan and draft
this repository's documentation and structure. Scope decisions and the downloaded data are the author's,
who reviewed the content. *The full declaration, covering AI use during the event, is published at
submission.*

## 10. Créditos y licencia / Credits and license

Autor: Emanuel Pereyra.
Datos: NASA FIRMS / LANCE (NASA ESDIS). Ver [`CITATION.cff`](CITATION.cff) para citar este repositorio.
Licencia del código: MIT (ver [`LICENSE`](LICENSE)). Los datos de NASA se rigen por su propia política de uso.

Seguridad y reporte de problemas: ver [`SECURITY.md`](SECURITY.md).

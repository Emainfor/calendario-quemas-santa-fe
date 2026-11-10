# Calendario de quemas armonizado — Santa Fe (MODIS + VIIRS)

**NASA Space Apps Challenge 2026 · Sede Rosario · Desafío: *Harmonization of MODIS and VIIRS Hot Spots***

> **Estado: en preparación.** Este repositorio contiene solo documentación y estructura.
> El código se escribe durante el hackatón (14 y 15 de noviembre de 2026).
>
> **Status: preparation only.** This repository holds documentation and structure.
> The code is written during the hackathon (14–15 November 2026).

---

## 1. El problema / The problem

Los satélites de la NASA registran focos de calor activos desde hace más de dos décadas, pero el
registro está partido entre sensores distintos (MODIS, de 1 km de resolución, y VIIRS, de 375 m)
cuyos datos no se pueden comparar directamente. Si se unen sin corregir, la actividad de quemas
puede parecer aumentar solo porque cambió el sensor.

NASA's satellites have tracked active fire hotspots for over two decades, but the record is split
across sensors (MODIS, 1 km; VIIRS, 375 m) that cannot be compared directly. Joining them without
correction can make burning activity appear to rise simply because the instrument changed.

## 2. Qué vamos a construir / What we will build

Una aplicación web que armonice los registros en un **calendario de actividad de quemas** para un
área de interés, donde se pueda:

- explorar patrones históricos,
- ver días y semanas inusuales respecto de la línea base,
- identificar períodos críticos, con su incertidumbre visible.

*(Se completa durante el hackatón.)*

## 3. Área de interés / Area of interest

Provincia de Santa Fe (datos descargados con ese polígono), con recortes por zona (Zona Núcleo,
norte santafesino, etc.) definidos al construir la aplicación.

**Limitación conocida:** las islas del Delta del Paraná del lado entrerriano no están incluidas en
un polígono de Santa Fe.

## 4. Datos / Data

Fuente: **NASA FIRMS** (Fire Information for Resource Management System), detecciones activas de
incendios de MODIS Collection 6.1 y VIIRS 375 m (S-NPP y NOAA-20).

Detalles, columnas, advertencias y cómo reproducir la descarga: ver [`docs/datos.md`](docs/datos.md).

**Cita / Citation:** seguir la política de uso de datos de Earthdata
(<https://www.earthdata.nasa.gov/engage/open-data-services-software-policies/data-use-policy>).

> Los datos **no** se incluyen en este repositorio (ver `.gitignore`).

## 5. Método / Method

*(Se completa durante el hackatón.)*

## 6. Cómo correrlo / How to run

*(Se completa durante el hackatón.)*

## 7. Limitaciones / Limitations

Estas ya las conocemos de antemano y se mantendrán visibles en la aplicación:

- **Un día sin observación no es un día sin fuego.** Los huecos de datos no son ceros.
- **Los valores armonizados son estimaciones**, no verdad absoluta.
- **S-NPP dejó de entregar datos nuevos el 2 de noviembre de 2026**, y las misiones MODIS
  (Terra/Aqua) se acercan a su fin. Por eso se incluye NOAA-20 como continuidad.
- **Los meses más recientes son datos en tiempo casi real (NRT)**, que luego son reemplazados por
  datos estándar de calidad científica y pueden cambiar.
- NASA advierte que, por su resolución espacial, estos datos **no son recomendables para decisiones
  tácticas ni para condiciones a escala local**. Esta herramienta apunta a la **planificación
  estacional y regional**, no a alertas por lote.

## 8. Caso de uso previsto / Intended use

Apoyar la planificación estacional (cosecha, logística y transporte) en zonas agroindustriales de
la región. *Este uso está por validarse con actores del sector; no es un requerimiento confirmado.*

## 9. Uso de inteligencia artificial / AI use

*(Declaración completa al cierre del hackatón: qué herramientas de IA se usaron, para qué y qué
parte fue revisada y validada por la persona autora.)*

## 10. Créditos y licencia / Credits and license

Autor: Emanuel Pereyra (Rosario, Argentina).
Datos: NASA FIRMS / LANCE (ESDIS).
Licencia del código: MIT (ver [`LICENSE`](LICENSE)).

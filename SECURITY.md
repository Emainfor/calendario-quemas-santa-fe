# Política de seguridad

## Qué no debe subirse a este repositorio

- Claves y credenciales: `MAP_KEY` de FIRMS, contraseñas o tokens de Earthdata, tokens de GitHub.
- Archivos de datos descargados (`datos/`, `*.zip`, `*.csv` de FIRMS).
- Rutas, nombres de equipo o correos personales en código, registros o capturas.

El archivo `.gitignore` excluye `datos/`, `*.zip`, `.env` y `clave_firms.txt`. Antes de cada
confirmación (`commit`) se recomienda ejecutar `git status` y revisar qué se agrega.

## Si se expone una credencial por error

1. Revocar o regenerar la credencial de inmediato en el servicio correspondiente.
2. Eliminarla del código; recordar que seguirá en el historial de Git hasta reescribirlo.
3. Avisar al autor.

## Reporte de vulnerabilidades

Si encontrás un problema de seguridad en este repositorio, abrí un *issue* sin datos sensibles o
usá la función **Report a vulnerability** de la pestaña Security de GitHub.

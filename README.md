# chile-hub — staging remoto

> **Espejo de máquina a máquina.** No es una distribución del dataset ni una API.
> El dataset publicado vive en [cortega26/chile-hub](https://github.com/cortega26/chile-hub).

Lo escribe una VM de OCI (Santiago) que ejecuta extractores de
[`chile-hub`](https://github.com/cortega26/chile-hub) para las fuentes que
bloquean el egress de GitHub Actions pero sí responden desde esa red.

- Un solo commit, reescrito en cada corrida (`--force`): el tamaño del repo se
  mantiene constante.
- Solo se publica un dataset si su extracción quedó en `source_mode=live`;
  un fallback nunca sobrescribe el último dato bueno.
- Sin datos personales: los extractores descartan RUT, email y teléfono por
  diseño.

## Contenido

`data/staging/<dataset>.csv` y `<dataset>.metadata.json` para:

- `establecimientos_educacionales` (MINEDUC)
- `resultados_educacionales` (MINEDUC)
- `pobreza_comunal` (MDS)
- `autoridades_electas` (Cámara + Senado)

`data/staging/PUBLISHED.json` lista qué datasets se actualizaron en la última
corrida.

## Licencias

Las mismas que la fuente original de cada capa; ver
[`DATA_LICENSES.md`](https://github.com/cortega26/chile-hub/blob/main/DATA_LICENSES.md)
en el repositorio principal.

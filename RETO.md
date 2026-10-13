# 🚀 Sideproject — Ingesta a S3 lista para producción

**Repositorio:** `sideproject-ingesta-s3` · **Tipo:** ETL en la nube (local con Floci) · **Tiempo:** 8–10 h · **Después de:** los retos 1 a 20

> Reglas, README y lista de cierre: [`SIDEPROJECTS.md`](docs/REGLAS.md). **No hay solución: el diseño es tuyo.**

## El caso

Los retos 15, 16 y 19 te pidieron pipelines sobre S3 y el 20 te dio requisitos ambiguos. Aquí lo conviertes en un proyecto real y **ejecutable**: en lugar de una cuenta de AWS usas Floci, un emulador local (cómo arrancarlo: `05_ingenieria_de_datos/07_nube_con_floci/02_almacenamiento/02_floci_y_s3.py`).

El requisito de tu tech lead sigue siendo el del reto 20: *«procesa los archivos de clientes que llegan a diario a S3; hay problemas de calidad; el output debe ser confiable; debe correr en local y en producción»*.

## Datos

`datos/`: seis archivos CSV de altas de clientes, del 1 al 5 de julio de 2026. Llegan como en la vida real: la mayoría bien, uno con otro formato, uno con problemas de calidad y un día enviado dos veces. Averiguar cuál es cuál es parte del reto. Son datos sintéticos.

## Qué practicas

| Retos | Dónde aparece |
|---|---|
| 1–8 | Funciones limpias, validación y refactorización |
| 9–10 | Configuración por entorno y reintentos |
| 11–14 | ETL, calidad de datos y procesamiento incremental |
| 15–16, 19–20 | S3, pipeline completo y criterio de ingeniería |

## Hitos

**Hito 1 — Preguntas antes que código.** `PREGUNTAS.md`: qué es ambiguo en el requisito, qué supones y qué criterios de aceptación defines.
*Comprueba:* al menos 8 preguntas, cada una con tu supuesto.

**Hito 2 — Entorno.** `docker compose up` levanta Floci; un script crea los buckets y sube archivos de ejemplo (buenos, malos y repetidos).
*Comprueba:* `aws s3 ls` contra Floci muestra los archivos.

**Hito 3 — El pipeline.** Lee de `s3://.../raw/`, valida, limpia y escribe Parquet particionado en `clean/`. Lo rechazado, a `quarantine/` con su motivo.
*Comprueba:* leídos = limpios + rechazados.

**Hito 4 — Incremental e idempotente.** Solo procesa archivos nuevos; relanzar no duplica.
*Comprueba:* segunda ejecución sin archivos nuevos: 0 procesados.

**Hito 5 — Local y «producción».** El mismo código corre contra Floci o contra AWS cambiando solo la configuración.
*Comprueba:* `grep -r localhost src/` no devuelve nada.

**Hito 6 — Tests y decisiones.** Tests unitarios de las transformaciones y `DECISIONS.md` con tres decisiones y sus alternativas.
*Comprueba:* `pytest` pasa sin Floci encendido.

## Preguntas para defenderlo

- ¿Cómo sabe tu pipeline qué archivos ya procesó? ¿Qué pasa si ese registro se pierde?
- ¿Qué supuesto tuyo sería el primero en confirmar con el tech lead?
- ¿Qué harías distinto si llegaran 10,000 archivos al día?

## Súbelo de nivel

- Que S3 avise de cada archivo nuevo por una cola en lugar de listar el bucket (`07_nube_con_floci/03_eventos_y_computo/03`).
- La transformación en PySpark (retos 17 y 18).

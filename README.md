# sideproject-ingesta-s3

> Pipeline que procesa los archivos de clientes que llegan a diario a S3, incremental e idempotente, en AWS local con Floci.

**Estado:** 🚧 sin empezar · **Tipo:** ETL en la nube (local con Floci) · **Módulo del programa:** 07 · Retos de integración

## La problemática

Cada día llega a S3 un archivo de altas de clientes. Algunos días viene bien, otros con otro formato, con problemas de calidad o repetido. El requisito es ambiguo a propósito: «que el resultado sea confiable y corra en local y en producción».

## Los datos

| Dónde | Qué es |
|---|---|
| `datos/` (6 archivos) | Seis CSV de altas de clientes (1 al 5 de julio de 2026): la mayoría bien, uno con otro formato, uno con problemas de calidad y un día enviado dos veces |

Los archivos de `datos/` son **sintéticos**, generados para practicar: no corresponden a personas ni a operaciones reales.

## Qué hay que construir

El enunciado completo, con sus hitos y cómo comprobar cada uno, está en [`RETO.md`](RETO.md). No trae solución: el diseño es tuyo.

- [`docs/REGLAS.md`](docs/REGLAS.md): cómo se trabaja un sideproject y qué debe tener este README al terminar.
- [`docs/RUBRICA.md`](docs/RUBRICA.md): con qué criterios se evalúa.

## Cómo se ejecuta

*Pendiente: se escribe al cerrar el primer hito. Los comandos exactos, desde `git clone`.*

## Decisiones

*Pendiente: tres decisiones técnicas y la alternativa que se descartó en cada una.*

## Qué aprendí

*Pendiente.*

---

Reto del programa de Python e ingeniería de datos: [UNIR_Python_Certification](https://github.com/KevinMondragonDev/UNIR_Python_Certification).

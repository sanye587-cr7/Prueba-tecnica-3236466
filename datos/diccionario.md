# Diccionario de datos - Corredor Linea T2

Sistema de transporte publico masivo. 14 estaciones, operacion de enero 2024
a junio 2025.

---

## validaciones.csv

Registro agregado de validaciones de tarjeta por estacion y hora.

| Campo | Tipo | Descripcion |
|---|---|---|
| `fecha` | date | Fecha de operacion (YYYY-MM-DD) |
| `hora` | int | Hora del dia, 0 a 23 |
| `estacion_id` | str | Codigo de estacion (E01 a E14) |
| `estacion_nombre` | str | Nombre comercial de la estacion |
| `franja` | str | Franja operativa a la que pertenece la hora |
| `validaciones` | int | Total de validaciones registradas en la estacion-hora |
| `validaciones_transbordo` | int | Subconjunto de `validaciones` marcadas por el sistema como transbordo |
| `ocupacion_promedio` | float | Indicador de ocupacion reportado por el sistema de flota (0 a 1) |
| `temperatura_c` | float | Temperatura ambiente registrada en la estacion |

## tiempos_recorrido.csv

| Campo | Tipo | Descripcion |
|---|---|---|
| `fecha` | date | Fecha de operacion |
| `hora` | int | Hora del dia |
| `tramo` | str | Par de estaciones consecutivas, formato `EXX-EYY` |
| `tiempo_min` | float | Tiempo promedio de recorrido del tramo, en minutos |

## flota_programada.csv

| Campo | Tipo | Descripcion |
|---|---|---|
| `fecha` | date | Fecha de operacion |
| `franja` | str | Franja operativa |
| `buses_despachados` | int | Buses efectivamente despachados en la franja |
| `horas_franja` | int | Cantidad de horas que cubre la franja |

## eventos_ciudad.csv

Registro de eventos que la operacion considera relevantes.

| Campo | Tipo | Descripcion |
|---|---|---|
| `fecha` | date | Fecha del evento |
| `tipo` | str | Categoria del evento |
| `descripcion` | str | Detalle en texto libre |
| `impacto_esperado` | str | Estimacion cualitativa: bajo / medio / alto |

---

## Franjas operativas

| Franja | Horas |
|---|---|
| `valle_madrugada` | 00:00 - 04:59 |
| `pico_am` | 05:00 - 08:59 |
| `valle_am` | 09:00 - 11:59 |
| `valle_pm` | 12:00 - 15:59 |
| `pico_pm` | 16:00 - 19:59 |
| `valle_noche` | 20:00 - 23:59 |

---

## Notas

- Los datos provienen del sistema de recaudo y del sistema de gestion de flota,
  consolidados por el equipo de operaciones.
- El indicador `ocupacion_promedio` es calculado por el proveedor del sistema de
  flota. La documentacion tecnica del proveedor no esta disponible.
- Este diccionario fue elaborado por el area de TI y no ha sido revisado por
  operaciones desde su version inicial.

# AeroPulse

Plataforma de datos de **puntualidad de vuelos y clima operativo** para aeropuertos del Caribe y Latinoamérica.

> Proyecto integrador de mi ruta de estudio de Data Engineering (oct 2026 – mar 2027). Cada fase agrega una versión nueva.

## Problema

¿Qué rutas y aeropuertos se retrasan más, en qué horarios, y cuánto se asocia el clima a esos retrasos? Información útil para aerolíneas regionales, aeropuertos, agencias de viaje y aseguradoras de retraso de vuelos.

## Fuentes de datos (públicas)

| Fuente | Uso |
| --- | --- |
| [OurAirports](https://ourairports.com/data/) | Catálogo de aeropuertos |
| [BTS On-Time Performance](https://www.transtats.bts.gov/ONTIME/) | Histórico de puntualidad (EE. UU.) |
| [AviationWeather.gov API](https://aviationweather.gov/data/api/) | METAR / TAF |
| [OpenSky Network](https://opensky-network.org/) | Posiciones de vuelos (opcional, uso no comercial) |

Solo datos públicos. Un cruce clima-vuelo muestra asociaciones, no causalidad.

## Arquitectura (objetivo)

```
Fuentes → Bronze (crudo) → Silver (limpio, UTC, deduplicado) → Gold (modelo estrella) → Power BI / API
```

Implementaciones: local (PostgreSQL + Docker + Airflow + dbt), Microsoft Fabric y AWS (S3, Glue, Athena, Step Functions).

## Estructura

| Carpeta | Contenido |
| --- | --- |
| `ingestion/` | Extractores en Python |
| `sql/` | DDL, modelo estrella y consultas de KPIs |
| `spark/` | Notebooks y jobs PySpark / Delta |
| `infra/` | Docker Compose, configuración cloud |
| `docs/` | Arquitectura, ADR y contratos de datos |

## Roadmap

| Versión | Entrega | Fecha límite | Estado |
| --- | --- | --- | --- |
| v0 | Repo, estructura y CI | 25 oct 2026 | En curso |
| v1 | Modelo estrella y 15 KPIs SQL | 8 nov 2026 | Pendiente |
| v2 | Extractores Python con tests | 22 nov 2026 | Pendiente |
| v3 | Arquitectura medallion y contratos | 29 nov 2026 | Pendiente |
| v4 | Spark + Delta Lake | 13 dic 2026 | Pendiente |
| v5 | Microsoft Fabric + Power BI | 27 dic 2026 | Pendiente |
| v6 | AWS + comparativa de costos + streaming | 31 ene 2027 | Pendiente |
| v7 | Docker + Airflow + dbt + CI | 7 feb 2027 | Pendiente |
| v1.0 | API, dashboard y demo | 7 mar 2027 | Pendiente |

## Licencia

MIT

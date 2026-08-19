# ADR-002 — Persistencia unificada con PostgreSQL y PostGIS y separación lógica de datos

**Estado:** Aceptada  
**Fecha:** 2026-07-12

## Contexto

La plataforma debe administrar información transaccional, geoespacial, histórica y auditable. El dashboard requiere consultas frecuentes sobre rutas, incidencias y ubicaciones recientes, mientras que las jefaturas y áreas de planificación necesitan reportes históricos y métricas consolidadas. La utilización de múltiples bases de datos permitiría optimizar cada carga, pero también aumentaría la complejidad de sincronización y operación.

## Decisión

Se utilizará PostgreSQL con PostGIS como plataforma principal de persistencia. Los datos se separarán lógicamente mediante estructuras diferenciadas para:

- Información operativa.
- Información geoespacial.
- Historial de eventos.
- Registros de auditoría.
- Consultas y proyecciones analíticas.

Los reportes de alto costo utilizarán consultas optimizadas, vistas o vistas materializadas, evitando ejecutar agregaciones extensas directamente sobre las consultas operativas del dashboard. La estructura deberá permitir una futura separación física del almacenamiento analítico sin modificar los contratos principales del dominio.

## Alternativas consideradas

- **Base transaccional y almacén analítico independientes:** Permitirían aislar cargas, pero requerirían procesos de extracción, transformación, sincronización y control de consistencia.
- **Base de datos NoSQL para ubicaciones:** Facilitaría el almacenamiento flexible de eventos, pero complicaría las relaciones con rutas, vehículos, cuadrillas e incidencias.
- **Base de datos sin extensión geoespacial:** Reduciría dependencias tecnológicas, pero obligaría a implementar o externalizar operaciones geográficas necesarias.

## Consecuencias positivas

- Permite manejar datos relacionales y geoespaciales en una tecnología integrada.
- Simplifica las transacciones y la consistencia entre rutas, unidades e incidencias.
- Reduce la cantidad de tecnologías que debe operar el Departamento de TI.
- Facilita consultas con coordenadas, geometrías y recorridos.
- Permite utilizar vistas materializadas para reportes frecuentes.

## Consecuencias negativas

- Las consultas analíticas pueden competir por recursos con la operación diaria.
- El crecimiento histórico puede incrementar los tiempos de respaldo y mantenimiento.
- La base de datos constituye una dependencia central del sistema.
- Una futura separación física requerirá migración y sincronización de datos.

## Medidas de mitigación

- Utilizar índices convencionales y geoespaciales.
- Aplicar particionamiento por fechas cuando el volumen lo requiera.
- Ejecutar actualizaciones de vistas materializadas fuera de períodos críticos.
- Monitorear consultas lentas y consumo de recursos.
- Definir contratos de repositorio que eviten acoplar la lógica de negocio directamente a PostgreSQL.

## Trazabilidad

- RF-03 — Generación de reportes e indicadores históricos.
- QA-04 — Auditabilidad.
- QA-05 — Modificabilidad.
- REST-02 — Trazabilidad completa.
- REST-04 — Conservación de información histórica.
- QS-01 — Rendimiento geoespacial.
- QS-04 — Trazabilidad de incidencias.
- QS-06 — Mantenibilidad.

## Criterio de validación

La ejecución de consultas analíticas no deberá impedir el cumplimiento de los tiempos máximos definidos para el monitoreo geoespacial y el registro de incidencias.

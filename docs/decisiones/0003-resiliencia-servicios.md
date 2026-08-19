# ADR-003 — Políticas de resiliencia para servicios externos

**Estado:** Aceptada  
**Fecha:** 2026-07-12

## Contexto

La plataforma depende de servicios externos de mapas, geolocalización, identidad y notificaciones. Estos servicios pueden presentar respuestas lentas, errores temporales o interrupciones completas. Una dependencia directa sin mecanismos de control podría provocar que una falla externa se propague al dashboard y a otros módulos de la plataforma.

## Decisión

Las integraciones externas serán encapsuladas mediante adaptadores y aplicarán políticas de resiliencia diferenciadas según el tipo de operación.
Se implementarán:

- Tiempo máximo de espera de 5 segundos por solicitud externa.
- Hasta dos reintentos con espera incremental únicamente para operaciones idempotentes.
- Circuit breaker después de cinco fallos consecutivos.
- Conservación de la última ubicación válida.
- Identificación visible de información desactualizada.
- Registro de fallos y generación de alertas operativas.
- Recuperación automática después del período de apertura del circuito.

Los reintentos no se utilizarán de forma automática en operaciones que puedan producir notificaciones duplicadas o efectos secundarios no controlados.

## Alternativas consideradas

- **Reintentos ilimitados:** Podrían recuperar operaciones temporales, pero aumentarían la latencia y podrían saturar un servicio que ya se encuentra degradado.
- **Fallar inmediatamente sin degradación:** Simplificaría la integración, pero eliminaría la visibilidad operativa ante interrupciones breves.
- **Duplicar internamente todos los servicios externos:** Proporcionaría mayor independencia, pero implicaría costos, infraestructura y responsabilidades fuera del alcance del sistema.

## Consecuencias positivas

- Evita que una falla externa bloquee indefinidamente el API Backend.
- Reduce la propagación de errores entre componentes.
- Mantiene información parcial disponible para los supervisores.
- Permite detectar y auditar interrupciones externas.
- Facilita sustituir un proveedor mediante el adaptador correspondiente.

## Consecuencias negativas

- La información mostrada puede quedar temporalmente desactualizada.
- Los circuit breakers y reintentos agregan estados internos que deben monitorearse.
- Un circuito abierto puede rechazar solicitudes aunque el proveedor ya haya comenzado a recuperarse.
- Los reintentos incrementan temporalmente el consumo de recursos.

## Medidas de mitigación

- Mostrar la fecha y hora de la última información válida.
- Configurar métricas sobre circuitos abiertos y cantidad de reintentos.
- Utilizar períodos de recuperación cortos y verificaciones controladas.
- Ajustar los parámetros de acuerdo con evidencia obtenida durante las pruebas.

## Trazabilidad

- RF-01 — Monitoreo casi en tiempo real.
- QA-01 — Disponibilidad.
- QA-02 — Rendimiento.
- QS-02 — Disponibilidad del dashboard.
- QS-05 — Interoperabilidad y tolerancia a fallos.

## Criterio de validación

Las fallas externas deben detectarse y notificarse en un máximo de 10 segundos, sin eliminar la última ubicación válida ni perder eventos previamente confirmados.

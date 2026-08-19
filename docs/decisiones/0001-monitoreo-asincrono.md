# ADR-001 — Actualización periódica y procesamiento asíncrono del monitoreo geoespacial

**Estado:** Aceptada  
**Fecha:** 2026-07-12

## Contexto

Las unidades recolectoras enviarán actualizaciones de ubicación durante la ejecución de las rutas. El dashboard operativo debe mostrar estas ubicaciones en intervalos cercanos al tiempo real, con un objetivo de 15 a 30 segundos. La conectividad de las unidades puede ser intermitente y la recepción de una ubicación no debe quedar bloqueada por la actualización de la interfaz, la consulta del servicio de mapas o la ejecución de otros procesos.

## Decisión

El API Backend recibirá las actualizaciones GPS mediante una interfaz HTTPS autenticada. Cada actualización válida será registrada antes de confirmar su recepción. El procesamiento de la ubicación y la actualización de la proyección consultada por el dashboard se realizarán de forma asíncrona dentro del módulo de monitoreo. La Aplicación Web consultará periódicamente la información operativa disponible, evitando mantener una conexión permanente como requisito obligatorio.

La solución distinguirá entre:

- El evento de ubicación recibido.
- La última posición válida de cada unidad.
- La representación utilizada por el dashboard.

## Alternativas consideradas

- **WebSockets como mecanismo principal:** Permitirían enviar cada actualización inmediatamente al navegador, pero aumentarían la complejidad de conexiones, reconexiones, escalamiento y monitoreo.
- **Consulta directa del servicio GPS desde la Aplicación Web:** Reduciría el procesamiento del API Backend, pero expondría la integración externa, dificultaría la auditoría y acoplaría la interfaz con el proveedor de geolocalización.
- **Microservicio independiente con plataforma de mensajería:** Proporcionaría mayor escalabilidad y aislamiento, pero agregaría infraestructura y complejidad operativa que no se justifican en la etapa inicial.

## Consecuencias positivas

- Se evita bloquear la recepción de ubicaciones por procesos posteriores.
- Se conserva trazabilidad sobre cada actualización aceptada.
- Se adapta mejor a conectividad intermitente.
- Se mantiene una arquitectura consistente con el API Backend existente.
- Se reduce la complejidad de mantener conexiones permanentes.

## Consecuencias negativas

- La ubicación mostrada puede tener una demora cercana al intervalo de actualización.
- La consulta periódica genera solicitudes repetidas al API Backend.
- El almacenamiento de eventos incrementará progresivamente el volumen de datos.
- La capacidad de escalamiento independiente será menor que con un microservicio dedicado.

## Medidas de mitigación

- Aplicar índices por unidad y fecha.
- Separar la tabla de eventos históricos de la proyección de última ubicación.
- Configurar monitoreo de colas o tareas pendientes.
- Evaluar una plataforma de mensajería si el volumen futuro supera la capacidad del procesamiento interno.

## Trazabilidad

- RF-01 — Monitoreo de rutas y unidades.
- QA-01 — Disponibilidad.
- QA-02 — Rendimiento.
- QS-01 — Rendimiento del monitoreo geoespacial.
- QS-05 — Tolerancia a fallos externos.

## Criterio de validación

Al menos el 95% de las actualizaciones debe mostrarse en el dashboard en un máximo de 30 segundos y ninguna actualización confirmada puede perderse.

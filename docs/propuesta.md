# Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos

## Problema
La Municipalidad de San José enfrenta desafíos en la gestión de la recolección de residuos debido a la planificación manual de rutas , la limitada trazabilidad de las operaciones , la baja visibilidad del estado de las unidades en campo  y la generación manual de reportes. Estas limitaciones dificultan la supervisión de las operaciones y la toma oportuna de decisiones.

## Alcance

### Incluye
  * Planificación y asignación de rutas.
  * Gestión de vehículos y cuadrillas.
  * Monitoreo geoespacial de unidades.
  * Registro de incidencias operativas.
  * Dashboard operativo y de monitoreo.
  * Generación automática de reportes.

### Excluye
  * Facturación municipal.
  * Gestión financiera.
  * Recursos humanos.
  * Gestión de rellenos sanitarios
  * Mantenimiento mecánico de la flotilla.

## Stakeholders
  * **Operarios de recolección**: registrar incidencias y consultar rutas asignadas.
  * **Conductores de vehículos recolectores**: seguimiento de recorridos y cumplimiento de rutas.
  * **Supervisores**: monitoreo operativo y gestión de incidencias.
  * **Jefatura de Servicios Urbanos**: seguimiento de indicadores y toma de decisiones.
  * **Dirección de Gestión Ambiental**: análisis de desempeño del servicio.
  * **Departamento de Planificación Municipal**: consulta de métricas e información histórica.

## Complejidad del sistema
* Participan múltiples actores con responsabilidades y necesidades de información diferenciadas.
* Se administra información operativa, histórica y geoespacial asociada a rutas, vehículos, cuadrillas e incidencias.
* La persistencia de estos datos requiere una estrategia no trivial de almacenamiento.
* El monitoreo de unidades móviles requiere procesamiento y visualización en tiempo casi real, con un intervalo objetivo de 15 a 30 segundos.
* La solución integra módulos de planificación, monitoreo, gestión de incidencias, administración de recursos y analítica.
* Requiere integración con servicios externos de mapas, geolocalización y notificaciones.
* Existen compromisos entre precisión de la información, rendimiento, disponibilidad y costos de procesamiento y almacenamiento.

## Acceso al Dominio
El equipo cuenta con acceso directo al personal involucrado en las operaciones de la Municipalidad de San José, lo que permitirá validar procesos, requerimientos y restricciones operativas reales durante el desarrollo del proyecto y fundamentar decisiones de diseño con conocimiento del dominio.
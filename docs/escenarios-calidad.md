# Escenarios de calidad

## Introducción

Los escenarios de calidad permiten evaluar cómo debe comportarse la Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos ante condiciones relevantes del entorno operativo. Para este avance se consideran atributos como disponibilidad, rendimiento, seguridad, trazabilidad, interoperabilidad y mantenibilidad, debido a que el sistema debe apoyar la supervisión de rutas, unidades recolectoras, incidencias y reportes operativos en un contexto municipal.

## Escenario 1: Rendimiento en el monitoreo geoespacial

| Elemento            | Descripción                                                                   |
| ------------------- | ----------------------------------------------------------------------------- |
| Atributo de calidad | Rendimiento                                                                   |
| Fuente              | Unidad recolectora en campo                                                   |
| Estímulo            | La unidad envía su ubicación GPS durante la ejecución de una ruta             |
| Entorno             | Operación normal durante la jornada de recolección                            |
| Artefacto           | Módulo de monitoreo geoespacial y dashboard operativo                         |
| Respuesta           | El sistema actualiza la ubicación de la unidad en el dashboard del supervisor |
| Medida              | La ubicación debe reflejarse en un intervalo máximo de 15 a 30 segundos       |

**Justificación:**  
Este escenario es relevante porque el sistema requiere monitoreo de unidades móviles en tiempo casi real. La actualización oportuna permite que los supervisores visualicen el estado de las rutas y tomen decisiones operativas durante la jornada.

## Escenario 2: Disponibilidad del dashboard operativo

| Elemento            | Descripción                                                                                |
| ------------------- | ------------------------------------------------------------------------------------------ |
| Atributo de calidad | Disponibilidad                                                                             |
| Fuente              | Supervisor operativo                                                                       |
| Estímulo            | El supervisor accede al dashboard para consultar rutas, unidades e incidencias             |
| Entorno             | Jornada operativa normal                                                                   |
| Artefacto           | Plataforma web / Dashboard operativo                                                       |
| Respuesta           | El sistema permite el acceso y muestra la información operativa disponible                 |
| Medida              | El dashboard debe estar disponible al menos el 99% del tiempo durante el horario operativo |

**Justificación:**  
La disponibilidad es crítica porque los supervisores dependen del dashboard para dar seguimiento a las unidades recolectoras y a las incidencias reportadas. Una caída del sistema durante la operación limitaría la capacidad de supervisión y respuesta.

## Escenario 3: Seguridad en el acceso por roles

| Elemento            | Descripción                                                                                |
| ------------------- | ------------------------------------------------------------------------------------------ |
| Atributo de calidad | Seguridad                                                                                  |
| Fuente              | Usuario autenticado o no autorizado                                                        |
| Estímulo            | El usuario intenta acceder a información o funcionalidades que no corresponden a su rol    |
| Entorno             | Sesión activa en la plataforma                                                             |
| Artefacto           | Módulo de autenticación y autorización                                                     |
| Respuesta           | El sistema valida los permisos del usuario y bloquea el acceso no autorizado               |
| Medida              | El 100% de las solicitudes a funciones restringidas deben pasar por validación de permisos |

**Justificación:**  
El sistema maneja información operativa municipal, reportes, rutas, incidencias y métricas históricas. Por eso, cada actor debe acceder únicamente a las funcionalidades necesarias según su rol, evitando exposición innecesaria de información.

## Escenario 4: Trazabilidad de incidencias operativas

| Elemento            | Descripción                                                                                             |
| ------------------- | ------------------------------------------------------------------------------------------------------- |
| Atributo de calidad | Trazabilidad                                                                                            |
| Fuente              | Operario de recolección                                                                                 |
| Estímulo            | El operario registra una incidencia durante una ruta asignada                                           |
| Entorno             | Operación normal en campo                                                                               |
| Artefacto           | Módulo de gestión de incidencias                                                                        |
| Respuesta           | El sistema almacena la incidencia con fecha, hora, ubicación, usuario responsable, descripción y estado |
| Medida              | La incidencia debe quedar registrada y disponible para consulta en menos de 5 segundos                  |

**Justificación:**  
La trazabilidad permite reconstruir lo ocurrido durante la operación, dar seguimiento a problemas en campo y generar reportes confiables para supervisores, jefaturas y áreas de planificación.

## Escenario 5: Interoperabilidad con servicios externos

| Elemento            | Descripción                                                                                                                         |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Atributo de calidad | Interoperabilidad / Tolerancia a fallos                                                                                             |
| Fuente              | Servicio externo de mapas o geolocalización                                                                                         |
| Estímulo            | El servicio externo responde lentamente o deja de estar disponible                                                                  |
| Entorno             | Monitoreo activo de unidades recolectoras                                                                                           |
| Artefacto           | Integración con servicios de mapas y geolocalización                                                                                |
| Respuesta           | El sistema conserva la última ubicación conocida, muestra una alerta al supervisor y evita perder los datos operativos ya recibidos |
| Medida              | El sistema debe mantener visible la última ubicación registrada y notificar la falla en menos de 10 segundos                        |

**Justificación:**  
La plataforma depende de servicios externos para mapas, geolocalización y posiblemente notificaciones. Por ello, debe contemplar fallos o latencia de estos servicios sin detener por completo la supervisión operativa.

## Escenario 6: Mantenibilidad de módulos del sistema

| Elemento            | Descripción                                                                                                          |
| ------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Atributo de calidad | Mantenibilidad                                                                                                       |
| Fuente              | Equipo técnico de desarrollo o mantenimiento                                                                         |
| Estímulo            | Se requiere modificar la lógica de reportes sin alterar el monitoreo geoespacial ni la gestión de incidencias        |
| Entorno             | Evolución normal del sistema                                                                                         |
| Artefacto           | Módulos de reportes, monitoreo e incidencias                                                                         |
| Respuesta           | El sistema permite modificar el módulo de reportes de forma independiente, sin afectar otros módulos principales     |
| Medida              | El cambio debe poder realizarse sin modificar componentes no relacionados directamente con la generación de reportes |

**Justificación:**  
El sistema está compuesto por varios módulos: planificación de rutas, monitoreo operativo, gestión de incidencias, administración de recursos y analítica. Separar responsabilidades mejora la mantenibilidad y reduce el riesgo de errores cuando el sistema evoluciona.

# Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos

---

| Campo                  | Detalle                                                                                                                                               |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre del sistema** | Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos                                                                   |
| **Grupo**              | Grupo 2                                                                                                                                               |
| **Integrantes**        | Michael Jiménez Montero — 503580589, Gregory Morera Torres — 115190172, Milton Alvarado Ramirez — 503510070, Juan Ignacio Gonzales Cortes — 118760078 |

| **URL del repositorio** | https://github.com/gmorerat-gif/pswe04-Gesti-n-Operativa-y-Anal-tica-para-la-Recolecci-n-de-Residuos-Urbanos-II-Cuatrimestre |
| **Docente** | JUAN MAURICIO LEANDRO JIMENEZ |
| **Cuatrimestre** | 2026 — 2 |
| **Versión del documento** | 0.2 — Avance1 |
| **Fecha de última actualización** | [2026-06-28] |
| Campo | Detalle |
|--------|---------|
| Nombre del sistema | Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos |
| Grupo | Grupo 2 |
| Integrantes | Michael Jiménez Montero — 503580589<br>Gregory Morera Torres — 115190172<br>Milton Alvarado Ramírez — 503510070<br>Juan Ignacio Gonzales Cortes — 118760078 |
| URL del repositorio | https://github.com/gmorerat-gif/pswe04-Gesti-n-Operativa-y-Anal-tica-para-la-Recolecci-n-de-Residuos-Urbanos-II-Cuatrimestre |
| Docente | JUAN MAURICIO LEANDRO JIMENEZ |
| Cuatrimestre | 2026 — 2 |
| Versión del documento | 0.2 — Avance 1 |
| Fecha de última actualización | 2026-06-30 |

---

## Historial de versiones

| Versión | Fecha        | Hito                | Cambios principales                                                                                  | Autor(es)                                                                      |
| ------- | ------------ | ------------------- | ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| 0.1     | 23/06/2026   | Propuesta (S03)     | Creación del documento inicial                                                                       | Michael Jiménez/Milton Alvarado                                                |
| 0.2     | 28/06/2026   | Avance 1 (S07)      | Contexto del sistema. Stakeholders, Drivers arquitectónicos,Escenarios de Calidad. Vista de Contexto | Michael Jiménez, Gregory Morera, Milton Alvarado, Juan Ignacio Gonzales Cortes |
| 0.3     | [fecha]      | Avance 2 (S11)      | [descripción]                                                                                        | [nombres]                                                                      |
| 1.0     | [fecha]      | Entrega final (S14) | Documento completo                                                                                   | [nombres]                                                                      |
| Versión | Fecha        | Hito                | Cambios principales                                                                                  | Autor(es)                                                                      |
| ------- | ------------ | ------------------- | ------------------------------                                                                       | -----------------                                                              |
| 0.1     | 23/06/2026   | Propuesta (S03)     | Creación del documento inicial                                                                       | Michael Jiménez/Milton Alvarado                                                |
| 0.2     | 28/06/2026   | Avance 1 (S07)      | Contexto del sistema. Stakeholders, Drivers arquitectónicos,Escenarios de Calidad. Vista de Contexto | Michael Jiménez, Gregory Morera, Milton Alvarado, Juan Ignacio Gonzales Cortes |
| 0.3     | 30/06/2026   | Avance 1 (S07)      | Corrección de observaciones derivadas de la revisión del Avance 1 (versión 0.2).                     | Michael Jiménez/ Milton Alvarado/ Juan Ignacio Gonzales Cortes                 |

---

> **Nota:** Este documento corresponde al Avance 1 (S07) y amplía la propuesta presentada en S03, desarrollando el contexto del sistema, el alcance, los stakeholders, los drivers arquitectónicos, los escenarios de calidad y la vista de contexto (C4 Nivel 1).

## Tabla de contenidos

1. [Descripción del sistema y alcance](#1-descripción-del-sistema-y-alcance)
   - 1.1 [Descripción general](#11-descripción-general)
   - 1.2 [Contexto del negocio o dominio](#12-contexto-del-negocio-o-dominio)
   - 1.3 [Alcance del sistema](#13-alcance-del-sistema)
   - 1.4 [Usuarios y casos de uso principales](#14-usuarios-y-casos-de-uso-principales)

2. [Stakeholders](#2-stakeholders)

3. [Drivers arquitectónicos](#3-drivers-arquitectónicos)
   - 3.1 [Requerimientos funcionales clave](#31-requerimientos-funcionales-clave)
   - 3.2 [Atributos de calidad prioritarios](#32-atributos-de-calidad-prioritarios)
   - 3.3 [Restricciones que actúan como drivers](#33-restricciones-que-actúan-como-drivers)

4. [Requerimientos de calidad — Escenarios](#4-requerimientos-de-calidad--escenarios)

5. [Vistas arquitectónicas](#5-vistas-arquitectónicas)
   - 5.1 [Vista de contexto](#51-vista-de-contexto)
   - 5.2 [Vista de estructura interna](#52-vista-de-estructura-interna)
   - 5.3 [Vista de comportamiento](#53-vista-de-comportamiento)
   - 5.4 [Vista de despliegue](#54-vista-de-despliegue)
   - 5.5 [Vista de concurrencia](#55-vista-de-concurrencia)

6. [Estilo arquitectónico](#6-estilo-arquitectónico)
   - 6.1 [Estilo arquitectónico adoptado](#61-estilo-arquitectónico-adoptado)
   - 6.2 [Alternativas arquitectónicas evaluadas](#62-alternativas-arquitectónicas-evaluadas)
   - 6.3 [Análisis de trade-offs](#63-análisis-de-trade-offs)

7. [Registro de decisiones — ADRs](#7-registro-de-decisiones--adrs)

8. [Diseño detallado](#8-diseño-detallado)
   - 8.1 [Diseño detallado de componentes](#81-diseño-detallado-de-componentes)

9. [Patrones de diseño aplicados](#9-patrones-de-diseño-aplicados)

10. [Principios y técnicas habilitadoras](#10-principios-y-técnicas-habilitadoras)

11. [Calidad y trazabilidad](#11-calidad-y-trazabilidad)

- 11.1 [Validación de escenarios de calidad](#111-validación-de-escenarios-de-calidad)
- 11.2 [Análisis de trade-offs entre atributos de calidad](#112-análisis-de-trade-offs-entre-atributos-de-calidad)
- 11.3 [Métricas de calidad del diseño](#113-métricas-de-calidad-del-diseño)

12. [Secciones específicas según el tipo de sistema](#12-secciones-específicas-según-el-tipo-de-sistema)

- 12.1 [Sistemas distribuidos / Cloud](#121-sistemas-distribuidos--cloud)
- 12.2 [Sistemas concurrentes o de tiempo real](#122-sistemas-concurrentes-o-de-tiempo-real)
- 12.3 [Sistemas IoT / Edge](#123-sistemas-iot--edge)
- 12.4 [Sistemas con Inteligencia Artificial Generativa o Agentes](#124-sistemas-con-inteligencia-artificial-generativa-o-agentes)
- 12.5 [Sistemas con requerimientos de seguridad crítica](#125-sistemas-con-requerimientos-de-seguridad-crítica)

13. [Tendencias y evolución del diseño](#13-tendencias-y-evolución-del-diseño)

- 13.1 [Tendencias arquitectónicas](#131-tendencias-arquitectónicas)
- 13.2 [Evolución del diseño](#132-evolución-del-diseño)

14. [Glosario](#14-glosario)

15. [Referencias](#15-referencias)

---

_Hito: Propuesta (S03) y Avance 1 (S07)_

---

## 1. Descripción del sistema y alcance

### 1.1 Descripción general

La Municipalidad de San José es responsable de coordinar y supervisar las operaciones de recolección de residuos urbanos en los distintos sectores del cantón. Estas operaciones involucran la planificación de rutas, la asignación de vehículos y cuadrillas, el seguimiento de recorridos, la atención de incidencias operativas y la generación de información para la supervisión y la toma de decisiones. Debido a la cantidad de recursos involucrados y a la naturaleza distribuida de la operación, la gestión eficiente del servicio depende de la disponibilidad de información confiable, oportuna y accesible para los diferentes actores que participan en el proceso (Brown, 2014; Gomaa, 2011).

Actualmente, parte de la información necesaria para gestionar la operación se administra mediante procesos manuales o herramientas aisladas, lo que dificulta obtener una visión integral del estado del servicio. Entre las principales limitaciones identificadas se encuentran la planificación manual de rutas, la limitada trazabilidad de las operaciones, la baja visibilidad de las unidades en campo y la generación manual de reportes operativos. Estas condiciones reducen la capacidad de supervisar el cumplimiento de las actividades programadas, dificultan la atención oportuna de incidencias y limitan el aprovechamiento de la información histórica para apoyar procesos de mejora continua y evaluación del desempeño operativo (Otero, 2012).

Para atender esta necesidad se propone una Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos. El sistema estará orientado a centralizar la información operativa relacionada con rutas, vehículos, cuadrillas e incidencias, permitiendo mejorar la supervisión de las operaciones y facilitar el acceso a información relevante para la toma de decisiones. La propuesta surge de la necesidad de contar con una visión integrada de la operación, que permita relacionar información actualmente dispersa y transformarla en insumos útiles para la supervisión, el control y la planificación del servicio. De esta forma, la Municipalidad podrá disponer de mejores herramientas para comprender el comportamiento de la operación, identificar oportunidades de mejora y dar seguimiento al desempeño del servicio a lo largo del tiempo.

Desde la perspectiva arquitectónica, el principal desafío consiste en diseñar una plataforma capaz de integrar información proveniente de múltiples actores y servicios externos, proporcionando monitoreo oportuno de la operación, trazabilidad de las incidencias y capacidades de análisis histórico, manteniendo atributos de calidad como disponibilidad, rendimiento, seguridad y modificabilidad.

### 1.2 Contexto del negocio o dominio

La gestión de residuos sólidos urbanos constituye uno de los servicios públicos esenciales que deben prestar los gobiernos locales para contribuir a la salud pública, la protección del ambiente y la calidad de vida de la población. En el caso de la Municipalidad de San José, este servicio comprende la planificación, coordinación, ejecución y supervisión de las actividades de recolección de residuos en los distintos sectores del cantón, mediante el uso de vehículos, cuadrillas operativas y recursos logísticos distribuidos geográficamente.

Desde una perspectiva organizacional, la operación involucra distintos niveles de responsabilidad y toma de decisiones. El personal operativo ejecuta las rutas de recolección y atiende las situaciones que se presentan en campo durante la jornada. Los supervisores coordinan recursos y dan seguimiento al cumplimiento de las actividades programadas, mientras que las jefaturas y áreas de planificación requieren información consolidada para evaluar el desempeño del servicio, identificar oportunidades de mejora y respaldar procesos de toma de decisiones a nivel táctico y estratégico (Brown, 2014).

El dominio se caracteriza por la necesidad de coordinar recursos móviles que operan simultáneamente en múltiples ubicaciones geográficas y bajo condiciones que pueden variar durante el transcurso del día. La operación puede verse afectada por factores como cambios en las condiciones del tránsito, bloqueos de vías, incidencias operativas, disponibilidad de vehículos o situaciones reportadas por la ciudadanía. Como consecuencia, la información utilizada para supervisar y gestionar el servicio debe reflejar de manera adecuada el estado de la operación y facilitar la respuesta ante eventos que afecten su ejecución.

Los procesos principales asociados al dominio incluyen la planificación y asignación de rutas, la gestión de vehículos y cuadrillas, el seguimiento de los recorridos realizados, el registro y atención de incidencias operativas, la supervisión de la operación diaria y la generación de reportes e indicadores de desempeño. Además de apoyar la ejecución diaria del servicio, estos procesos generan información histórica que puede utilizarse para analizar tendencias, evaluar el cumplimiento de objetivos operativos y apoyar iniciativas de mejora continua (Gomaa, 2011; Otero, 2012).

Desde el punto de vista regulatorio, la prestación del servicio se encuentra enmarcada dentro de las competencias asignadas a los gobiernos locales por la legislación costarricense relacionada con la gestión municipal y la gestión integral de residuos. Asimismo, la información generada durante la operación debe administrarse considerando las políticas institucionales aplicables en materia de seguridad de la información, control administrativo, trazabilidad y resguardo de datos.

Para un arquitecto de software, resulta especialmente relevante comprender que este dominio combina información operativa, histórica y geográfica generada por múltiples actores con necesidades de información diferentes. Mientras algunos usuarios requieren información actualizada para apoyar decisiones operativas durante la ejecución de las rutas, otros necesitan información consolidada para análisis, control y planificación. Esta coexistencia de necesidades operativas y analíticas representa una característica fundamental del dominio y constituye un elemento que deberá considerarse en las decisiones de diseño que se desarrollarán en las siguientes etapas del proyecto (Brown, 2014; Gomaa, 2011).

### 1.3 Alcance del sistema

**Dentro del alcance — el sistema HACE:**

Permite planificar y asignar recorridos de recolección a vehículos y cuadrillas para cada jornada operativa.
Permite mantener información actualizada sobre vehículos, cuadrillas y recursos involucrados en la operación de recolección.
Permite consultar la programación de rutas y los recursos asignados a cada recorrido.
Permite visualizar el estado de ejecución de las rutas y el avance de las actividades programadas.
Permite monitorear la ubicación de las unidades de recolección durante la operación mediante información geoespacial.
Permite registrar incidencias operativas detectadas durante la ejecución de los recorridos, incluyendo eventos que afecten el cumplimiento de las rutas planificadas.
Permite dar seguimiento a las incidencias registradas y documentar las acciones realizadas para su atención.
Permite proporcionar a supervisores y responsables operativos una visión consolidada del estado de la operación.
Permite generar reportes relacionados con el cumplimiento de rutas, atención de incidencias y utilización de recursos operativos.
Permite consultar indicadores de desempeño que apoyen actividades de supervisión, control y mejora continua del servicio.
Permite almacenar y consultar información histórica sobre recorridos, incidencias, vehículos y cuadrillas para fines de análisis y planificación.
Permite notificar eventos relevantes asociados a la operación cuando sea necesario comunicar cambios o situaciones que requieran atención.
Permite administrar usuarios y controlar el acceso a la información de acuerdo con los roles y responsabilidades definidos por la organización.
Permite mantener trazabilidad sobre las actividades registradas dentro de la plataforma para apoyar procesos de supervisión, auditoría y control.

**Fuera del alcance — el sistema NO HACE:**

No realiza procesos de facturación municipal ni administra cobros asociados a los servicios prestados por la Municipalidad.
No gestiona presupuestos, procesos contables ni actividades de administración financiera institucional.
No administra procesos de recursos humanos, incluyendo contratación, control de asistencia, planillas, vacaciones o evaluación del personal.
No gestiona el mantenimiento preventivo o correctivo de la flotilla vehicular ni administra talleres, repuestos o inventarios asociados.
No administra la operación de rellenos sanitarios, centros de transferencia o instalaciones destinadas a la disposición final de residuos.
No ejecuta procesos de contratación administrativa, compras institucionales o gestión de proveedores.
No reemplaza los sistemas corporativos municipales utilizados para gestión financiera, recursos humanos o administración documental.
No sustituye la toma de decisiones de supervisores y responsables operativos; la plataforma proporciona información y herramientas de apoyo para la gestión.
No administra infraestructura tecnológica institucional, redes, servidores o plataformas corporativas utilizadas por la Municipalidad

### 1.4 Usuarios y casos de uso principales

| Tipo de usuario                     | Casos de uso principales                                                                                                                                                                       |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Operario de Recolección             | Consultar ruta asignada, consultar actividades programadas, registrar incidencias operativas, actualizar estado de actividades realizadas, consultar incidencias reportadas                    |
| Conductor de Vehículo Recolector    | Consultar recorrido asignado, visualizar información operativa de la ruta, reportar incidencias, registrar inicio y finalización de recorridos, consultar cambios en la programación operativa |
| Supervisor Operativo                | Monitorear rutas en ejecución, visualizar ubicación de unidades operativas, gestionar incidencias, reasignar recursos operativos, generar reportes de seguimiento                              |
| Jefatura de Servicios Urbanos       | Consultar indicadores de desempeño, analizar información histórica, generar reportes ejecutivos, evaluar cumplimiento de rutas, consultar estadísticas operativas                              |
| Analista de Planificación y Gestión | Consultar información histórica consolidada, analizar tendencias operativas, generar reportes analíticos, evaluar indicadores de desempeño, exportar información para planificación            |
| Administrador del Sistema           | Gestionar usuarios y roles, administrar permisos de acceso, configurar parámetros operativos, administrar catálogos y datos maestros, consultar registros de auditoría                         |

### 1.5 Problema arquitectónico central

El problema arquitectónico central de la Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos no consiste únicamente en digitalizar la gestión de rutas, vehículos, cuadrillas e incidencias. El núcleo del problema está en mantener una visibilidad operativa confiable de la recolección mientras la información se genera en campo, se actualiza en intervalos cercanos al tiempo real y se consolida posteriormente para supervisión, fiscalización y análisis histórico.

La operación de recolección ocurre de forma distribuida: múltiples unidades y cuadrillas ejecutan rutas en distintos puntos geográficos del cantón, mientras supervisores y jefaturas necesitan conocer el estado de la operación para tomar decisiones oportunas. Esto genera una tensión arquitectónica entre la actualización rápida de datos operativos, la confiabilidad de la información recibida desde campo, la trazabilidad de los eventos registrados y la conservación de datos históricos para análisis posterior.

Para efectos del sistema, la fuente primaria de la ubicación de una unidad recolectora será el servicio o dispositivo de geolocalización asociado a la unidad. La plataforma recibirá actualizaciones periódicas de ubicación en un intervalo objetivo de 15 a 30 segundos durante la ejecución de las rutas. Sin embargo, el sistema no debe asumir que esta información estará siempre disponible ni que los servicios externos funcionarán sin interrupciones. Por esta razón, la arquitectura deberá contemplar escenarios donde el GPS no reporte, donde exista conectividad intermitente o donde el servicio externo de mapas presente fallos o latencia.

La información operativa en tiempo casi real corresponde principalmente a la ubicación de unidades, estado de rutas, avance de recorridos, incidencias activas y alertas operativas. En cambio, la información histórica o analítica corresponde a rutas ejecutadas, incidencias cerradas, cumplimiento de recorridos, tiempos de atención, utilización de vehículos y métricas consolidadas para reportes. Esta separación es relevante porque el dashboard operativo requiere datos recientes para supervisión inmediata, mientras que los reportes analíticos requieren datos consistentes, consolidados y consultables a lo largo del tiempo.

Desde el punto de vista de seguridad y fiscalización, el sistema también debe distinguir qué información puede consultar cada rol. Operarios y conductores requieren acceso a datos asociados a sus rutas y actividades asignadas; supervisores requieren visibilidad operativa de rutas, unidades e incidencias; jefaturas, planificación y gestión ambiental requieren reportes e indicadores consolidados; y administradores requieren capacidades de configuración, usuarios, roles y auditoría. Esta diferenciación obliga a diseñar mecanismos de autorización, trazabilidad y control de acceso desde la arquitectura.

Por tanto, las decisiones arquitectónicas del sistema deberán responder a las siguientes preguntas centrales:

- ¿Cómo capturar y actualizar la ubicación de unidades recolectoras sin depender de disponibilidad perfecta del GPS o del servicio de mapas?
- ¿Cómo mantener un dashboard operativo actualizado sin sacrificar trazabilidad ni consistencia histórica?
- ¿Cómo separar los datos operativos de corto plazo de los datos históricos usados para reportes y análisis?
- ¿Cómo registrar eventos auditables relacionados con rutas, incidencias, cambios de estado, usuarios y permisos?
- ¿Cómo controlar el acceso a la información según el rol del usuario?
- ¿Cómo diseñar la plataforma para que el Avance 2 derive decisiones arquitectónicas concretas a partir de estos drivers y escenarios de calidad?

---

## 2. Stakeholders

| Stakeholder                                | Rol                                                                                                                   | Intereses principales                                                                                                   | Preocupaciones o restricciones                                                                                                                             |
| ------------------------------------------ | --------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Operario de Recolección                    | Personal encargado de ejecutar actividades de recolección en campo.                                                   | Acceder fácilmente a la información de las rutas asignadas, registrar incidencias y reportar situaciones operativas.    | Facilidad de uso, acceso oportuno a la información durante la jornada y mínima carga administrativa adicional.                                             |
| Conductor de Vehículo Recolector           | Responsable de ejecutar los recorridos asignados y operar la unidad de recolección.                                   | Consultar rutas asignadas, registrar eventos relevantes y mantener visibilidad sobre cambios operativos.                | Disponibilidad de la información durante la operación y actualización oportuna de cambios en la programación.                                              |
| Supervisor Operativo                       | Responsable de coordinar y supervisar la ejecución diaria de las rutas de recolección.                                | Monitorear el estado de la operación, gestionar incidencias y coordinar recursos operativos.                            | Necesita visibilidad actualizada sobre el estado de las rutas para identificar desviaciones operativas y responder oportunamente ante eventos imprevistos. |
| Jefatura de Servicios Urbanos              | Responsable de la gestión general del servicio de recolección y de la toma de decisiones operativas.                  | Evaluar el desempeño del servicio, dar seguimiento al cumplimiento de objetivos y optimizar la utilización de recursos. | Requiere indicadores confiables, información trazable y reportes consistentes que respalden la toma de decisiones.                                         |
| Analista de Planificación y Gestión        | Responsable de analizar información operativa e histórica para apoyar procesos de planificación institucional.        | Identificar tendencias, evaluar desempeño y generar información para la mejora continua del servicio.                   | Calidad de los datos, consistencia histórica y capacidad para consultar información acumulada a lo largo del tiempo.                                       |
| Administrador del Sistema                  | Responsable de la administración funcional de la plataforma.                                                          | Gestionar usuarios, permisos, configuraciones y parámetros operativos.                                                  | Control de accesos, trazabilidad de cambios, facilidad de administración y seguridad de la información.                                                    |
| Dirección de Gestión Ambiental             | Área encargada de supervisar y evaluar el desempeño general de los servicios relacionados con la gestión de residuos. | Contar con información consolidada para evaluar resultados y apoyar decisiones estratégicas.                            | Disponibilidad de información confiable, consistencia de indicadores y acceso a información histórica para evaluación del servicio.                        |
| Departamento de Tecnologías de Información | Responsable del soporte y operación de las plataformas tecnológicas institucionales.                                  | Mantener una solución sostenible, segura e integrada con el ecosistema tecnológico institucional.                       | Seguridad, mantenibilidad, monitoreo, capacidad de integración y sostenibilidad tecnológica a largo plazo.                                                 |
| Ciudadanía                                 | Beneficiarios finales del servicio de recolección de residuos urbanos.                                                | Recibir un servicio oportuno, eficiente y consistente.                                                                  | Retrasos en la prestación del servicio, falta de atención de incidencias y baja calidad operativa.                                                         |
| Entidades de Fiscalización y Control       | Organismos encargados de verificar el cumplimiento de normativas, controles y obligaciones institucionales.           | Acceder a información confiable cuando sea requerida para procesos de control, auditoría o fiscalización.               | Integridad de la información, trazabilidad de las operaciones, disponibilidad de evidencia y cumplimiento de requisitos normativos.                        |

---

## 3. Drivers arquitectónicos

### 3.1 Requerimientos funcionales clave

| ID       | Requerimiento                                                                                                                            | Stakeholder                                                        | Por qué es un driver                                                                                 |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------- | --- | --- | --- |
| RF-01    | Monitorear en tiempo casi real la ejecución de rutas y la ubicación de las unidades, con actualizaciones objetivo cada 15 a 30 segundos. | Supervisor Operativo                                               | Obliga a diseñar mecanismos de captura, procesamiento y visualización de información en tiempo real. |
| RF-02    | Gestionar incidencias operativas durante los recorridos.                                                                                 | Supervisor Operativo, Operario de Recolección                      | Requiere componentes para registro, seguimiento y trazabilidad de eventos operativos.                |
| RF-03    | Generar reportes e indicadores históricos para toma de decisiones.                                                                       | Jefatura de Servicios Urbanos, Analista de Gestión                 | Obliga a incorporar almacenamiento histórico y capacidades analíticas.                               |
| RF-04    | Administrar usuarios, roles y permisos de acceso.                                                                                        | Administrador del Sistema                                          | Impacta directamente la arquitectura de seguridad y control de acceso.                               |
| RF-05    | Gestionar rutas, vehículos y cuadrillas como núcleo de la operación.                                                                     | Supervisor Operativo                                               | Define las entidades principales del dominio y la estructura central del sistema.                    |     |     |     |
| ID       | Requerimiento                                                                                                                            | Stakeholder                                                        | ¿Por qué es un driver?                                                                               |
| -------- | ---------------                                                                                                                          | -------------                                                      | --------------------------                                                                           |
| RF-01    | Monitorear en tiempo real la ejecución de rutas y la ubicación de las unidades.                                                          | Supervisor Operativo                                               | Obliga a diseñar mecanismos de captura, procesamiento y visualización de información en tiempo real. |
| RF-02    | Gestionar incidencias operativas durante los recorridos.                                                                                 | Supervisor Operativo, Operario de Recolección                      | Requiere componentes para el registro, seguimiento y trazabilidad de eventos operativos.             |
| RF-03    | Generar reportes e indicadores históricos para la toma de decisiones.                                                                    | Jefatura de Servicios Urbanos, Analista de Planificación y Gestión | Obliga a incorporar mecanismos de almacenamiento histórico y capacidades analíticas.                 |
| RF-04    | Administrar usuarios, roles y permisos de acceso.                                                                                        | Administrador del Sistema                                          | Impacta directamente la arquitectura de seguridad, autenticación y control de acceso.                |
| RF-05    | Gestionar rutas, vehículos y cuadrillas como núcleo de la operación.                                                                     | Supervisor Operativo                                               | Define las entidades principales del dominio y condiciona la estructura central de la solución.      |

### 3.2 Atributos de calidad prioritarios

| ID    | Atributo        | Importancia | Stakeholder                                                 | Justificación                                                                          |
| ----- | --------------- | ----------- | ----------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| QA-01 | Disponibilidad  | Alta        | Operarios, Conductores y Supervisores                       | El sistema debe estar disponible durante toda la jornada operativa.                    |
| QA-02 | Rendimiento     | Alta        | Supervisor Operativo                                        | La información debe mostrarse rápidamente para apoyar decisiones oportunas.            |
| QA-03 | Seguridad       | Alta        | Administrador del Sistema, Departamento de TI               | Debe proteger la información operativa y administrativa contra accesos no autorizados. |
| QA-04 | Auditabilidad   | Alta        | Entidades de Fiscalización y Dirección de Gestión Ambiental | Se requiere evidencia completa de actividades, incidencias y cambios realizados.       |
| QA-05 | Modificabilidad | Media       | Departamento de Tecnologías de Información                  | La plataforma debe evolucionar fácilmente para soportar nuevos requerimientos.         |

| ID    | Atributo        | Importancia | Stakeholder                                                 | Justificación                                                                          |
| ----- | --------------- | ----------- | ----------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| QA-01 | Disponibilidad  | Alta        | Operarios, Conductores y Supervisores                       | El sistema debe estar disponible durante toda la jornada operativa.                    |
| QA-02 | Rendimiento     | Alta        | Supervisor Operativo                                        | La información debe mostrarse rápidamente para apoyar decisiones oportunas.            |
| QA-03 | Seguridad       | Alta        | Administrador del Sistema, Departamento de TI               | Debe proteger la información operativa y administrativa contra accesos no autorizados. |
| QA-04 | Auditabilidad   | Alta        | Entidades de Fiscalización y Dirección de Gestión Ambiental | Se requiere evidencia completa de actividades, incidencias y cambios realizados.       |
| QA-05 | Modificabilidad | Media       | Departamento de Tecnologías de Información                  | La plataforma debe evolucionar fácilmente para soportar nuevos requerimientos.         |

### 3.3 Restricciones que actúan como drivers

| ID      | Restricción                                                               | Tipo        | Impacto en el diseño                                                                 |
| ------- | ------------------------------------------------------------------------- | ----------- | ------------------------------------------------------------------------------------ |
| REST-01 | Cumplir las políticas institucionales de seguridad de la información.     | Regulatoria | Obliga a implementar autenticación, autorización y protección de datos.              |
| REST-02 | Mantener trazabilidad completa de operaciones e incidencias.              | Negocio     | Requiere auditoría y conservación de registros históricos.                           |
| REST-03 | Integrarse con la infraestructura tecnológica institucional existente.    | Técnica     | Condiciona las tecnologías utilizadas y la arquitectura de despliegue.               |
| REST-04 | Conservar información histórica para análisis e indicadores.              | Negocio     | Obliga a diseñar estrategias de persistencia y consulta eficientes.                  |
| REST-05 | Cumplir normativa costarricense aplicable a gestión municipal y residuos. | Regulatoria | Condiciona el manejo, almacenamiento y disponibilidad de la información del sistema. |

---

## 4. Requerimientos de calidad — Escenarios

Los escenarios de calidad permiten evaluar cómo debe comportarse la Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos ante condiciones relevantes del entorno operativo. Para este avance se consideran atributos como rendimiento, disponibilidad, seguridad, trazabilidad, interoperabilidad y mantenibilidad, debido a que el sistema debe apoyar la supervisión de rutas, unidades recolectoras, incidencias y reportes operativos en un contexto municipal.

### Escenario QS-01 — Rendimiento en el monitoreo geoespacial

| Elemento                | Descripción                                                                   |
| ----------------------- | ----------------------------------------------------------------------------- |
| **Fuente del estímulo** | Unidad recolectora en campo                                                   |
| **Estímulo**            | La unidad envía su ubicación GPS durante la ejecución de una ruta             |
| **Entorno**             | Operación normal durante la jornada de recolección                            |
| **Artefacto**           | Módulo de monitoreo geoespacial y dashboard operativo                         |
| **Respuesta**           | El sistema actualiza la ubicación de la unidad en el dashboard del supervisor |
| **Medida de respuesta** | La ubicación debe reflejarse en un intervalo máximo de 15 a 30 segundos       |

**Justificación:**  
Este escenario es relevante porque el sistema requiere monitoreo de unidades móviles en tiempo casi real. La actualización oportuna permite que los supervisores visualicen el estado de las rutas y tomen decisiones operativas durante la jornada.

_Tensión con:_ QS-05 — Interoperabilidad / Tolerancia a fallos, porque depender de servicios externos de mapas o geolocalización puede afectar el tiempo de actualización esperado.

---

### Escenario QS-02 — Disponibilidad del dashboard operativo

| Elemento                | Descripción                                                                                |
| ----------------------- | ------------------------------------------------------------------------------------------ |
| **Fuente del estímulo** | Supervisor operativo                                                                       |
| **Estímulo**            | El supervisor accede al dashboard para consultar rutas, unidades e incidencias             |
| **Entorno**             | Jornada operativa normal                                                                   |
| **Artefacto**           | Plataforma web / Dashboard operativo                                                       |
| **Respuesta**           | El sistema permite el acceso y muestra la información operativa disponible                 |
| **Medida de respuesta** | El dashboard debe estar disponible al menos el 99% del tiempo durante el horario operativo |

**Justificación:**  
La disponibilidad es crítica porque los supervisores dependen del dashboard para dar seguimiento a las unidades recolectoras y a las incidencias reportadas. Una caída del sistema durante la operación limitaría la capacidad de supervisión y respuesta.

_Tensión con:_ QS-03 — Seguridad en el acceso por roles, porque aplicar validaciones de autenticación y autorización puede agregar procesamiento adicional antes de permitir el acceso a la información.

---

### Escenario QS-03 — Seguridad en el acceso por roles

| Elemento                | Descripción                                                                                |
| ----------------------- | ------------------------------------------------------------------------------------------ |
| **Fuente del estímulo** | Usuario autenticado o no autorizado                                                        |
| **Estímulo**            | El usuario intenta acceder a información o funcionalidades que no corresponden a su rol    |
| **Entorno**             | Sesión activa en la plataforma                                                             |
| **Artefacto**           | Módulo de autenticación y autorización                                                     |
| **Respuesta**           | El sistema valida los permisos del usuario y bloquea el acceso no autorizado               |
| **Medida de respuesta** | El 100% de las solicitudes a funciones restringidas deben pasar por validación de permisos |

**Justificación:**  
El sistema maneja información operativa municipal, reportes, rutas, incidencias y métricas históricas. Por eso, cada actor debe acceder únicamente a las funcionalidades necesarias según su rol, evitando exposición innecesaria de información.

_Tensión con:_ QS-02 — Disponibilidad del dashboard operativo, porque los controles de acceso aumentan la seguridad, pero pueden introducir dependencia sobre el sistema de identidad y afectar el acceso si dicho servicio presenta fallas.

---

### Escenario QS-04 — Trazabilidad de incidencias operativas

| Elemento                | Descripción                                                                                             |
| ----------------------- | ------------------------------------------------------------------------------------------------------- |
| **Fuente del estímulo** | Operario de recolección                                                                                 |
| **Estímulo**            | El operario registra una incidencia durante una ruta asignada                                           |
| **Entorno**             | Operación normal en campo                                                                               |
| **Artefacto**           | Módulo de gestión de incidencias                                                                        |
| **Respuesta**           | El sistema almacena la incidencia con fecha, hora, ubicación, usuario responsable, descripción y estado |
| **Medida de respuesta** | La incidencia debe quedar registrada y disponible para consulta en menos de 5 segundos                  |

**Justificación:**  
La trazabilidad permite reconstruir lo ocurrido durante la operación, dar seguimiento a problemas en campo y generar reportes confiables para supervisores, jefaturas y áreas de planificación.

_Tensión con:_ QS-01 — Rendimiento en el monitoreo geoespacial, porque almacenar información detallada de cada incidencia mejora la trazabilidad, pero también incrementa el volumen de datos que debe procesar y consultar la plataforma.

---

### Escenario QS-05 — Interoperabilidad y tolerancia a fallos con servicios externos

| Elemento                | Descripción                                                                                                                         |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| **Fuente del estímulo** | Servicio externo de mapas o geolocalización                                                                                         |
| **Estímulo**            | El servicio externo responde lentamente o deja de estar disponible                                                                  |
| **Entorno**             | Monitoreo activo de unidades recolectoras                                                                                           |
| **Artefacto**           | Integración con servicios de mapas y geolocalización                                                                                |
| **Respuesta**           | El sistema conserva la última ubicación conocida, muestra una alerta al supervisor y evita perder los datos operativos ya recibidos |
| **Medida de respuesta** | El sistema debe mantener visible la última ubicación registrada y notificar la falla en menos de 10 segundos                        |

**Justificación:**  
La plataforma depende de servicios externos para mapas, geolocalización y posiblemente notificaciones. Por ello, debe contemplar fallos o latencia de estos servicios sin detener por completo la supervisión operativa.

_Tensión con:_ QS-01 — Rendimiento en el monitoreo geoespacial, porque la disponibilidad y velocidad de servicios externos puede afectar el cumplimiento del intervalo de actualización de 15 a 30 segundos.

---

### Escenario QS-06 — Mantenibilidad de módulos del sistema

| Elemento                | Descripción                                                                                                          |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- |
| **Fuente del estímulo** | Equipo técnico de desarrollo o mantenimiento                                                                         |
| **Estímulo**            | Se requiere modificar la lógica de reportes sin alterar el monitoreo geoespacial ni la gestión de incidencias        |
| **Entorno**             | Evolución normal del sistema                                                                                         |
| **Artefacto**           | Módulos de reportes, monitoreo e incidencias                                                                         |
| **Respuesta**           | El sistema permite modificar el módulo de reportes de forma independiente, sin afectar otros módulos principales     |
| **Medida de respuesta** | El cambio debe poder realizarse sin modificar componentes no relacionados directamente con la generación de reportes |

**Justificación:**  
El sistema está compuesto por varios módulos: planificación de rutas, monitoreo operativo, gestión de incidencias, administración de recursos y analítica. Separar responsabilidades mejora la mantenibilidad y reduce el riesgo de errores cuando el sistema evoluciona.

_Tensión con:_ QS-02 — Disponibilidad del dashboard operativo, porque una arquitectura más modular facilita el mantenimiento, pero puede introducir más dependencias internas que deben gestionarse correctamente para no afectar la operación.

### 4.1 Trazabilidad hacia decisiones arquitectónicas del Avance 2

Los escenarios de calidad definidos en este avance no se consideran elementos aislados. Su propósito es preparar las decisiones arquitectónicas que deberán formalizarse en el Avance 2 mediante la vista de contenedores C4, la selección del estilo arquitectónico, los ADRs y el primer componente con diseño detallado.

La siguiente matriz relaciona los problemas arquitectónicos identificados, los drivers y escenarios de calidad asociados, y las decisiones que deberán analizarse en el siguiente hito.

| Problema arquitectónico                                            | Drivers relacionados       | Escenarios relacionados | Decisión esperada para Avance 2                                                                                                                                                                     |
| ------------------------------------------------------------------ | -------------------------- | ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Monitoreo geoespacial casi en tiempo real de unidades recolectoras | RF-01, QA-02               | QS-01, QS-05            | Definir el mecanismo de captura, procesamiento y visualización de ubicaciones: actualización periódica, procesamiento asincrónico, almacenamiento temporal y actualización del dashboard operativo. |
| Falla o latencia de servicios externos de mapas y geolocalización  | RF-01, QA-01, QA-02        | QS-01, QS-05            | Definir una estrategia de resiliencia ante fallos externos: uso de última ubicación conocida, alertas al supervisor, timeouts, reintentos controlados y degradación funcional.                      |
| Separación entre operación diaria y análisis histórico             | RF-03, QA-04, QA-05        | QS-02, QS-04, QS-06     | Definir si la arquitectura separará el dashboard operativo de los reportes analíticos mediante módulos, bases de datos, vistas materializadas o procesos de consolidación.                          |
| Trazabilidad de incidencias y eventos operativos                   | RF-02, QA-04               | QS-04                   | Definir cómo se registrarán eventos auditables: creación de incidencias, cambios de estado, usuario responsable, fecha, hora, ubicación y acciones realizadas.                                      |
| Control de acceso por roles                                        | RF-04, QA-03               | QS-03                   | Definir el mecanismo de autenticación y autorización, incluyendo integración con un sistema de identidad municipal y políticas de acceso por rol.                                                   |
| Disponibilidad del dashboard operativo durante la jornada          | RF-01, QA-01, QA-02        | QS-02, QS-05            | Definir una estructura que permita mantener disponible la consulta operativa aun cuando algunos servicios externos fallen parcialmente.                                                             |
| Evolución y mantenibilidad de módulos                              | RF-02, RF-03, RF-05, QA-05 | QS-06                   | Definir fronteras internas entre planificación de rutas, monitoreo, incidencias, administración de recursos, seguridad y analítica.                                                                 |
| Persistencia de datos operativos e históricos                      | RF-03, QA-04               | QS-04, QS-06            | Definir la estrategia de almacenamiento para datos transaccionales, datos geoespaciales, eventos auditables y datos históricos usados en reportes.                                                  |

A partir de esta trazabilidad, los ADRs del Avance 2 deberán derivarse directamente de los problemas identificados en este documento. De forma preliminar, se identifican las siguientes decisiones candidatas:

| ADR candidato | Decisión a documentar                                             | Justificación                                                                                                                                                 |
| ------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ADR-001       | Estrategia de monitoreo geoespacial casi en tiempo real           | Responde a la necesidad de actualizar la ubicación de unidades cada 15 a 30 segundos y mantener visibilidad operativa confiable.                              |
| ADR-002       | Separación entre dashboard operativo y reportes analíticos        | Permite distinguir datos recientes usados para supervisión inmediata de datos históricos usados para análisis y planificación.                                |
| ADR-003       | Estrategia de resiliencia ante fallos de mapas/geolocalización    | Permite mantener continuidad operativa cuando servicios externos fallen, respondan lento o dejen de reportar ubicación.                                       |
| ADR-004       | Modelo de trazabilidad y auditoría de incidencias                 | Permite registrar eventos operativos relevantes para supervisión, fiscalización y análisis posterior.                                                         |
| ADR-005       | Mecanismo de autenticación y autorización por roles               | Permite controlar qué información puede consultar o modificar cada usuario según sus responsabilidades.                                                       |
| ADR-006       | Estrategia de persistencia para información operativa e histórica | Permite soportar consultas operativas, conservación histórica, reportes e indicadores sin mezclar necesidades de lectura inmediatas con análisis posteriores. |

## Estas decisiones deberán conectarse en el Avance 2 con la vista de contenedores C4, el estilo arquitectónico seleccionado, los trade-offs identificados y el diseño detallado del primer componente.

## 5. Restricciones

> **Instrucciones:** Las restricciones son decisiones que ya fueron tomadas antes de que el grupo empiece a diseñar — no son negociables. Pueden ser tecnológicas (el cliente ya tiene Oracle), de negocio (el sistema debe estar listo en 6 meses), regulatorias (cumplimiento de la Ley 8968 en Costa Rica) o de equipo (el grupo solo conoce Java). Sé honesto — las restricciones reales ayudan a justificar decisiones de diseño que de otra forma parecerían arbitrarias.

| ID      | Restricción           | Tipo                                     | Origen            | Impacto en el diseño           |
| ------- | --------------------- | ---------------------------------------- | ----------------- | ------------------------------ |
| REST-01 | [Descripción precisa] | Técnica / Negocio / Regulatoria / Equipo | [Quién la impone] | [Cómo limita o guía el diseño] |
| REST-02 |                       |                                          |                   |                                |

---

## 6. Principios de diseño adoptados

> **Instrucciones:** Listá los principios que el grupo se compromete a respetar durante todo el diseño. No los listés todos — elegí los que son más relevantes para este sistema y explicá por qué cada uno importa en este contexto. En la sección 12 vas a demostrar con evidencia concreta que los respetaste.

| Principio                                                | Justificación para este sistema                                              |
| -------------------------------------------------------- | ---------------------------------------------------------------------------- |
| [ej. Separación de responsabilidades]                    | [Por qué este principio es especialmente importante dado el tipo de sistema] |
| [ej. Diseño para el cambio]                              |                                                                              |
| [ej. Defensa en profundidad]                             |                                                                              |
| [Agregar los que apliquen: SOLID, DRY, KISS, PoLA, etc.] |                                                                              |

---

# BLOQUE 3 — VISTAS ARQUITECTÓNICAS

_Hito: Avance 1 (S07) — sección 7.1 / Avance 2 (S11) — secciones 7.2 a 7.5_

> **Nota sobre notación:** Este documento usa **C4 como notación por defecto** para las vistas arquitectónicas porque es la notación del texto base del curso (Brown, 2014). Si para alguna vista específica C4 no es la notación más adecuada dado el tipo de sistema, el grupo puede usar la notación UML equivalente (diagrama de componentes, despliegue, estado o actividad), pero debe justificar explícitamente en esa sección por qué C4 no aplica y qué notación alternativa usa. Una justificación insuficiente se evalúa como si no hubiera diagrama.

---

## 7. Vistas arquitectónicas

### 7.1 Vista de contexto

_Hito: Avance 1 (S07)_

> **Qué muestra:** El sistema como una caja negra en su entorno. Las personas y sistemas externos que interactúan con él. Las relaciones entre ellos. **No muestra** lo que hay dentro del sistema.
>
> **Notación:** C4 nivel 1 (Context Diagram). Esta notación permite representar la Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos dentro del entorno en el que opera, identificando los actores y sistemas externos con los que intercambia información.
>
> **Instrucciones:** Se incluye el diagrama en formato Mermaid. Debajo del diagrama se describe el sistema principal, los actores externos y los sistemas externos, indicando la naturaleza de las relaciones existentes entre ellos.

---

## 5. Vistas arquitectónicas

### 5.1 Vista de contexto

La vista de contexto representa la Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos dentro de su entorno de operación, mostrando los principales actores que interactúan con ella y los sistemas externos necesarios para soportar sus funcionalidades. El objetivo de esta vista es proporcionar una comprensión de alto nivel del sistema y de las relaciones existentes con elementos externos, sin exponer detalles internos de implementación.

De acuerdo con el modelo C4 propuesto por Brown, la vista de contexto constituye el nivel más alto de abstracción y permite representar el sistema como una única unidad funcional dentro del ecosistema en el que opera, facilitando la comunicación entre los distintos interesados y proporcionando una comprensión común del alcance de la solución (Brown, 2014). Asimismo, Gomaa señala que las vistas arquitectónicas deben permitir identificar las interacciones entre el sistema y su entorno, favoreciendo el entendimiento de los requisitos y las responsabilidades asociadas a cada actor (Gomaa, 2011).

```mermaid
flowchart LR

Operario["Operario de recolección"]
Conductor["Conductor de vehículo recolector"]
Supervisor["Supervisor operativo"]
Jefatura["Jefatura de Servicios Urbanos"]
Ambiental["Dirección de Gestión Ambiental"]
Planificacion["Departamento de Planificación Municipal"]

Sistema["Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos"]

Mapas["Servicio externo de mapas"]
GPS["Servicio de geolocalización"]
Notificaciones["Servicio de notificaciones"]
Identidad["Sistema de identidad municipal"]

Operario -->|"Registra incidencias y consulta rutas"| Sistema
Conductor -->|"Consulta ruta y reporta avance"| Sistema
Supervisor -->|"Monitorea operación y gestiona incidencias"| Sistema
Jefatura -->|"Consulta dashboards e indicadores"| Sistema
Ambiental -->|"Consulta reportes y análisis"| Sistema
Planificacion -->|"Consulta métricas históricas"| Sistema

Sistema -->|"Obtiene mapas y rutas"| Mapas
GPS -->|"Envía ubicación de unidades"| Sistema
Sistema -->|"Envía alertas operativas"| Notificaciones
Sistema -->|"Valida usuarios y permisos"| Identidad
```

_Figura 1 — Vista de contexto del sistema Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos._

| Elemento                                                                            | Tipo              | Descripción de la relación                                                                                                                                                                                                            |
| ----------------------------------------------------------------------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos | Sistema principal | Sistema central del proyecto. Permite planificar rutas, administrar vehículos y cuadrillas, monitorear unidades recolectoras, registrar incidencias operativas y generar reportes para apoyar la supervisión y la toma de decisiones. |
| Operario de recolección                                                             | Persona / Rol     | Registra incidencias operativas y consulta las rutas asignadas durante la ejecución de las labores de recolección.                                                                                                                    |
| Conductor de vehículo recolector                                                    | Persona / Rol     | Consulta el recorrido asignado y reporta el avance de la ruta durante la jornada operativa.                                                                                                                                           |
| Supervisor operativo                                                                | Persona / Rol     | Monitorea las unidades recolectoras, supervisa el cumplimiento de las rutas y gestiona incidencias operativas.                                                                                                                        |
| Jefatura de Servicios Urbanos                                                       | Persona / Rol     | Consulta dashboards, reportes e indicadores para supervisar la operación y apoyar la toma de decisiones.                                                                                                                              |
| Dirección de Gestión Ambiental                                                      | Persona / Rol     | Analiza el desempeño del servicio y utiliza la información histórica para apoyar procesos de mejora continua.                                                                                                                         |
| Departamento de Planificación Municipal                                             | Persona / Rol     | Consulta métricas históricas e información consolidada para apoyar la planificación del servicio.                                                                                                                                     |
| Servicio externo de mapas                                                           | Sistema externo   | Proporciona mapas, rutas y capacidades de georreferenciación utilizadas por la plataforma para la visualización geoespacial.                                                                                                          |
| Servicio de geolocalización                                                         | Sistema externo   | Envía periódicamente la ubicación de las unidades recolectoras para soportar el monitoreo operativo.                                                                                                                                  |
| Servicio de notificaciones                                                          | Sistema externo   | Recibe solicitudes de la plataforma para enviar alertas relacionadas con incidencias y eventos relevantes.                                                                                                                            |
| Sistema de identidad municipal                                                      | Sistema externo   | Proporciona servicios de autenticación y autorización para validar usuarios, roles y permisos de acceso.                                                                                                                              |

Brown (2014) establece que la vista de contexto tiene como objetivo mostrar el sistema dentro del entorno en el que opera y representar las relaciones existentes con personas y sistemas externos. De forma complementaria, Gomaa (2011) señala que la identificación de actores y responsabilidades facilita la comprensión de los requisitos y de las interacciones entre el sistema y su entorno, constituyendo un insumo fundamental para las siguientes vistas arquitectónicas.

---

### 5.2 Vista de estructura interna

> **Estado:** Esta sección será desarrollada en el **Avance 2 (Semana 11)**, conforme a los entregables del curso. En este hito se presentará la vista de contenedores del modelo C4, describiendo los principales elementos que conforman la solución, sus responsabilidades, las tecnologías utilizadas y las relaciones de comunicación entre ellos.

---

### 5.3 Vista de Comportamiento

> **Estado:** Esta sección será desarrollada en el **Avance 2 (Semana 11)**. Se documentarán los principales flujos de interacción del sistema mediante diagramas de secuencia UML para representar el comportamiento de los casos de uso críticos y su relación con los escenarios de calidad definidos.

---

### 5.4 Vista de Despliegue

> **Estado:** Esta sección será desarrollada en la **Entrega Final (Semana 14)**. Se describirá la infraestructura donde se desplegará la solución, incluyendo los nodos de ejecución, componentes desplegados y las comunicaciones entre ellos.

---

### 5.5 Vista de Concurrencia

> **Estado:** Esta sección será desarrollada en la **Entrega Final (Semana 14)**, en caso de que la arquitectura seleccionada requiera documentar mecanismos de concurrencia, procesamiento asíncrono o sincronización entre componentes.

## 6. Estilo Arquitectónico

> **Estado:** Pendiente de desarrollo en el Avance 2 (Semana 11). En esta sección se documentará el estilo arquitectónico seleccionado, su justificación con base en los drivers arquitectónicos y los escenarios de calidad, así como las alternativas evaluadas y los principales trade-offs.

### 6.1 Estilo Arquitectónico Adoptado

> **Estado:** Pendiente de desarrollo en el Avance 2 (Semana 11).

---

### 6.2 Alternativas Arquitectónicas Evaluadas

> **Estado:** Pendiente de desarrollo en el Avance 2 (Semana 11).

---

### 6.3 Análisis de Trade-offs

> **Estado:** Pendiente de desarrollo en el Avance 2 (Semana 11).

---

## 7. Registro de decisiones — ADRs

> **Estado:** Pendiente de desarrollo en el Avance 2 (Semana 11). Se documentarán las principales decisiones arquitectónicas mediante Architecture Decision Records (ADR).

---

## 8. Diseño Detallado

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. En esta sección se documentará el diseño detallado de los componentes críticos del sistema, estableciendo su trazabilidad con la arquitectura definida y los casos de uso identificados.

### 8.1 Diseño Detallado de Componentes

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Se presentará el diseño detallado de los componentes con mayor impacto en la solución, incluyendo diagramas de clases, contratos de interfaces, análisis de robustez y diagramas de secuencia.

---

## 9. Patrones de Diseño Aplicados

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Se documentarán los patrones de diseño utilizados en la solución, justificando su aplicación dentro del contexto del sistema y su contribución a los atributos de calidad y decisiones arquitectónicas adoptadas.

## 10. Principios y Técnicas Habilitadoras

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. En esta sección se documentará cómo los principios de diseño adoptados se reflejan en la solución propuesta, proporcionando evidencia de su aplicación mediante los artefactos arquitectónicos y de diseño desarrollados durante el proyecto.

---

## 11. Calidad y Trazabilidad

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Esta sección presentará la validación del diseño arquitectónico frente a los escenarios de calidad definidos, el análisis de los principales trade-offs entre atributos de calidad y una evaluación de la calidad estructural del diseño mediante métricas y criterios arquitectónicos.

### 11.1 Validación de Escenarios de Calidad

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Se demostrará la trazabilidad entre los escenarios de calidad definidos en el Avance 1 y las decisiones arquitectónicas incorporadas en la solución.

---

### 11.2 Análisis de Trade-offs entre Atributos de Calidad

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Se documentarán los principales compromisos de diseño (trade-offs) identificados durante el desarrollo de la arquitectura y la justificación de las decisiones adoptadas.

---

### 11.3 Métricas de Calidad del Diseño

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Se analizarán indicadores de calidad estructural del diseño, tales como cohesión, acoplamiento y otras métricas que permitan evaluar la arquitectura propuesta.

## 12. Secciones Específicas según el Tipo de Sistema

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. En esta sección se documentarán únicamente los aspectos específicos que apliquen a la arquitectura del sistema, de acuerdo con las características de la solución diseñada y los entregables definidos para el curso.

### 12.1 Sistemas Distribuidos / Cloud

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Si la arquitectura propuesta corresponde a un sistema distribuido, se documentarán las decisiones relacionadas con consistencia, resiliencia, disponibilidad, despliegue en la nube y mecanismos de tolerancia a fallos.

---

### 12.2 Sistemas Concurrentes o de Tiempo Real

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. En caso de aplicar, se documentará el modelo de concurrencia, la sincronización entre procesos y las estrategias para evitar condiciones de carrera o bloqueos.

---

### 12.3 Sistemas IoT / Edge

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Si el sistema incorpora dispositivos IoT o procesamiento en el borde (Edge), se describirá la arquitectura de comunicación, el flujo de datos y las estrategias de sincronización.

---

### 12.4 Sistemas con Inteligencia Artificial Generativa o Agentes

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Si el diseño incorpora capacidades de inteligencia artificial generativa o agentes, se documentarán las decisiones arquitectónicas relacionadas con la orquestación, gestión del contexto, mecanismos de recuperación ante fallos y trazabilidad de las respuestas generadas.

---

### 12.5 Sistemas con Requerimientos de Seguridad Crítica

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Si el sistema requiere controles de seguridad avanzados o cumplimiento regulatorio, se documentará el modelo de amenazas, los controles implementados y las decisiones de diseño orientadas a la protección de la información.

---

## 13. Tendencias y Evolución del Diseño

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Esta sección analizará la evolución de la arquitectura propuesta, su alineación con tendencias relevantes de ingeniería de software y las posibilidades de evolución futura del sistema.

### 13.1 Tendencias Arquitectónicas

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Se evaluará cómo la solución incorpora, adapta o descarta tendencias arquitectónicas relevantes de acuerdo con las necesidades del dominio.

---

### 13.2 Evolución del Diseño

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Se identificarán los principales puntos de extensión del sistema y las decisiones de diseño que facilitan su evolución futura.

---

## 14. Glosario

> **Estado:** Pendiente de desarrollo en la **Entrega Final (Semana 14)**. Se incorporará el glosario de términos del dominio y conceptos técnicos utilizados de manera consistente a lo largo del documento.

## 15. Referencias

- Brown, S. (2014). _Software Architecture for Developers_. Leanpub.
- Budgen, D. (2003). _Software Design_ (2.ª ed.). Addison-Wesley.
- Gomaa, H. (2011). _Software Modeling and Design_. Cambridge University Press.
- Gamma, E., Helm, R., Johnson, R., & Vlissides, J. (1995). _Design Patterns_. Addison-Wesley.

---

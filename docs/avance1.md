# Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos

> Documento de Diseño de Software — PSWE-04  
> Universidad Cenfotec · Maestría Profesional en Ingeniería del Software

---

| Campo                             | Detalle                                                                                                                      |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **Nombre del sistema**            | Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos                                          |
| **Grupo**                         | Grupo 2                                                                                                                      |
| **Integrantes**                   | [Michael Jiménez Montero — Carné], [Nombre — Carné], [Nombre — Carné], [Nombre — Carné]                                      |
| **URL del repositorio**           | https://github.com/gmorerat-gif/pswe04-Gesti-n-Operativa-y-Anal-tica-para-la-Recolecci-n-de-Residuos-Urbanos-II-Cuatrimestre |
| **Docente**                       | [Nombre del docente]                                                                                                         |
| **Cuatrimestre**                  | 2026 — 2                                                                                                                     |
| **Versión del documento**         | 0.1 — Propuesta inicial                                                                                                      |
| **Fecha de última actualización** | [YYYY-MM-DD]                                                                                                                 |

---

## Historial de versiones

| Versión | Fecha        | Hito                | Cambios principales            | Autor(es)         |
| ------- | ------------ | ------------------- | ------------------------------ | ----------------- |
| 0.1     | [fecha]      | Propuesta (S03)     | Creación del documento inicial | [nombres]         |
| 0.2     | [20/06/2026] | Avance 1 (S07)      | [descripción]                  | [Michael Jiménez] |
| 0.3     | [fecha]      | Avance 2 (S11)      | [descripción]                  | [nombres]         |
| 1.0     | [fecha]      | Entrega final (S14) | Documento completo             | [nombres]         |

---

## Tabla de contenidos

1. [Descripción del sistema y alcance](#1-descripción-del-sistema-y-alcance)
2. [Stakeholders](#2-stakeholders)
3. [Drivers arquitectónicos](#3-drivers-arquitectónicos)
4. [Requerimientos de calidad — Escenarios](#4-requerimientos-de-calidad--escenarios)
5. [Restricciones](#5-restricciones)
6. [Principios de diseño adoptados](#6-principios-de-diseño-adoptados)
7. [Vistas arquitectónicas](#7-vistas-arquitectónicas)
   - 7.1 [Vista de contexto](#71-vista-de-contexto)
   - 7.2 [Vista de estructura interna](#72-vista-de-estructura-interna)
   - 7.3 [Vista de comportamiento](#73-vista-de-comportamiento)
   - 7.4 [Vista de despliegue](#74-vista-de-despliegue)
   - 7.5 [Vista de concurrencia](#75-vista-de-concurrencia-opcional) _(si aplica)_
8. [Estilo arquitectónico](#8-estilo-arquitectónico)
9. [Registro de decisiones — ADRs](#9-registro-de-decisiones--adrs)
10. [Diseño detallado de componentes](#10-diseño-detallado-de-componentes)
11. [Patrones de diseño aplicados](#11-patrones-de-diseño-aplicados)
12. [Principios y técnicas habilitadoras — evidencia](#12-principios-y-técnicas-habilitadoras--evidencia)
13. [Análisis de calidad del diseño](#13-análisis-de-calidad-del-diseño)
14. [Secciones específicas por tipo de sistema](#14-secciones-específicas-por-tipo-de-sistema) _(si aplica)_
15. [Tendencias y evolución del diseño](#15-tendencias-y-evolución-del-diseño)
16. [Glosario](#16-glosario)
17. [Referencias](#17-referencias)

---

# BLOQUE 1 — CONTEXTO Y PROBLEMA

_Hito: Propuesta (S03) y Avance 1 (S07)_

---

## 1. Descripción del sistema y alcance

### 1.1 Descripción general

La Municipalidad de San José es responsable de coordinar y supervisar las operaciones de recolección de residuos urbanos en los distintos sectores del cantón. Estas operaciones involucran la planificación de rutas, la asignación de vehículos y cuadrillas, el seguimiento de recorridos, la atención de incidencias operativas y la generación de información para la supervisión y la toma de decisiones. Debido a la cantidad de recursos involucrados y a la naturaleza distribuida de la operación, la gestión eficiente del servicio depende de la disponibilidad de información confiable, oportuna y accesible para los diferentes actores que participan en el proceso (Brown, 2014; Gomaa, 2011).

Actualmente, parte de la información necesaria para gestionar la operación se administra mediante procesos manuales o herramientas aisladas, lo que dificulta obtener una visión integral del estado del servicio. Entre las principales limitaciones identificadas se encuentran la planificación manual de rutas, la limitada trazabilidad de las operaciones, la baja visibilidad de las unidades en campo y la generación manual de reportes operativos. Estas condiciones reducen la capacidad de supervisar el cumplimiento de las actividades programadas, dificultan la atención oportuna de incidencias y limitan el aprovechamiento de la información histórica para apoyar procesos de mejora continua y evaluación del desempeño operativo (Otero, 2012).

Para atender esta necesidad se propone una Plataforma de Gestión Operativa y Analítica para la Recolección de Residuos Urbanos. El sistema estará orientado a centralizar la información operativa relacionada con rutas, vehículos, cuadrillas e incidencias, permitiendo mejorar la supervisión de las operaciones y facilitar el acceso a información relevante para la toma de decisiones. La propuesta surge de la necesidad de contar con una visión integrada de la operación, que permita relacionar información actualmente dispersa y transformarla en insumos útiles para la supervisión, el control y la planificación del servicio. De esta forma, la Municipalidad podrá disponer de mejores herramientas para comprender el comportamiento de la operación, identificar oportunidades de mejora y dar seguimiento al desempeño del servicio a lo largo del tiempo.

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

> **Instrucciones:** Los drivers son los factores que más van a moldear la arquitectura. No son todos los requerimientos — son los que, si los ignorás, el sistema falla o el diseño queda fundamentalmente equivocado. Clasificalos en las tres categorías siguientes. Para cada driver, indicá el stakeholder que lo origina (referencia a la sección 2) y el atributo de calidad que afecta.

### 3.1 Requerimientos funcionales clave

> Solo los que tienen impacto arquitectónico directo — los que obligan a tomar decisiones de estructura, no de implementación.

| ID    | Requerimiento | Stakeholder      | Por qué es un driver         |
| ----- | ------------- | ---------------- | ---------------------------- |
| RF-01 | [Descripción] | [Ref. sección 2] | [Impacto en la arquitectura] |
| RF-02 |               |                  |                              |

### 3.2 Atributos de calidad prioritarios

> Los más importantes para este sistema. Justificá por qué estos y no otros. Máximo 5 — si todo es prioridad, nada lo es.

| ID    | Atributo                                          | Importancia  | Stakeholder | Justificación                                        |
| ----- | ------------------------------------------------- | ------------ | ----------- | ---------------------------------------------------- |
| QA-01 | [Rendimiento / Disponibilidad / Seguridad / etc.] | Alta / Media | [Ref.]      | [Por qué este atributo es crítico para este sistema] |
| QA-02 |                                                   |              |             |                                                      |

### 3.3 Restricciones que actúan como drivers

> Restricciones que no son negociables y obligan a decisiones arquitectónicas específicas.

| ID      | Restricción   | Tipo                            | Impacto en el diseño             |
| ------- | ------------- | ------------------------------- | -------------------------------- |
| REST-01 | [Descripción] | Técnica / Negocio / Regulatoria | [Cómo condiciona las decisiones] |
| REST-02 |               |                                 |                                  |

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

---

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
> **Notación:** C4 nivel 1 (Context Diagram). Aplica a todos los tipos de sistema — un sistema embebido, un pipeline de datos, un monolito y una plataforma SaaS todos tienen contexto externo.
>
> **Instrucciones:** Incluí el diagrama (imagen exportada o código PlantUML/Mermaid en `/diagramas/c4-contexto.puml`). Debajo del diagrama, describí cada elemento: el sistema central, cada actor externo (persona o rol) y cada sistema externo, con una oración que explique la naturaleza de la relación.

![Vista de contexto](../diagramas/c4-contexto.png)
_Figura 1 — Vista de contexto del sistema [Nombre]_

| Elemento             | Tipo              | Descripción de la relación                              |
| -------------------- | ----------------- | ------------------------------------------------------- |
| [Nombre del sistema] | Sistema principal | [Descripción breve]                                     |
| [Actor externo 1]    | Persona / Rol     | [Qué hace con el sistema y cómo]                        |
| [Sistema externo 1]  | Sistema externo   | [Qué datos o servicios intercambia y con qué protocolo] |

---

### 7.2 Vista de estructura interna

_Hito: Avance 2 (S11)_

> **Qué muestra:** Las piezas principales que componen el sistema, cómo están organizadas y cómo se comunican entre sí. Esta vista es la base del diseño detallado.
>
> **Notación por defecto — C4 nivel 2 (Container Diagram):** Usá esta notación si tu sistema tiene unidades desplegables separadas — APIs, aplicaciones web, bases de datos, servicios de mensajería, apps móviles, procesos batch, etc. "Contenedor" en C4 no es Docker — es cualquier unidad de ejecución o almacenamiento con una frontera propia.
>
> **Alternativa justificada:** Si el sistema es un monolito, un firmware, un sistema embebido o un pipeline de datos sin unidades desplegables separadas, podés usar un **diagrama de componentes UML** o un **diagrama de módulos**. Justificá en la subsección 7.2.1 por qué C4 contenedores no es la representación más honesta para tu sistema.
>
> **Instrucciones:** Para cada contenedor o componente principal, describí: su responsabilidad, la tecnología usada, las interfaces que expone y las dependencias que tiene. Las relaciones entre contenedores deben indicar el protocolo o mecanismo de comunicación (REST, gRPC, eventos, SQL, etc.).

#### 7.2.1 Justificación de notación

> Si usás C4 contenedores, escribí "Se usa C4 nivel 2 porque el sistema tiene N unidades desplegables separadas: [listá]. Si usás una alternativa: "No se usa C4 nivel 2 porque [razón]. En su lugar se usa [notación] porque [justificación]."

[Completar]

#### 7.2.2 Diagrama

![Vista de estructura interna](../diagramas/estructura-interna.png)
_Figura 2 — Vista de estructura interna del sistema [Nombre]_

#### 7.2.3 Descripción de elementos

| Elemento | Tipo                             | Responsabilidad | Tecnología          | Interfaces expuestas                  | Dependencias                   |
| -------- | -------------------------------- | --------------- | ------------------- | ------------------------------------- | ------------------------------ |
| [Nombre] | Contenedor / Componente / Módulo | [Qué hace]      | [Stack tecnológico] | [API REST en /api/v1, cola SQS, etc.] | [Qué otros elementos necesita] |

---

### 7.3 Vista de comportamiento

_Hito: Avance 2 (S11) — al menos 2 flujos; Entrega final (S14) — flujos completos_

> **Qué muestra:** Cómo fluye la información y el control a través del sistema para los casos de uso más importantes. Complementa la vista estática de la sección 7.2.
>
> **Notación:** Diagramas de secuencia UML. **Esta sección es obligatoria para todos los tipos de sistema.**
>
> **Instrucciones:** Incluí un diagrama de secuencia por cada flujo crítico. Para el Avance 2, incluí al menos los 2 flujos más importantes. Para la Entrega final, cubrí el camino feliz Y al menos un camino de error o excepción por flujo. Cada diagrama debe tener título, los participantes claramente identificados y las llamadas etiquetadas con el método o mensaje.

#### Flujo 1 — [Nombre del flujo, ej. "Autenticación de usuario"]

![Diagrama de secuencia — Flujo 1](../diagramas/secuencia-flujo1.png)
_Figura 3 — [Nombre del flujo]_

**Descripción:** [Párrafo que narra el flujo, los actores involucrados, las decisiones que se toman y cómo se maneja el caso de error]

**Escenarios de calidad que este flujo valida:** [Referencias a QS-XX de la sección 4]

---

#### Flujo 2 — [Nombre del flujo]

_(Repetir estructura para cada flujo adicional)_

---

### 7.4 Vista de despliegue

_Hito: Entrega final (S14)_

> **Qué muestra:** Dónde y cómo se despliega el sistema físicamente — servidores, contenedores Docker, servicios cloud, dispositivos edge, bases de datos, balanceadores, etc.
>
> **Notación:** C4 Deployment Diagram o diagrama de despliegue UML. Obligatorio si el sistema tiene componentes distribuidos en múltiples nodos. Opcional pero recomendado para sistemas monolíticos desplegados en cloud.
>
> **Instrucciones:** Mostrá los nodos de infraestructura, qué artefactos de software corren en cada nodo, y las conexiones de red entre ellos con el protocolo indicado. Si usás servicios cloud, nombralos específicamente (ej. AWS RDS, Google Cloud Run, Azure Service Bus).

![Vista de despliegue](../diagramas/despliegue.png)
_Figura N — Vista de despliegue del sistema [Nombre]_

| Nodo              | Descripción                                       | Artefactos desplegados                 | Conectividad                                       |
| ----------------- | ------------------------------------------------- | -------------------------------------- | -------------------------------------------------- |
| [Nombre del nodo] | [ej. Servidor de aplicación en AWS EC2 t3.medium] | [ej. API REST — Java 21 / Spring Boot] | [ej. HTTPS/443 hacia clientes, JDBC/5432 hacia BD] |

---

### 7.5 Vista de concurrencia _(sección opcional)_

_Hito: Entrega final (S14) — obligatoria si el sistema maneja concurrencia_

> **Cuándo incluirla:** Si tu sistema tiene múltiples procesos o hilos ejecutándose simultáneamente, maneja eventos asincrónicos, tiene condiciones de carrera posibles, o requiere sincronización entre componentes. Si el sistema es completamente secuencial y single-threaded, omití esta sección y justificá por qué no aplica.
>
> **Notación:** Diagrama de estado UML o diagrama de actividad UML con swimlanes.
>
> **Instrucciones:** Describí el modelo de concurrencia del sistema: qué procesos o hilos existen, cómo se sincronizan, qué recursos comparten, y cómo se evitan condiciones de carrera o deadlocks. Referenciá los escenarios de calidad de la sección 4 que este modelo satisface.

**¿Aplica esta sección?** [Sí / No — y justificación]

_(Si aplica, completar con diagrama y descripción)_

---

# BLOQUE 4 — DECISIONES ARQUITECTÓNICAS

_Hito: Avance 2 (S11)_

---

## 8. Estilo arquitectónico

> **Instrucciones:** Documentá el estilo o los estilos arquitectónicos que usás en el sistema (capas, microservicios, event-driven, pipe-and-filter, CQRS, hexagonal, etc.). Un sistema puede combinar estilos — documentá cómo. Para cada estilo, explicá: por qué es el más adecuado para este sistema, cuáles son sus trade-offs en este contexto específico, y qué alternativas consideraron y rechazaron. La justificación debe conectar directamente con los drivers de la sección 3 y los escenarios de calidad de la sección 4.

### 8.1 Estilo(s) adoptado(s)

| Estilo              | Aplicación en el sistema | Justificación                                            |
| ------------------- | ------------------------ | -------------------------------------------------------- |
| [Nombre del estilo] | [Dónde y cómo se aplica] | [Por qué este estilo responde a los drivers del sistema] |

### 8.2 Alternativas consideradas y rechazadas

| Alternativa            | Por qué se consideró   | Por qué se rechazó                                              |
| ---------------------- | ---------------------- | --------------------------------------------------------------- |
| [Estilo alternativo 1] | [Qué ventajas ofrecía] | [Qué desventaja o incompatibilidad con los drivers la descartó] |
| [Estilo alternativo 2] |                        |                                                                 |

### 8.3 Análisis de trade-offs del estilo elegido

> **Instrucciones:** Todo estilo arquitectónico tiene compromisos. Documentá los trade-offs del estilo elegido en el contexto específico de este sistema. Conectá cada trade-off con un escenario de calidad de la sección 4.

| Trade-off                   | Qué se gana          | Qué se sacrifica | Escenario afectado |
| --------------------------- | -------------------- | ---------------- | ------------------ |
| [Descripción del trade-off] | [Beneficio concreto] | [Costo concreto] | [QS-XX]            |

---

## 9. Registro de decisiones — ADRs

> **Instrucciones:** Un ADR documenta una decisión arquitectónica significativa — una que, si se toma mal o se cambia después, tiene consecuencias costosas. No todas las decisiones merecen un ADR — solo las que involucran trade-offs, alternativas reales y consecuencias duraderas. Ejemplos: elección de base de datos, protocolo de comunicación entre servicios, mecanismo de autenticación, estrategia de manejo de errores, modelo de datos principal. Se requieren **mínimo 3 ADRs**. Cada ADR vive en un archivo separado en `/decisiones/ADR-XXX-titulo.md` y se referencia desde aquí.
>
> **Estado posible:** Propuesta | Aceptada | Superada | Deprecada

---

### ADR-001 — [Título de la decisión]

| Campo       | Detalle      |
| ----------- | ------------ |
| **Estado**  | [Aceptada]   |
| **Fecha**   | [YYYY-MM-DD] |
| **Autores** | [Nombres]    |

**Contexto**

> Describí la situación que requirió tomar esta decisión. ¿Qué problema estabas resolviendo? ¿Qué constraints existían? ¿Qué sabías y qué no sabías en el momento de decidir?

[Completar]

**Decisión**

> La decisión tomada, enunciada de forma clara y directa. "Decidimos usar X porque Y."

[Completar]

**Alternativas consideradas**

| Alternativa | Ventajas | Desventajas | Por qué se descartó |
| ----------- | -------- | ----------- | ------------------- |
| [Opción A]  |          |             |                     |
| [Opción B]  |          |             |                     |

**Consecuencias positivas**

- [Qué mejora o se habilita con esta decisión]
- [Qué drivers o escenarios de calidad satisface]

**Consecuencias negativas**

- [Qué se complica o qué deuda introduce]
- [Qué escenarios de calidad se ven afectados negativamente]

**Revisión requerida si:** [Condición que haría que esta decisión deba revisarse — ej. "Si el volumen de transacciones supera 10k/día, esta decisión debe reevaluarse"]

---

### ADR-002 — [Título de la decisión]

_(Repetir estructura)_

---

### ADR-003 — [Título de la decisión]

_(Repetir estructura. Agregar ADR-004, ADR-005, etc. según las decisiones del proyecto)_

---

# BLOQUE 5 — DISEÑO DETALLADO

_Hito: Entrega final (S14)_

---

## 10. Diseño detallado de componentes

> **Instrucciones:** Seleccioná los **3 componentes más críticos** del sistema — los que implementan la lógica más importante, los que tienen mayor impacto en los atributos de calidad, o los que toman las decisiones de diseño más interesantes. Para cada componente, producí los cuatro artefactos de diseño siguientes. La trazabilidad desde los casos de uso hasta el diseño es obligatoria — cada componente debe poder rastrearse hasta al menos un caso de uso de la sección 1.4.

---

### Componente 1 — [Nombre del componente]

**Responsabilidad:** [Una oración que describe qué hace este componente y por qué es crítico para el sistema]

**Trazabilidad:** [Referencia a los casos de uso de la sección 1.4 que este componente soporta] → [Referencia al elemento en la vista de estructura interna, sección 7.2]

#### 10.1.1 Diagrama de clases de diseño

> **Instrucciones:** Este no es un diagrama de clases de análisis ni un modelo de dominio. Es el diseño: incluí métodos con firmas completas (nombre, parámetros, tipo de retorno), modificadores de acceso, relaciones de dependencia reales y las interfaces que el componente expone y consume. Mostrá cómo se aplican los patrones de diseño (sección 11) dentro de este componente.

![Diagrama de clases — Componente 1](../diagramas/clases-componente1.png)
_Figura N — Diagrama de clases de diseño: [Nombre del componente]_

#### 10.1.2 Contratos de interfaz

> **Instrucciones:** Para cada método o endpoint público del componente, documentá su contrato formal. Un contrato no es solo la firma — es la especificación de qué garantiza el método y qué exige de quien lo llama.

| Método / Endpoint    | Precondición                            | Postcondición                           | Excepciones                                     |
| -------------------- | --------------------------------------- | --------------------------------------- | ----------------------------------------------- |
| `[firma del método]` | [Qué debe ser verdad antes de llamarlo] | [Qué garantiza que será verdad después] | [Qué errores puede lanzar y bajo qué condición] |

#### 10.1.3 Análisis de robustez

> **Instrucciones:** Usá el análisis de robustez para verificar que el diseño del componente cubre correctamente la interacción entre la interfaz externa (boundary), la lógica de control (control) y los datos (entity). Identificá los objetos de cada tipo que participan en los flujos principales de este componente.

| Objeto   | Tipo (Boundary / Control / Entity) | Responsabilidad |
| -------- | ---------------------------------- | --------------- |
| [Nombre] |                                    |                 |

#### 10.1.4 Diagrama de secuencia — flujo principal

> **Instrucciones:** Mostrá el flujo de mensajes entre los objetos identificados en el análisis de robustez para el caso de uso principal que este componente soporta. Incluí el camino feliz y al menos un camino de error significativo.

![Secuencia — Componente 1, flujo principal](../diagramas/secuencia-comp1-principal.png)
_Figura N — Secuencia: [Nombre del flujo principal de Componente 1]_

![Secuencia — Componente 1, camino de error](../diagramas/secuencia-comp1-error.png)
_Figura N — Secuencia: [Nombre del camino de error de Componente 1]_

---

### Componente 2 — [Nombre del componente]

_(Repetir la estructura 10.1.1 a 10.1.4)_

---

### Componente 3 — [Nombre del componente]

_(Repetir la estructura 10.1.1 a 10.1.4)_

---

## 11. Patrones de diseño aplicados

> **Instrucciones:** Documentá los patrones de diseño que aplicaste en el sistema. Se requieren **mínimo 3 patrones**. Para cada patrón, no describas el patrón en general — describí cómo lo aplicaste en este sistema específico. La justificación debe responder: ¿qué problema concreto de este sistema resuelve este patrón?, ¿qué alternativa consideraste y por qué el patrón fue mejor? El diagrama debe mostrar la aplicación real, no el diagrama genérico del libro.

---

### Patrón 1 — [Nombre del patrón, ej. "Strategy"]

| Campo                                     | Detalle                                                                          |
| ----------------------------------------- | -------------------------------------------------------------------------------- |
| **Categoría**                             | Creacional / Estructural / Comportamiento                                        |
| **Ubicación en el sistema**               | [En qué componente o capa se aplica — referencia a sección 10]                   |
| **Problema que resuelve**                 | [Descripción del problema concreto en este sistema que motivó el uso del patrón] |
| **Alternativa considerada**               | [Qué otra solución se evaluó]                                                    |
| **Por qué el patrón y no la alternativa** | [Justificación técnica, no "porque es buena práctica"]                           |

![Aplicación del patrón Strategy en [Componente]](../diagramas/patron-strategy.png)
_Figura N — Aplicación del patrón [Nombre] en [Componente/contexto]_

---

### Patrón 2 — [Nombre del patrón]

_(Repetir estructura)_

---

### Patrón 3 — [Nombre del patrón]

_(Repetir estructura. Agregar Patrón 4, 5, etc. según aplique)_

---

## 12. Principios y técnicas habilitadoras — evidencia

> **Instrucciones:** En la sección 6 declararon los principios que adoptarían. Aquí demostrás con evidencia concreta que los respetaron. Para cada principio, señalá dónde en el diseño se puede ver su aplicación — referencia específica a una clase, una interfaz, una decisión en un ADR, o un diagrama. Si hubo tensión entre principios (situación frecuente), documentá cómo la resolviste.

| Principio                   | Evidencia en el diseño                                                                                                                       | Referencia                           | Tensión con otro principio                                                          |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ | ----------------------------------------------------------------------------------- |
| [ej. Responsabilidad única] | [ej. La clase OrderProcessor solo gestiona el flujo de la orden — la validación está en OrderValidator y la persistencia en OrderRepository] | [Sección 10.1.1, diagrama de clases] | [ej. Tensiona con YAGNI cuando se separan clases para casos futuros no confirmados] |
| [Principio 2]               |                                                                                                                                              |                                      |                                                                                     |

---

# BLOQUE 6 — CALIDAD Y TRAZABILIDAD

_Hito: Entrega final (S14)_

---

## 13. Análisis de calidad del diseño

### 13.1 Validación de escenarios de calidad

> **Instrucciones:** Volvé a los escenarios de calidad de la sección 4. Para cada uno, argumentá cómo el diseño (vistas, componentes, patrones, ADRs) satisface el escenario. Esta es la trazabilidad vertical del documento — conecta los requerimientos de calidad con las decisiones de diseño concretas. Si un escenario no está completamente satisfecho, documentalo honestamente con el riesgo residual.

| Escenario        | Medida requerida         | Cómo el diseño la satisface               | Decisiones que lo habilitan      | Riesgo residual              |
| ---------------- | ------------------------ | ----------------------------------------- | -------------------------------- | ---------------------------- |
| QS-01 — [Nombre] | [Medida de la sección 4] | [Explicación de por qué el diseño cumple] | [ADR-XX, Patrón Y, Componente Z] | [Qué sigue siendo un riesgo] |
| QS-02            |                          |                                           |                                  |                              |
| QS-03            |                          |                                           |                                  |                              |
| QS-04            |                          |                                           |                                  |                              |

### 13.2 Análisis de trade-offs entre atributos de calidad

> **Instrucciones:** Identificá los conflictos entre atributos de calidad que surgieron durante el diseño y documentá cómo los resolviste. Un conflicto real (ej. rendimiento vs. consistencia) con una resolución razonada demuestra pensamiento arquitectónico maduro. Si no encontraste ningún conflicto, es señal de que el análisis no fue suficientemente profundo.

| Conflicto                                              | Atributo favorecido | Atributo sacrificado    | Decisión que lo resolvió            | Justificación                                             |
| ------------------------------------------------------ | ------------------- | ----------------------- | ----------------------------------- | --------------------------------------------------------- |
| [ej. Velocidad de respuesta vs. consistencia de datos] | [Rendimiento]       | [Consistencia eventual] | [ADR-002: uso de caché distribuida] | [El dominio tolera datos con hasta 5 segundos de desfase] |

### 13.3 Métricas de diseño — estimación

> **Instrucciones:** Para los componentes diseñados en la sección 10, estimá o calculá las métricas de cohesión y acoplamiento. No necesitás herramientas especializadas — podés hacer la estimación razonada: ¿cuántas responsabilidades tiene esta clase?, ¿de cuántos otros módulos depende?. Lo que se evalúa es que el grupo reflexionó sobre la calidad estructural del diseño, no la precisión del número.

| Componente     | Cohesión estimada   | Acoplamiento estimado | Observación                            |
| -------------- | ------------------- | --------------------- | -------------------------------------- |
| [Componente 1] | Alta / Media / Baja | Alto / Medio / Bajo   | [Justificación y qué se puede mejorar] |
| [Componente 2] |                     |                       |                                        |
| [Componente 3] |                     |                       |                                        |

---

# BLOQUE 7 — SECCIONES ESPECÍFICAS POR TIPO DE SISTEMA

_Hito: Entrega final (S14) — incluir solo las que aplican al sistema_

> **Instrucciones:** Incluí solo las secciones que corresponden al tipo de sistema que diseñaste. Si tu sistema no es distribuido, no incluís la sección 14.1. Si no tiene componentes de IA, no incluís la 14.4. Justificá al inicio de este bloque cuáles secciones incluís y por qué.

**Secciones incluidas en este proyecto:** [Listá las que aplican con una oración de justificación]

---

## 14.1 Sistemas distribuidos / cloud _(si aplica)_

> **Instrucciones:** Documentá las decisiones de diseño específicas para la distribución. Incluí la estrategia de consistencia (fuerte, eventual, causal), el modelo CAP aplicado, la estrategia de tolerancia a particiones y el modelo de despliegue en nube con los servicios específicos usados.

### Estrategia de consistencia

[Completar — qué modelo de consistencia usa el sistema y por qué es el adecuado para el dominio]

### Modelo CAP aplicado

[Completar — entre CP y AP, cuál favorece el sistema y bajo qué condiciones. Justificar con los escenarios de calidad]

### Manejo de fallos y resiliencia

[Completar — circuit breakers, retries, timeouts, fallbacks. Para cada mecanismo: dónde aplica y por qué]

---

## 14.2 Sistemas concurrentes / tiempo real _(si aplica)_

> **Instrucciones:** Documentá el modelo de concurrencia del sistema. Identificá los recursos compartidos, los mecanismos de sincronización y cómo se evitan condiciones de carrera y deadlocks.

### Modelo de concurrencia

[Completar — hilos, procesos, actores, eventos asincrónicos — qué modelo usa el sistema]

### Recursos compartidos y sincronización

| Recurso compartido | Mecanismo de sincronización   | Riesgo de condición de carrera | Mitigación         |
| ------------------ | ----------------------------- | ------------------------------ | ------------------ |
| [Recurso]          | [Mutex, semáforo, lock, etc.] | [Sí/No — descripción]          | [Cómo se previene] |

---

## 14.3 Sistemas IoT / edge _(si aplica)_

> **Instrucciones:** Documentá el diseño del flujo de datos desde los dispositivos hasta la nube o el sistema central. Incluí el protocolo de comunicación, la estrategia ante conectividad intermitente y el modelo de procesamiento en edge vs. nube.

### Topología edge-cloud

[Completar con diagrama de despliegue físico si no está cubierto en 7.4]

### Estrategia ante conectividad intermitente

[Completar — qué hace el dispositivo cuando pierde conectividad, cómo sincroniza cuando la recupera, qué datos se pierden y cuáles no]

### Protocolo de comunicación

[Completar — MQTT, CoAP, AMQP, HTTP/REST — justificación de la elección]

---

## 14.4 Sistemas con IA Generativa / Agentes _(si aplica)_

> **Instrucciones:** El diseño de sistemas con IA generativa o agentes tiene desafíos específicos que no aparecen en sistemas tradicionales. Documentá las decisiones de diseño para cada uno de los siguientes aspectos. La IA no puede ser una API call sin diseño — se evalúa que el grupo pensó en la arquitectura del sistema de IA, no solo en su uso.

### Diseño del orquestador

[Completar — cómo se coordinan los agentes o llamadas al modelo, qué decide el orquestador y qué los agentes individuales]

### Gestión de contexto y memoria

[Completar — cómo se mantiene el contexto entre interacciones, qué se persiste, qué se descarta, con qué estrategia de windowing]

### Estrategia de fallback

[Completar — qué hace el sistema cuando el modelo falla, produce respuestas inaceptables o supera el límite de latencia]

### Trazabilidad de decisiones del modelo

[Completar — cómo el sistema registra qué decisión tomó el modelo, con qué contexto y con qué resultado, para auditoría y mejora]

### Evaluación de calidad de respuestas

[Completar — cómo el sistema detecta alucinaciones, respuestas fuera de dominio o respuestas de baja calidad, y qué hace al respecto]

---

## 14.5 Sistemas con seguridad crítica _(si aplica)_

> **Instrucciones:** Si el sistema maneja datos sensibles, tiene requerimientos regulatorios o es un objetivo de ataque probable, documentá el modelo de seguridad desde el diseño.

### Modelo de amenazas (STRIDE simplificado)

| Amenaza                | Componente en riesgo | Mitigación en el diseño |
| ---------------------- | -------------------- | ----------------------- |
| Spoofing               |                      |                         |
| Tampering              |                      |                         |
| Repudiation            |                      |                         |
| Information Disclosure |                      |                         |
| Denial of Service      |                      |                         |
| Elevation of Privilege |                      |                         |

### Controles por capa

[Completar — qué controles de seguridad existen en cada capa del sistema]

---

# BLOQUE 8 — TENDENCIAS Y EVOLUCIÓN

_Hito: Entrega final (S14)_

---

## 15. Tendencias y evolución del diseño

> **Instrucciones:** Este bloque no es una sección teórica sobre tendencias — es una reflexión fundamentada sobre cómo el diseño actual se posiciona frente a las tendencias estudiadas en el curso. Para cada tendencia relevante, documentá una decisión consciente: adoptaron elementos de ella, la consideraron y la rechazaron, o la dejaron como punto de extensión futuro. Cada postura debe estar justificada con criterios de diseño, no con preferencias personales.

### 15.1 Postura frente a tendencias relevantes

| Tendencia                                     | Postura del diseño                                                | Justificación                                                  |
| --------------------------------------------- | ----------------------------------------------------------------- | -------------------------------------------------------------- |
| Microservicios                                | Adoptada / Parcialmente adoptada / Rechazada / Punto de extensión | [Por qué — conectado con los drivers y trade-offs del sistema] |
| Cloud-native / 12-factor                      |                                                                   |                                                                |
| Diseño dirigido por el dominio (DDD)          |                                                                   |                                                                |
| IA Generativa / Agentes                       |                                                                   |                                                                |
| [Otras tendencias relevantes para el dominio] |                                                                   |                                                                |

### 15.2 Puntos de extensión del diseño

> **Instrucciones:** Identificá las partes del diseño que están preparadas para crecer o cambiar sin romper el sistema. Un buen diseño anticipa el cambio sin sobrediseñar. Para cada punto de extensión, indicá qué cambio habilitaría y qué decisión de diseño lo hace posible.

| Punto de extensión                                                   | Cambio que habilita                                                         | Decisión de diseño que lo soporta                           |
| -------------------------------------------------------------------- | --------------------------------------------------------------------------- | ----------------------------------------------------------- |
| [ej. Interfaz INotificationService desacoplada de la implementación] | [Agregar un nuevo canal de notificación sin modificar la lógica de negocio] | [ADR-003: abstracción de notificaciones detrás de interfaz] |

---

# APÉNDICES

---

## 16. Glosario

> **Instrucciones:** Definí los términos del dominio y los términos técnicos específicos de este sistema que un lector externo podría no conocer. El glosario es el "ubiquitous language" del proyecto — si el equipo usa términos del dominio de forma consistente en todo el documento, este glosario los define.

| Término   | Definición                                  |
| --------- | ------------------------------------------- |
| [Término] | [Definición en el contexto de este sistema] |

---

## 17. Referencias

> **Instrucciones:** Listá todas las fuentes usadas en el documento — libros del curso, artículos, documentación técnica, estándares. Usá formato APA o IEEE de forma consistente.

- Brown, S. (2014). _Software Architecture for Developers_. Leanpub.
- Budgen, D. (2003). _Software Design_ (2.ª ed.). Addison-Wesley.
- Gomaa, H. (2011). _Software Modeling and Design_. Cambridge University Press.
- Gamma, E., Helm, R., Johnson, R., & Vlissides, J. (1995). _Design Patterns_. Addison-Wesley.
- [Agregar referencias adicionales usadas en el proyecto]

---

_Documento generado bajo el template estándar PSWE-04 — Universidad Cenfotec — Maestría Profesional en Ingeniería del Software_

# ADR-004 — Autenticación centralizada, autorización por roles y auditoría de accesos

**Estado:** Aceptada  
**Fecha:** 2026-07-12

## Contexto

La plataforma será utilizada por operarios, conductores, supervisores, jefaturas, analistas y administradores. Cada rol requiere permisos diferentes sobre rutas, incidencias, reportes, configuraciones y registros de auditoría. El sistema debe integrarse con el Servicio de Identidad Municipal y evitar administrar contraseñas institucionales directamente.

## Decisión

La autenticación se delegará al Servicio de Identidad Municipal mediante OpenID Connect y OAuth 2.0. El API Backend validará los tokens y aplicará autorización basada en roles y políticas. Todas las operaciones se considerarán denegadas por defecto y solo se habilitarán cuando exista una política explícita. La Aplicación Web podrá ocultar opciones según el rol para mejorar la experiencia, pero la decisión definitiva de autorización se realizará en el API Backend.

Se registrarán en auditoría:

- Intentos de acceso rechazados.
- Cambios de roles y permisos.
- Operaciones administrativas.
- Cambios relevantes sobre rutas e incidencias.
- Consulta o exportación de información sensible cuando corresponda.

Cada registro incluirá fecha y hora, usuario o identificador disponible, recurso, acción, origen y resultado.

## Alternativas consideradas

- **Usuarios y contraseñas almacenados localmente:** Reducirían la dependencia externa, pero aumentarían la responsabilidad de proteger credenciales y administrar ciclos de vida de usuarios.
- **Controles únicamente en la Aplicación Web:** Serían sencillos de implementar, pero podrían evadirse invocando directamente el API Backend.
- **Permisos incorporados directamente en cada controlador:** Permitirían una implementación rápida, pero producirían duplicación, inconsistencias y dificultad de mantenimiento.

## Consecuencias positivas

- Centraliza la identidad institucional.
- Evita almacenar contraseñas municipales.
- Permite aplicar políticas consistentes.
- Proporciona trazabilidad de accesos y operaciones sensibles.
- Facilita agregar nuevos roles y permisos.

## Consecuencias negativas

- El inicio de nuevas sesiones depende del Servicio de Identidad Municipal.
- La validación y auditoría agregan procesamiento a cada solicitud.
- Una definición incorrecta de roles podría conceder o bloquear accesos indebidamente.
- Los registros de auditoría incrementan el volumen de almacenamiento.

## Medidas de mitigación

- Mantener en caché las claves públicas necesarias para validar tokens vigentes.
- Aplicar pruebas automatizadas por rol y recurso.
- Revisar periódicamente la matriz de permisos.
- Restringir el acceso a los registros de auditoría.
- Monitorear fallos de autenticación y patrones anómalos.

## Trazabilidad

- RF-04 — Administración de usuarios, roles y permisos.
- QA-03 — Seguridad.
- QA-04 — Auditabilidad.
- REST-01 — Políticas institucionales de seguridad.
- QS-03 — Seguridad, rechazo y auditoría de accesos.
- QS-04 — Trazabilidad de incidencias.

## Criterio de validación

El 100% de las operaciones restringidas debe validar permisos. Los accesos no autorizados deben responder con código 401 o 403 en un máximo de 2 segundos y generar un evento de auditoría consultable.

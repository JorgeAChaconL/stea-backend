# STEA – README Técnico (Base de Proyecto)

---

## 1. Descripción General

STEA es un sistema administrativo-clínico diseñado para un centro de terapias infantiles que actualmente opera con múltiples herramientas dispersas (Excel, Google Calendar, expedientes físicos y documentos digitales sin control).

El objetivo principal del sistema es centralizar la operación del centro en una sola plataforma que permita:

* Controlar pacientes
* Gestionar agenda y sesiones
* Registrar servicios y costos
* Llevar control de pagos
* Mantener expediente digital básico
* Reducir errores operativos y fugas de dinero

STEA no inicia como sistema clínico complejo, sino como una **plataforma de control operativo con soporte clínico básico**, con capacidad de evolucionar.

---

## 2. Problema Actual

El centro presenta los siguientes problemas críticos:

* Uso excesivo de múltiples Excels desconectados
* Agenda separada del resto del sistema (Google Calendar)
* No existe trazabilidad entre:

  * citas
  * sesiones realizadas
  * pagos
* Fugas de dinero por falta de control
* Dependencia de personas clave
* Expedientes duplicados (físico + digital sin control)
* Riesgo de pérdida de información
* Procesos manuales y repetitivos

---

## 3. Objetivo del Sistema

Crear una plataforma que:

* Sea la **fuente única de verdad**
* Permita auditar la operación
* Reduzca errores humanos
* Conecte agenda, sesiones, pagos y expediente
* Sea fácil de usar para personal no técnico
* Escale a múltiples sedes

---

## 4. Reglas del Negocio (Core Rules)

```text
- Cada paciente debe existir una sola vez en el sistema
- Cada sesión debe poder auditarse
- Cada servicio debe relacionarse con un pago
- Toda evidencia clínica debe pertenecer a un expediente
- No se debe depender de Excel como fuente de verdad
- Cada rol tiene acceso limitado según su responsabilidad
- Los cambios importantes deben quedar registrados
- La lógica crítica vive en backend
- El sistema debe permitir conciliación entre sesiones, pagos y servicios
```

---

## 5. Nivel de Complejidad

Complejo

Justificación:

* Manejo de datos sensibles (salud)
* Múltiples roles con permisos distintos
* Integración de agenda, pagos y expediente
* Reglas de negocio variables por tipo de servicio
* Necesidad de auditoría y trazabilidad

---

## 6. Stack Tecnológico

### Frontend

* React
* Vite
* JavaScript
* TailwindCSS
* DaisyUI

### Backend

* Node.js
* Express

### Base de Datos

* PostgreSQL

### ORM

* Prisma 6.x

### Infraestructura

* VPS (Linux)
* Nginx
* PM2

### Otros

* JWT (autenticación interna)
* Google OAuth (login)
* Google Calendar API (sincronización)
* Storage para documentos
* Logs y auditoría

---

## 7. Arquitectura General

* Tipo: Separado (Frontend / Backend)
* Comunicación: REST API

Repositorios:

* stea-frontend
* stea-backend

Principio clave:

```text
STEA es la fuente de verdad.
Servicios externos son complementarios.
```

---

## 8. Integraciones

### Google Calendar

Uso:

* Sincronización de citas
* Visualización para terapeutas

Regla:

```text
STEA controla la agenda.
Google Calendar solo refleja.
```

---

### Google Login

Uso:

* Autenticación segura
* Reducción de manejo de contraseñas

Flujo:

```text
Login Google → Backend valida → Usuario interno → JWT
- Siempre existir respaldo de información
- No eliminar datos críticos (soft delete)
```

---

## 10. Roles del Sistema
| Coordinador    | Supervisión        | Pacientes y terapeutas |
| Terapeuta      | Operación clínica  | Sesiones, notas        |
| Consulta       | Solo lectura       | Información limitada   |

---

## 11. Módulos del Sistema

```text
- Auth
- Usuarios
- Pacientes
- Expedientes
- Agenda
- Sesiones
- Servicios y costos
- Pagos
- Reportes
- Auditoría
- Configuración
```

---

## 12. Flujos Principales

### Alta de paciente

1. Registro
2. Creación de expediente
3. Asignación de servicio
4. Programación inicial

---

### Sesión

1. Agendar cita
2. Realizar sesión
3. Registrar evidencia
4. Validar pago

---

### Conciliación

1. Comparar sesiones vs pagos
2. Detectar inconsistencias

3. Generar reportes
| Rol            | Descripción        | Permisos               |

| Recepción      | Agenda             | Citas, asistencia      |
---

## 13. Seguridad y Cumplimiento

El sistema debe alinearse desde el diseño a:

### Leyes (México)

* LFPDPPP (protección de datos)

### Normativas

* NOM-004-SSA3 (expediente clínico)
* NOM-024 (sistemas de salud)

### ISO (referencia)

* ISO 27001 (seguridad)
* ISO 27799 (datos de salud)

---

## 14. Reglas de Seguridad Técnica

```text
- Uso obligatorio de HTTPS
- Control de acceso por rol
- Auditoría de acciones
- Manejo seguro de documentos
- Backups automáticos
- No exposición de datos sensibles
```

---

## 15. MVP (Primera Versión)

Debe resolver:

* Registro de pacientes
* Agenda funcional
* Catálogo de servicios
* Registro de sesiones
* Control básico de pagos
* Vista administrativa
* Expediente básico
* Roles y permisos

---

## 16. Fuera de MVP

* Formularios clínicos complejos
* Automatización completa de diagnósticos
* Certificaciones legales completas
* Portal externo
* Facturación avanzada

---

## 17. Roadmap

### Fase 1

* Auth
* Pacientes
* Agenda
* Servicios
* Sesiones
* Pagos

### Fase 2

* Expediente completo
* Documentos
* Notas clínicas
* Conciliación avanzada

### Fase 3

* Automatización clínica
* Reportes avanzados
* Integraciones externas

---

## 18. Riesgos

* Manejo de datos sensibles
* Mala adopción por usuarios
* Complejidad operativa
* Dependencia de procesos actuales
* Falta de respaldo de datos

---

## 19. Objetivo de la v1

```text
Tener control total de la operación administrativa:
- qué se agenda
- qué se atiende
- qué se cobra
- qué se paga
```

---

## 20. Dirección del Proyecto

STEA no es solo un sistema.

Es la transición de:

```text
Operación manual → Sistema controlado → Plataforma escalable
```

---

## 21. Enfoque Estratégico

```text
Primero: resolver administración
Después: fortalecer expediente
Finalmente: evolucionar a sistema clínico completo
```

---

## 22. Estado Actual

* Blueprint definido
* Reglas claras
* Stack definido
* Arquitectura definida
* Enfoque validado con usuario real

---

## 23. Siguiente Paso

```text
Diseñar:
- Auth + Roles
- Modelo de datos base
- Agenda (con integración Google)
```

---
| Dirección      | Visión total       | Acceso completo        |
| -------------- | ------------------ | ---------------------- |
| Administración | Control financiero | Pagos, reportes        |


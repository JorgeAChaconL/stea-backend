# STEA – Project Rules v1

## Objetivo de la v1

Resolver el problema administrativo principal:

- control de pacientes
- control de sesiones
- control de pagos
- trazabilidad básica

NO resolver todo lo clínico en esta fase.

---

## Qué SÍ entra en v1

- Auth + roles
- Pacientes
- Agenda básica
- Registro de sesiones
- Control de pagos
- Relación sesión ↔ pago
- Vista administrativa
- Auditoría básica

---

## Qué NO entra en v1

- Automatización clínica compleja
- Formularios médicos avanzados
- IA
- Reportes avanzados
- Facturación completa

---

## Reglas clave

- STEA es la fuente de verdad
- No depender de Excel
- Toda sesión debe poder auditarse
- Todo pago debe tener referencia
- No borrar datos críticos (soft delete)
- Lógica crítica vive en backend

---

## Stack confirmado

Frontend:
- React + Vite + Tailwind + DaisyUI

Backend:
- Node + Express

DB:
- PostgreSQL

ORM:
- Prisma

Infra:
- VPS + Nginx + PM2

---

## Módulos v1

- Auth
- Usuarios
- Pacientes
- Agenda
- Sesiones
- Pagos
- Auditoría básica

---

## Orden de desarrollo

1. Auth + roles
2. Pacientes
3. Agenda
4. Sesiones
5. Pagos
6. Relación sesión-pago
7. Auditoría

---

## Regla crítica

NO avanzar a siguiente módulo si el actual está inestable.
# Git Workflow – STEA

## Ramas

- main → producción
- develop → integración
- feature/*
- fix/*
- hotfix/*
- refactor/*
- docs/*

---

## Flujo

Nueva feature:
feature/* → develop → main

Fix:
fix/* → develop

Hotfix:
hotfix/* → main → develop

---

## Convención commits

feat: nueva funcionalidad  
fix: corrección  
refactor: mejora interna  
docs: documentación  
chore: mantenimiento  

---

## Reglas

- no commits genéricos
- no mezclar responsabilidades
- no trabajar directo en main
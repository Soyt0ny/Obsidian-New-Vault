---
tags:
  - project
status: active
priority: high
start_date: '{"date":"2024-01-15"}'
due_date: 2024-04-01
owner: Yo
area: Engineering
---

# Project: Personal Finance Tracker API

## Overview
> **Goal:** Construir una API REST para rastrear gastos e ingresos personales, con soporte para dashboard de visualización de datos.

- **Why?** Para dejar de usar hojas de Excel y aprender desarrollo backend con Go (Golang).
- **Success Criteria:** 
  - API desplegada en AWS Lambda
  - 90% cobertura de pruebas
  - Frontend puede obtener y mostrar gráficos mensuales

## Objectives & OKRs
- [x] Diseñar Esquema de Base de Datos
- [ ] Implementar endpoints CRUD para Transacciones
- [ ] Configurar pipeline de CI/CD

## Milestones
- [x] **Phase 1:** API Core & Configuración DB (2024-02-01)
- [ ] **Phase 2:** Auth & Gestión de Usuarios (2024-02-20)
- [ ] **Phase 3:** Endpoints de Reportes (2024-03-10)

## Technical Specs
- **Stack:** Go (Gin framework), PostgreSQL, Docker
- **Architecture:** Clean Architecture (Handlers -> Services -> Repositories)

## Project Log
- [[2024-01-20]]: Repositorio inicializado y Docker Compose configurado.
- [[2024-02-05]]: Scripts de migración completados para la base de datos.

## Resources & References
- [Repo Link](https://github.com/username/finance-tracker)
- [Design Doc](https://docs.google.com/document/d/xyz)

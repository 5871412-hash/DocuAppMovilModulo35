# 🏗️ Manual Técnico de Arquitectura y Despliegue

Este documento detalla la estructura física y lógica del sistema, los requisitos de infraestructura del servidor y el procedimiento para empaquetar el portal mediante contenedores Docker.

---

## 1. Arquitectura de Despliegue (Modelo de 3 Capas)

El sistema está diseñado bajo un modelo distribuido de **3 capas**, garantizando el aislamiento de responsabilidades y la alta disponibilidad de los servicios:

```text
+-------------------------------------------------------------------+
|                     CAPA DE PRESENTACIÓN                          |
|  - Aplicación Móvil (React Native)                                |
|  - Portal Web de Documentación (Nginx / MkDocs)                   |
+-------------------------------------------------------------------+
                                  │
                                  │ (Peticiones HTTP / JSON)
                                  ▼
+-------------------------------------------------------------------+
|                       CAPA DE NEGOCIO                             |
|  - Servidor REST API (Node.js / Express)                          |
|  - Middleware de Autenticación (JWT)                              |
+-------------------------------------------------------------------+
                                  │
                                  │ (Consultas SQL)
                                  ▼
+-------------------------------------------------------------------+
|                        CAPA DE DATOS                              |
|  - Motor de Base de Datos (PostgreSQL 15)                         |
+-------------------------------------------------------------------+
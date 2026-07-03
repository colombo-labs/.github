<div align="center">

# 🚀 Colombo Labs

**Innovación en movilidad urbana con datos abiertos, IA y visualización geoespacial**

[![Bogotá](https://img.shields.io/badge/📍-Bogotá,_Colombia-blue)]()
[![Datos Abiertos](https://img.shields.io/badge/🗂️-Datos_Abiertos-green)]()
[![IA](https://img.shields.io/badge/🧠-Inteligencia_Artificial-purple)]()

---

</div>

## 🎯 ¿Quiénes somos?

Somos un equipo de desarrolladores colombianos apasionados por transformar la movilidad urbana usando **datos abiertos**, **inteligencia artificial** y **tecnología geoespacial**. Creemos que la información pública puede mejorar la calidad de vida de millones de personas.

## 🗺️ MoviCol — Nuestro proyecto principal

**MoviCol** es una plataforma de movilidad inteligente para Bogotá que integra datos de TransMilenio, SITP, siniestralidad vial y red urbana para ofrecer:

- 🗺️ **Planificador de viajes multimodal** — TM, SITP, vehículo, bicicleta, caminata
- 🧠 **Predicción de congestión** — Modelos GNN (Graph Attention Network) entrenados con datos reales
- 📊 **Métricas en tiempo real** — Congestión, alertas, estado del sistema
- 🤖 **Asistente IA** — Chat contextual para consultas de movilidad
- ♿ **Accesibilidad** — Información de estaciones accesibles
- 🌐 **Multiidioma** — Español, inglés, francés, portugués

### 🏗️ Arquitectura

```
Frontend (React/Vite) → Backend (NestJS) → AI Service (FastAPI) → PostGIS
                              ↕                      ↕
                           Redis              GNN Models (PyTorch)
```

### 📦 Repositorios

| Repo | Stack | Descripción |
|------|-------|-------------|
| [movicol-frontend](https://github.com/colombo-labs/movicol-frontend) | React + Vite + Leaflet | App web PWA estilo Google Maps |
| [movicol-backend](https://github.com/colombo-labs/movicol-backend) | NestJS + TypeORM + Redis | API REST y WebSocket |
| [movicol-ai](https://github.com/colombo-labs/movicol-ai) | FastAPI + PyTorch + NetworkX | Predicción GNN y routing |
| [movicol-data](https://github.com/colombo-labs/movicol-data) | Python + PostGIS | ETL de datos abiertos de Bogotá |
| [movicol-infra](https://github.com/colombo-labs/movicol-infra) | Docker Compose | Infraestructura local y CI/CD |
| [movicol-docs](https://github.com/colombo-labs/movicol-docs) | Astro Starlight | Documentación del proyecto |

## 🛠️ Tech Stack

<div align="center">

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-10-E0234E?logo=nestjs&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.115-009688?logo=fastapi&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-2.x-EE4C2C?logo=pytorch&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostGIS-3.4-4169E1?logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-7-DC382D?logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white)

</div>

## 📊 Fuentes de datos

- [TransMilenio S.A.](https://www.transmilenio.gov.co/) — Estaciones, rutas troncales, demanda
- [SITP](https://www.sitp.gov.co/) — Rutas zonales y alimentadoras
- [Datos Abiertos Bogotá](https://datosabiertos.bogota.gov.co/) — Siniestralidad, red vial
- [OpenStreetMap](https://www.openstreetmap.org/) — POIs, red caminable
- [OSRM](http://project-osrm.org/) — Routing vehicular

## 👥 Equipo

| Nombre | Rol |
|--------|-----|
| Pipe Escobar | Frontend, UX, DevOps |
| Kevin Castañeda | Backend, Infraestructura |
| Danna | Data Science, Modelos |

## 📜 Licencia

MIT © Colombo Labs

---

<div align="center">

*Construido con ❤️ en Bogotá para el concurso [Datos al Ecosistema 2026](https://herramientas.datos.gov.co/)*

</div>

<div align="center">

<img src="https://em-content.zobj.net/source/apple/391/bus_1f68c.png" width="80" />

# Colombo Labs

### Movilidad urbana inteligente con datos abiertos e IA

*Transformamos datos públicos de transporte en herramientas que mejoran*
*la experiencia de millones de pasajeros en Bogotá*

[![Bogotá, Colombia](https://img.shields.io/badge/📍_Bogotá-Colombia-1a73e8?style=for-the-badge)]()
[![Datos Abiertos](https://img.shields.io/badge/📊_Datos-Abiertos-34a853?style=for-the-badge)]()
[![Deep Learning](https://img.shields.io/badge/🧠_Graph_Neural-Networks-9334e6?style=for-the-badge)]()
[![Docs](https://img.shields.io/badge/📖_Documentación-Starlight-f9ab00?style=for-the-badge)](https://colombo-labs.github.io/movicol-docs/)

---

</div>

## 🗺️ MoviCol

**Plataforma de movilidad inteligente** que unifica TransMilenio, SITP, vehículo particular, bicicleta y caminata en una sola experiencia. Predice congestión con modelos **Graph Attention Network (GAT)** entrenados sobre el grafo real de la red de transporte.

<table>
<tr>
<td width="50%">

### ✨ Funcionalidades

🗺️ Planificador de viajes multimodal<br/>
🧠 Predicción de congestión con GNN<br/>
📊 Métricas y alertas en tiempo real<br/>
🤖 Asistente IA conversacional<br/>
🗂️ Catálogo de rutas y estaciones<br/>
♿ Info de accesibilidad por estación<br/>
🌐 4 idiomas (ES, EN, FR, PT)<br/>
📱 PWA instalable en móvil

</td>
<td width="50%">

### 📊 En números

**153** estaciones TransMilenio indexadas<br/>
**125** rutas troncales con trazado real<br/>
**500+** paraderos SITP geolocalizados<br/>
**6** modos de transporte soportados<br/>
**4** modelos predictivos en producción<br/>
**6** repositorios open source<br/>
**2,000+** commits entre el equipo<br/>
**100%** datos públicos colombianos

</td>
</tr>
</table>

---

## 🏗️ Arquitectura

```
┌─────────────────────────────────────────────────────────────────────────┐
│                            CLIENTE (PWA)                                 │
│         React 19 · Vite · Leaflet · TailwindCSS · ArcGIS Maps          │
└───────────────────────────────────┬─────────────────────────────────────┘
                                    │ HTTP / WebSocket
                                    ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                          API GATEWAY (NestJS)                            │
│                                                                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌────────────┐ │
│  │   Grafo TM   │  │  Rutas SITP  │  │    Auth      │  │  WebSocket │ │
│  │  & Estaciones│  │  & Paraderos │  │  Google OAuth │  │  Real-time │ │
│  └──────┬───────┘  └──────┬───────┘  └──────────────┘  └────────────┘ │
│         │                  │                                            │
│         ▼                  ▼                                            │
│  ┌─────────────────────────────────┐     ┌─────────────────────────┐   │
│  │        PostGIS + TypeORM        │     │     Redis 7 (Cache)     │   │
│  │   Estaciones · Rutas · Grafos   │     │   TTL 60s-600s · Pub/Sub│   │
│  └─────────────────────────────────┘     └─────────────────────────┘   │
└───────────────────────────────────┬─────────────────────────────────────┘
                                    │ HTTP interno
                                    ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                      SERVICIO IA (FastAPI)                               │
│                                                                         │
│  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────────┐  │
│  │  GAT Predictor   │  │  Route Planner   │  │    MoviBot Agent     │  │
│  │  PyTorch + DGL   │  │  OSRM + ORS      │  │    LLM + Tools      │  │
│  │                  │  │                  │  │                      │  │
│  │ Congestión por   │  │ Routing multi-   │  │ Chat contextual      │  │
│  │ segmento y hora  │  │ modal con costos │  │ con acciones         │  │
│  └──────────────────┘  └──────────────────┘  └──────────────────────┘  │
│                                                                         │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │              NetworkX — Grafo de la red de transporte             │   │
│  │         Nodos: estaciones/paradas  ·  Edges: segmentos viales    │   │
│  └──────────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────────┘

                    ┌────────────────────────────┐
                    │    FUENTES EXTERNAS         │
                    │                            │
                    │  🗺️  OSRM (routing)        │
                    │  🌡️  Open-Meteo (clima)    │
                    │  📍  Nominatim (geocoding) │
                    │  🏗️  Overpass (POIs)       │
                    │  🚨  TM alerts (scraping)  │
                    │  🗺️  ArcGIS (basemaps)     │
                    └────────────────────────────┘
```

---

## 📦 Repositorios

| Repo | Stack | Descripción |
|:-----|:------|:------------|
| [`movicol-frontend`](https://github.com/colombo-labs/movicol-frontend) | React 19 · Vite · Leaflet · TailwindCSS | App PWA con mapa interactivo, planificador y chat |
| [`movicol-backend`](https://github.com/colombo-labs/movicol-backend) | NestJS · TypeORM · Redis · PostGIS | API REST, WebSocket, cache y grafo de transporte |
| [`movicol-ai`](https://github.com/colombo-labs/movicol-ai) | FastAPI · PyTorch · NetworkX · OSRM | Predicción GNN, routing multimodal y agente IA |
| [`movicol-data`](https://github.com/colombo-labs/movicol-data) | Python · PostGIS · Pandas | ETL de datos abiertos: TM, SITP, siniestralidad, red vial |
| [`movicol-infra`](https://github.com/colombo-labs/movicol-infra) | Docker Compose · GitHub Actions | Infraestructura, CI/CD con MegaLinter + SonarCloud |
| [`movicol-docs`](https://github.com/colombo-labs/movicol-docs) | Astro Starlight | Documentación: arquitectura CRISP-ML, API, guías |

---

## 🛠️ Stack tecnológico

<div align="center">

![React](https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript_5-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostGIS-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis_7-DC382D?style=flat-square&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![SonarCloud](https://img.shields.io/badge/SonarCloud-F3702A?style=flat-square&logo=sonarcloud&logoColor=white)

</div>

---

## 📊 Fuentes de datos abiertos

| Fuente | Datos | Uso |
|--------|-------|-----|
| [TransMilenio S.A.](https://www.transmilenio.gov.co/) | Estaciones, troncales, demanda, alertas | Grafo TM, predicción, alertas live |
| [SITP](https://www.sitp.gov.co/) | Rutas zonales, alimentadoras, paraderos | Grafo SITP, routing zonal |
| [Datos Abiertos Bogotá](https://datosabiertos.bogota.gov.co/) | Siniestralidad vial, red de ciclorrutas | Capas de riesgo, rutas seguras |
| [OpenStreetMap](https://www.openstreetmap.org/) | Red vial, POIs, infraestructura | Routing vehicular, puntos de interés |
| [datos.gov.co](https://www.datos.gov.co/) | Datasets nacionales de transporte | Contexto metropolitano |

---

## 👥 Equipo

<table>
<tr>
<td align="center"><b>Andrés Felipe Escobar Beltrán</b><br/><sub>Frontend · UX · DevOps</sub></td>
<td align="center"><b>Kevin Alexis Castañeda Narváez</b><br/><sub>Backend · Infraestructura</sub></td>
<td align="center"><b>Danna Valentina Martínez González</b><br/><sub>Data Science · Modelos IA</sub></td>
</tr>
</table>

---

<div align="center">

### 🏆 Participantes en [Datos al Ecosistema 2026](https://herramientas.datos.gov.co/)

*Categoría: Innovación Social — Transporte y Movilidad (Nivel Avanzado)*

---

📜 MIT License · Construido con ❤️ en Colombia 🇨🇴

</div>

# 🚀 Proyecto Semestral DevOps - Innovatech Chile

## Descripción del Proyecto

Aplicación web para gestión de despachos y ventas desarrollada con arquitectura de microservicios. El proyecto incluye:

- **Frontend**: React + Vite + Nginx
- **Backend**: Dos microservicios Spring Boot (Ventas y Despachos)
- **Base de Datos**: MySQL 8
- **Contenerización**: Docker + Docker Compose
- **Despliegue**: AWS EC2 (arquitectura multi-instancia)
- **CI/CD**: GitHub Actions (Build → Push → Deploy automático)

---

## 🏗️ Arquitectura

- **Frontend EC2** (Pública): Contenedor Nginx sirviendo la aplicación React
- **Backend EC2** (Privada): Microservicios Spring Boot + MySQL
- **Comunicación**: Frontend → Backend a través de IP privada
- **Persistencia**: Volúmenes Docker para MySQL

---

## 🛠️ Tecnologías Utilizadas

| Capa              | Tecnología                          |
|-------------------|-------------------------------------|
| Frontend          | React, Vite, Nginx                  |
| Backend           | Spring Boot, Java 17, Maven         |
| Base de Datos     | MySQL 8                             |
| Contenerización   | Docker, Docker Compose              |
| CI/CD             | GitHub Actions                      |
| Cloud             | AWS EC2 (VPC, Subredes pública/privada) |

---

## 📁 Estructura del Proyecto
proyecto-semestral-devops/
├── front_despacho/                # Frontend React
├── back-Ventas_SpringBoot/        # Microservicio Ventas
├── back-Despachos_SpringBoot/     # Microservicio Despachos
├── docker-compose-frontend.yml
├── docker-compose-backend.yml
├── .github/workflows/             # Pipeline CI/CD
├── Dockerfile (en cada servicio)
└── README.md


---

## 🐳 Docker

### Dockerfiles
- **Multi-stage builds** para optimizar tamaño de imágenes
- **Usuario no-root** por seguridad
- Limpieza de capas y buenas prácticas

### Comandos principales

**Frontend:**
```bash
docker compose -f docker-compose-frontend.yml up -d

Backend:
docker compose -f docker-compose-backend.yml up -d


🚀 CI/CD - GitHub Actions
El pipeline se activa con cada push a la rama deploy:

Construye las 3 imágenes Docker
Publica las imágenes en Docker Hub
Despliega automáticamente en la instancia frontend-ec2

Estado del pipeline: <img src="https://github.com/Vi8let/proyecto-semestral-devops/actions/workflows/docker-image.yml/badge.svg" alt="GitHub Actions">

🌐 Acceso a la Aplicación

Frontend: http://54.173.145.213
Backend Ventas: http://10.0.142.109:8080 (privado)
Backend Despachos: http://10.0.142.109:8081 (privado)


🔧 Decisiones Técnicas (Justificación)

Multi-stage builds: Reducir tamaño de imágenes y mejorar seguridad
Named volumes para MySQL: Persistencia de datos entre reinicios
Docker Hub: Facilidad y rapidez para proyecto académico
Separación de docker-compose: Mayor claridad y mantenimiento
Rama deploy: Cumplimiento de buenas prácticas DevOps


📋 Requisitos Cumplidos

 Contenerización con Docker (multi-stage + usuario no-root)
 Persistencia de datos con volúmenes
 Pipeline CI/CD completo (Build → Push → Deploy)
 Despliegue en AWS EC2 (arquitectura VPC)
 Comunicación segura Frontend ↔ Backend
 Documentación técnica


Proyecto desarrollado como parte de la Evaluación Intro a Herramientas DevOps

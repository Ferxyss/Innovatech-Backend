# Innovatech Backend

Backend del sistema Innovatech desarrollado para la Evaluación Parcial N°2 de la asignatura Introducción a Herramientas DevOps.

La solución implementa microservicios Spring Boot desplegados en AWS EC2 mediante Docker, Docker Compose y GitHub Actions.

---

## Tecnologías Utilizadas

- Spring Boot
- Java 17
- Maven
- Docker
- Docker Compose
- MySQL 8
- Docker Hub
- GitHub Actions
- AWS EC2
- Linux

---

## Características Implementadas

- Arquitectura basada en microservicios.
- Dockerfile multi-stage.
- Usuario no root.
- Docker Compose para orquestación.
- Persistencia de datos mediante Docker Volumes.
- CI/CD automatizado.
- Backend privado en AWS.
- Comunicación segura mediante Security Groups.
- Integración con frontend público.

---

## Arquitectura

La solución implementa:

- EC2 pública para Frontend.
- EC2 privada para Backend.
- EC2 privada para Base de Datos.
- Comunicación interna mediante IP privada.
- Segmentación de red mediante Security Groups.

---

## Servicios Backend

El backend se compone de:

- Microservicio Ventas.
- Microservicio Despachos.
- Base de datos MySQL.

---

## Persistencia de Datos

La persistencia se implementó utilizando Docker Volumes.

Tipo utilizado:

```bash
Named Volume
```

Objetivo:

- Mantener la información aunque los contenedores sean reiniciados.
- Facilitar administración y continuidad operativa.
- Separar los datos del ciclo de vida del contenedor.

---

## CI/CD

El pipeline realiza automáticamente:

1. Build de imágenes Docker.
2. Push hacia Docker Hub.
3. Deploy automático en EC2 Backend.
4. Actualización automática de contenedores.

---

## Docker Hub

Imágenes utilizadas:

```bash
ferxyss/innovatech-ventas:latest
ferxyss/innovatech-despachos:latest
```

---

## Ejecución Local

Levantar servicios:

```bash
docker-compose up -d
```

Ver contenedores:

```bash
docker ps
```

Ver logs:

```bash
docker logs api_ventas
docker logs api_despachos
```

---

## Seguridad Implementada

- Usuario no root.
- Backend privado.
- Base de datos privada.
- Security Groups segmentados.
- Comunicación interna privada.
- Secrets en GitHub Actions.
- SSH mediante llave PEM.

---

## Integración Front → Back

El frontend consume los endpoints backend utilizando comunicación privada dentro de la VPC de AWS.

Esto permite:

- Mayor seguridad.
- Menor exposición pública.
- Escalabilidad.
- Separación de responsabilidades.

---

## Integrantes

- Fernanda Paredes

---

## Asignatura

**ISY1101 - Introducción a Herramientas DevOps**

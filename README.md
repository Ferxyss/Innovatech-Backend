# Innovatech Backend

Backend del sistema **Innovatech Chile**, desarrollado para la
Evaluación Parcial de la asignatura **Introducción a Herramientas
DevOps**.

La solución está basada en una arquitectura de microservicios
desarrollada con Spring Boot y desplegada sobre **Amazon EKS
(Kubernetes)**. El proceso de integración y despliegue continuo se
encuentra automatizado mediante **GitHub Actions**, mientras que las
imágenes Docker son almacenadas en **Amazon Elastic Container Registry
(ECR)**.

------------------------------------------------------------------------

# Tecnologías utilizadas

-   Java 17
-   Spring Boot
-   Maven
-   Docker
-   Kubernetes
-   Amazon EKS
-   Amazon ECR
-   GitHub Actions
-   MySQL 8
-   AWS Cloud

------------------------------------------------------------------------

# Arquitectura

El backend está compuesto por:

-   Microservicio de Ventas.
-   Microservicio de Despachos.
-   Base de datos MySQL.

Cada servicio se ejecuta como un Deployment independiente dentro del
clúster de Kubernetes y se comunica mediante Services de tipo ClusterIP.

------------------------------------------------------------------------

# Características implementadas

-   Arquitectura basada en microservicios.
-   Contenedores Docker para cada servicio.
-   Despliegue en Amazon EKS.
-   Deployments y Services independientes.
-   Horizontal Pod Autoscaler (HPA).
-   Pipeline CI/CD con GitHub Actions.
-   Imágenes almacenadas en Amazon ECR.
-   Despliegue automático mediante Rolling Update.
-   Gestión segura de credenciales con GitHub Secrets.

------------------------------------------------------------------------

# Pipeline CI/CD

El flujo automatizado realiza:

1.  Descarga del código desde GitHub.
2.  Compilación del proyecto con Maven.
3.  Construcción de imágenes Docker.
4.  Publicación en Amazon ECR.
5.  Conexión al clúster Amazon EKS.
6.  Actualización automática de los Deployments.

------------------------------------------------------------------------

# Kubernetes

Recursos utilizados:

-   Deployment de Ventas.
-   Deployment de Despachos.
-   Deployment de MySQL.
-   Services internos.
-   Horizontal Pod Autoscaler (HPA).

Los manifiestos YAML se encuentran en la carpeta **k8s/**.

------------------------------------------------------------------------

# Variables de entorno

La configuración de la aplicación utiliza variables de entorno definidas
en Kubernetes para la conexión con MySQL:

-   SPRING_DATASOURCE_URL
-   SPRING_DATASOURCE_USERNAME
-   SPRING_DATASOURCE_PASSWORD

------------------------------------------------------------------------

# Ejecución local

``` bash
mvn clean package
docker build -t innovatech-backend .
docker-compose up -d
```

------------------------------------------------------------------------

# Seguridad

-   GitHub Secrets para credenciales AWS.
-   Imágenes privadas en Amazon ECR.
-   Comunicación interna mediante Kubernetes Services.
-   Base de datos accesible solo desde el clúster.
-   Credenciales fuera del repositorio.

------------------------------------------------------------------------

# Estructura del proyecto

``` text
Backend-deploy/
├── back-Ventas_SpringBoot/
├── back-Despachos_SpringBoot/
├── k8s/
├── .github/
│   └── workflows/
│       └── deploy-backend.yml
└── docker-compose.yml
```

------------------------------------------------------------------------

# Integrantes

-   Claudio Rojas
-   Fernanda Paredes

------------------------------------------------------------------------

# Asignatura

**ISY1101 - Introducción a Herramientas DevOps**

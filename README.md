# Fintech Core — proyecto académico

Aplicación full stack desarrollada como proyecto de aprendizaje sobre arquitectura de software y despliegue con contenedores. Este repositorio es un fork de [cesar-devsenior/CleanArchitecture-G1-fintech-core-app](https://github.com/cesar-devsenior/CleanArchitecture-G1-fintech-core-app); conserva la atribución del proyecto original y los cambios de este fork están disponibles en el historial de commits.

> **Estado:** proyecto académico/de demostración. La configuración permite levantar los componentes localmente con Docker Compose, pero eso no significa que la aplicación esté auditada o lista para operar en producción.

## Tecnologías

- **Backend:** Node.js, Express, TypeScript y Prisma.
- **Frontend:** React y Vite, servido por Nginx.
- **Base de datos:** PostgreSQL.
- **Contenedores:** Docker y Docker Compose.

## Estructura

- `backend/`: API REST.
- `frontend/`: aplicación web.
- `docker-compose.yml`: servicios locales de PostgreSQL, backend y frontend.

## Requisitos

- Docker y Docker Compose.
- Git para clonar el repositorio.

## Ejecución local

1. Clone este repositorio y entre a su carpeta.
2. Copie el archivo de ejemplo de variables:

   ```bash
   cp .env.example .env
   ```

3. Revise y configure los valores de `.env` para su equipo. No publique secretos reales.
4. Valide la configuración y levante los servicios:

   ```bash
   docker compose config
   docker compose up -d --build
   docker compose ps
   ```

URLs locales configuradas:

- Frontend: http://localhost:8081
- Backend: http://localhost:3001
- Health check: http://localhost:3001/health
- PostgreSQL: localhost:5434

Para revisar registros:

```bash
docker compose logs -f backend
docker compose logs -f postgres-db
```

Para detener los servicios:

```bash
docker compose down
```

Para borrar también los datos del volumen local de PostgreSQL:

```bash
docker compose down -v
```

## Pruebas y compilación

Backend:

```bash
cd backend
pnpm install
pnpm test --run
pnpm build
```

Frontend:

```bash
cd frontend
pnpm install
pnpm test --run
pnpm build
```

## Alcance y contribuciones

Este trabajo se desarrolló en contexto académico. Revise el historial de commits de este fork para distinguir los cambios realizados aquí del código heredado del repositorio original. Antes de usar cualquier configuración fuera de un entorno local, deben revisarse seguridad, secretos, migraciones, permisos, monitoreo y pruebas.

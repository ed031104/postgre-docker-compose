# Postgre Docker Compose

Este repositorio contiene una configuración mínima de Docker Compose para levantar una base de datos PostgreSQL con soporte para `pgvector`.

## Qué hace el archivo `docker-compose.yaml`

El archivo define un único servicio llamado `postgres` con estas características:

- Usa la imagen `pgvector/pgvector:pg17`, que incluye PostgreSQL 17 con la extensión `pgvector`.
- Expone el puerto `5432` para permitir conexiones desde tu máquina local.
- Define credenciales y una base de datos inicial mediante variables de entorno:
  - Usuario: `postgres`
  - Contraseña: `postgres`
  - Base de datos: `cv_analysis`
- Monta un volumen persistente llamado `postgres_data` para conservar los datos aunque el contenedor se detenga o se elimine.

## Cómo ejecutarlo

1. Asegúrate de tener Docker y Docker Compose instalados.
2. En la raíz del proyecto, levanta el contenedor con:

```bash
docker compose up -d
```

3. Verifica que el contenedor esté corriendo con:

```bash
docker compose ps
```

4. Si quieres ver los logs:

```bash
docker compose logs -f
```

## Cómo detenerlo

Para detener los servicios:

```bash
docker compose down
```

Si también quieres eliminar el volumen y borrar los datos persistidos:

```bash
docker compose down -v
```

## Conexión a la base de datos

Puedes conectarte usando estos datos:

- Host: `localhost`
- Puerto: `5432`
- Usuario: `postgres`
- Contraseña: `postgres`
- Base de datos: `cv_analysis`

## Nota

Si el puerto `5432` ya está ocupado en tu máquina, modifica el mapeo de puertos en `docker-compose.yaml` antes de iniciar el contenedor.
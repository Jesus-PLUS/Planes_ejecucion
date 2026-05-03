# Pagila Database Setup

Base de datos PostgreSQL Pagila configurada con Docker Compose.

## Requisitos

- Docker Desktop instalado
- Docker Compose v1.29+

## Instalación

1. **Copiar variables de entorno:**
   ```bash
   cp .env.example .env
   ```

2. **Editar `.env` si es necesario:**
   - Cambiar `POSTGRES_PASSWORD` por una contraseña segura
   - Ajustar `POSTGRES_PORT` si el puerto 5432 está en uso

3. **Iniciar la base de datos:**
   ```bash
   docker-compose up -d
   ```

4. **Verificar que está corriendo:**
   ```bash
   docker-compose ps
   ```

## Conexión

Desde cualquier cliente PostgreSQL:
```
Host: localhost
Puerto: 5432 (o el configurado en .env)
Usuario: postgres (o el configurado en .env)
Base de datos: pagila
```

### Ejemplo con psql:
```bash
psql -h localhost -U postgres -d pagila
```

## Comandos útiles

```bash
# Ver logs
docker-compose logs -f postgres

# Detener
docker-compose down

# Eliminar todo (volumen incluido)
docker-compose down -v

# Ejecutar comando en el contenedor
docker-compose exec postgres psql -U postgres -d pagila
```

## Seguridad

⚠️ **Importante:** El archivo `.env` contiene contraseñas y NO debe commitearse al repositorio.

El archivo `.env.example` es un template con valores de ejemplo para nuevos desarrolladores.

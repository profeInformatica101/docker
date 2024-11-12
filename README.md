
# Docker Moodle Setup

Este repositorio contiene una configuración básica de Docker para ejecutar Moodle con MariaDB como base de datos. Utiliza `docker-compose` para crear y gestionar los contenedores de forma rápida y sencilla.

## Requisitos

- Docker
- Docker Compose

## Contenido del repositorio

- `docker-compose.yml`: Archivo de configuración de Docker Compose para desplegar Moodle y MariaDB.

## Comandos Básicos

### 1. Levantar el entorno

Para iniciar el entorno de Moodle y MariaDB, ejecuta el siguiente comando en el directorio del repositorio:

```bash
docker-compose up -d
```

Este comando levantará los contenedores en segundo plano (`-d` para "detached mode").

### 2. Verificar el estado de los contenedores

Para ver el estado de los contenedores en ejecución:

```bash
docker ps
```

Este comando muestra los contenedores activos y sus puertos mapeados.

### 3. Acceder a los logs de un contenedor

Para ver los logs de un contenedor específico, como el de Moodle o MariaDB:

```bash
docker-compose logs moodle
docker-compose logs mariadb
```

También puedes ver los logs en tiempo real usando la opción `-f`:

```bash
docker-compose logs -f moodle
```

### 4. Detener el entorno

Para detener los contenedores sin eliminar los datos:

```bash
docker-compose down
```

Este comando detiene y elimina los contenedores, pero preserva los volúmenes (datos).

### 5. Reiniciar el entorno

Para reiniciar los contenedores (útil después de hacer cambios en `docker-compose.yml`):

```bash
docker-compose down
docker-compose up -d
```

### 6. Ejecutar comandos dentro de un contenedor

Si necesitas ejecutar comandos dentro del contenedor de Moodle o MariaDB, usa el siguiente comando:

```bash
docker exec -it <nombre_del_contenedor> bash
```

Ejemplo para acceder al contenedor de Moodle:

```bash
docker exec -it moodle_moodle_1 bash
```

### 7. Eliminar todos los volúmenes y contenedores

Si deseas eliminar completamente los datos y empezar desde cero:

```bash
docker-compose down -v
```

> **Nota:** Esto eliminará todos los volúmenes de datos, incluidas las bases de datos.

## Acceso a Moodle

Una vez que los contenedores estén en ejecución, podrás acceder a Moodle en [http://localhost:8080](http://localhost:8080).

## Personalización

Puedes ajustar el archivo `docker-compose.yml` para cambiar las configuraciones de Moodle y MariaDB según tus necesidades. Asegúrate de reiniciar los contenedores después de realizar cualquier cambio en este archivo.

## Contribuciones

Las contribuciones son bienvenidas. Si tienes alguna mejora o encuentras un problema, siéntete libre de abrir un issue o hacer un pull request.

## Licencia

Este proyecto está bajo la licencia MIT. Consulta el archivo `LICENSE` para obtener más detalles.

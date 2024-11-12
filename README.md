# Docker Ejemplos - Comandos Generales

Este repositorio contiene varios ejemplos de configuraciones y aplicaciones Docker. A continuación, se muestran algunos comandos generales útiles para gestionar contenedores, imágenes y redes en Docker.

## Comandos Básicos de Docker

### 1. Listar Contenedores

- Para listar los contenedores activos:
  ```bash
  docker ps
  ```
- Para listar todos los contenedores, incluyendo los detenidos:
  ```bash
  docker ps -a
  ```

### 2. Iniciar y Detener Contenedores

- Iniciar un contenedor específico:
  ```bash
  docker start <nombre_del_contenedor>
  ```
- Detener un contenedor específico:
  ```bash
  docker stop <nombre_del_contenedor>
  ```

### 3. Eliminar Contenedores

- Eliminar un contenedor específico:
  ```bash
  docker rm <nombre_del_contenedor>
  ```
- Eliminar todos los contenedores detenidos:
  ```bash
  docker container prune
  ```

### 4. Gestionar Imágenes

- Listar todas las imágenes locales:
  ```bash
  docker images
  ```
- Eliminar una imagen específica:
  ```bash
  docker rmi <id_de_la_imagen>
  ```
- Eliminar todas las imágenes no usadas:
  ```bash
  docker image prune
  ```

### 5. Construir una Imagen

- Construir una imagen a partir de un Dockerfile en el directorio actual:
  ```bash
  docker build -t nombre_imagen .
  ```

### 6. Ejecutar un Contenedor

- Crear y ejecutar un contenedor a partir de una imagen:
  ```bash
  docker run -d --name nombre_contenedor nombre_imagen
  ```

  - `-d`: Ejecuta el contenedor en modo "detached" (en segundo plano).
  - `--name`: Asigna un nombre específico al contenedor.

### 7. Acceder a un Contenedor en Ejecución

- Acceder a un contenedor en modo interactivo:
  ```bash
  docker exec -it nombre_contenedor bash
  ```

### 8. Comandos para Docker Compose

- Levantar los servicios definidos en `docker-compose.yml` en segundo plano:
  ```bash
  docker-compose up -d
  ```
- Detener los servicios de `docker-compose`:
  ```bash
  docker-compose down
  ```
- Ver los logs de un servicio en tiempo real:
  ```bash
  docker-compose logs -f <nombre_servicio>
  ```

### 9. Redes en Docker

- Listar todas las redes:
  ```bash
  docker network ls
  ```
- Crear una red personalizada:
  ```bash
  docker network create nombre_red
  ```
- Conectar un contenedor a una red:
  ```bash
  docker network connect nombre_red nombre_contenedor
  ```

## Otros Comandos Útiles

- Ver el uso de espacio en disco por Docker:
  ```bash
  docker system df
  ```
- Limpiar todos los contenedores, imágenes y redes no utilizados:
  ```bash
  docker system prune -a
  ```
- Inspeccionar los detalles de un contenedor o imagen:
  ```bash
  docker inspect <nombre_contenedor_o_imagen>
  ```

## Diferencias Principales entre Dockerfile y docker-compose.yml

| Característica               | Dockerfile                           | docker-compose.yml                     |
|------------------------------|--------------------------------------|----------------------------------------|
| **Propósito**                | Crear una imagen Docker             | Orquestar y ejecutar múltiples contenedores |
| **Uso**                      | Construcción de imagen              | Configuración y despliegue de contenedores |
| **Formato**                  | Instrucciones de Docker (texto plano) | YAML                                  |
| **Comandos principales**     | `FROM`, `COPY`, `RUN`, `CMD`, etc.  | `services`, `build`, `volumes`, `networks`, `depends_on` |
| **Escalabilidad**            | Diseñado para una sola imagen       | Diseñado para múltiples contenedores   |
| **Ejemplo de aplicación**    | Empaquetar una app en una imagen    | Ejecutar una app con base de datos, caché, backend y frontend en contenedores separados |

## Conclusión

- **Dockerfile** es ideal para crear una imagen de una aplicación específica.
- **docker-compose.yml** es ideal para configurar y orquestar múltiples contenedores que trabajen en conjunto.

Usualmente, ambos archivos se usan en conjunto: el Dockerfile define cómo construir la imagen de la aplicación, mientras que el docker-compose.yml orquesta cómo se ejecutarán esa imagen y otros servicios adicionales en contenedores.

## Contribuciones

Las contribuciones son bienvenidas. Si tienes alguna mejora o encuentras un problema, siéntete libre de abrir un issue o hacer un pull request.

## Licencia

Este proyecto está bajo la licencia MIT. Consulta el archivo `LICENSE` para obtener más detalles.

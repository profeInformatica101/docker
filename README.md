# Docker Ejemplos - Comandos Generales

Este repositorio contiene varios ejemplos de configuraciones y aplicaciones Docker. A continuación, se muestran algunos comandos generales útiles para gestionar contenedores, imágenes y redes en Docker.

## Instalación de Docker en Linux 🐋

### 1. Actualizar el sistema
Ejecuta los siguientes comandos para actualizar los paquetes del sistema:
```bash
sudo apt update
sudo apt upgrade -y
```

### 2. Instalar dependencias necesarias
Instala los paquetes necesarios para permitir a Docker usar repositorios HTTPS:
```bash
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

### 3. Agregar la clave GPG oficial de Docker
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### 4. Agregar el repositorio de Docker
```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu focal stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### 5. Instalar Docker
```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

### 6. Verificar la instalación
Ejecuta el siguiente comando para verificar que Docker está correctamente instalado:
```bash
docker --version
```

### 7. Opcional: Ejecutar Docker sin sudo
Si deseas ejecutar Docker sin usar `sudo`:
```bash
sudo usermod -aG docker $USER
```
Después, reinicia tu sesión.

### 8. Instalar Docker Compose
Descarga e instala la última versión de Docker Compose:
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

## Comandos Básicos de Docker ⚙️

### 1. Listar Contenedores 🗄️
- Para listar los contenedores activos:
  ```bash
  docker ps
  ```
- Para listar todos los contenedores, incluyendo los detenidos:
  ```bash
  docker ps -a
  ```

### 2. Iniciar y Detener Contenedores ▶️⏹️
- Iniciar un contenedor específico:
  ```bash
  docker start <nombre_del_contenedor>
  ```
- Detener un contenedor específico:
  ```bash
  docker stop <nombre_del_contenedor>
  ```

### 3. Eliminar Contenedores 🗑️
- Eliminar un contenedor específico:
  ```bash
  docker rm <nombre_del_contenedor>
  ```
- Eliminar todos los contenedores detenidos:
  ```bash
  docker container prune
  ```

### 4. Gestionar Imágenes 🖼️
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

### 5. Construir una Imagen 🏠
- Construir una imagen a partir de un Dockerfile en el directorio actual:
  ```bash
  docker build -t nombre_imagen .
  ```

### 6. Ejecutar un Contenedor 🚀
- Crear y ejecutar un contenedor a partir de una imagen:
  ```bash
  docker run -d --name nombre_contenedor nombre_imagen
  ```

  - `-d`: Ejecuta el contenedor en modo "detached" (en segundo plano).
  - `--name`: Asigna un nombre específico al contenedor.

### 7. Acceder a un Contenedor en Ejecución 🛠️
- Acceder a un contenedor en modo interactivo:
  ```bash
  docker exec -it nombre_contenedor bash
  ```

### 8. Comandos para Docker Compose 📦
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

### 9. Redes en Docker 🌐
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

## Otros Comandos Útiles 🛠️

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

## Diferencias Principales entre Dockerfile y docker-compose.yml 🔝⚙️

| Característica               | Dockerfile                           | docker-compose.yml                     |
|------------------------------|--------------------------------------|----------------------------------------|
| **Propósito**                | Crear una imagen Docker             | Orquestar y ejecutar múltiples contenedores |
| **Uso**                      | Construcción de imagen              | Configuración y despliegue de contenedores |
| **Formato**                  | Instrucciones de Docker (texto plano) | YAML                                  |
| **Comandos principales**     | `FROM`, `COPY`, `RUN`, `CMD`, etc.  | `services`, `build`, `volumes`, `networks`, `depends_on` |
| **Escalabilidad**            | Diseñado para una sola imagen       | Diseñado para múltiples contenedores   |
| **Ejemplo de aplicación**    | Empaquetar una app en una imagen    | Ejecutar una app con base de datos, caché, backend y frontend en contenedores separados |

## Conclusión 🎯

- **Dockerfile** es ideal para crear una imagen de una aplicación específica.
- **docker-compose.yml** es ideal para configurar y orquestar múltiples contenedores que trabajen en conjunto.

Usualmente, ambos archivos se usan en conjunto: el Dockerfile define cómo construir la imagen de la aplicación, mientras que el docker-compose.yml orquesta cómo se ejecutarán esa imagen y otros servicios adicionales en contenedores.

## Contribuciones 🤝

Las contribuciones son bienvenidas. Si tienes alguna mejora o encuentras un problema, siéntete libre de abrir un issue o hacer un pull request.

## Licencia 📜

Este proyecto está bajo la licencia MIT. Consulta el archivo `LICENSE` para obtener más detalles.



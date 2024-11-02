# Examen-final---Pregunta-2
markdown
Copiar código
# Examen Final - Pregunta 2

Este proyecto orquesta contenedores de: 
**MySQL** y **phpMyAdmin** usando Docker y `docker-compose`. Incluye la configuración de una base de datos `testdb` con credenciales específicas y el acceso a la interfaz de phpMyAdmin para gestionar la base de datos.

## Estructura del Proyecto

### Servicios

1. **MySQL**: Servidor de base de datos configurado para crear una base de datos inicial (`testdb`).
2. **phpMyAdmin**: Interfaz gráfica para gestionar la base de datos MySQL desde el navegador.

## Requisitos

- **Docker** y **Docker Compose** instalados.
- Cuenta en **GitHub** para subir el repositorio.

## Configuración de Docker Compose

El archivo 

`docker-compose.yml` configura dos servicios principales:

- **MySQL** en el puerto `3306` del contenedor.
- **phpMyAdmin** en el puerto `8080` del host, con conexión al servicio MySQL.

### Ejemplo del archivo `docker-compose.yml`

```yaml
version: '3.8'

services:
  mysql:
    image: mysql:latest
    container_name: mysql_container
    environment:
      MYSQL_ROOT_PASSWORD: root_password
      MYSQL_DATABASE: testdb
      MYSQL_USER: testuser
      MYSQL_PASSWORD: testpassword
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    container_name: phpmyadmin_container
    environment:
      PMA_HOST: mysql
      PMA_PORT: 3306
    ports:
      - "8080:80"

# Acceso a phpMyAdmin: http://localhost:8080

volumes:
  mysql_data:
Instrucciones
Iniciar los contenedores:

Ejecuta el siguiente comando para levantar los contenedores en segundo plano:

shell
Copiar código
docker-compose up -d
Acceder a phpMyAdmin:

URL: http://localhost:8080
Usuario MySQL: root o testuser
Contraseñas: root_password (para root) o testpassword (para testuser)
Detener los contenedores:

Para detener y eliminar los contenedores:

shell
Copiar código
docker-compose down
Configuración de Git y GitHub
Inicialización del Repositorio
Cambiar a la rama main y agregar el repositorio remoto:

shell
Copiar código
git branch -M main
git remote add origin https://github.com/MagalyEscalera23/Examen-final---Pregunta-2.git
Confirmar la conexión con el repositorio remoto:

shell
Copiar código
git remote -v
Subir los Cambios a GitHub
Si es la primera vez, haz un pull con rebase para integrar los cambios remotos:

shell
Copiar código
git pull origin main --rebase
Luego, haz push al repositorio remoto:

shell
Copiar código
git push -u origin main
Notas
Asegúrate de que Docker esté corriendo antes de ejecutar docker-compose.
Si el puerto 3306 está ocupado, cambia el puerto externo en docker-compose.yml.
Acceso Rápido
phpMyAdmin: http://localhost:8080
Acceso Rápido
phpMyAdmin: http://localhost:8080
Copiar código

Este `README.md` describe el propósito del proyecto, cómo configurarlo y cómo interactuar con los servicios y el repositorio en GitHub.

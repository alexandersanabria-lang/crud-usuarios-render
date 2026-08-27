# CRUD Usuarios — Spring Boot + PostgreSQL

API REST para gestionar la entidad `Usuario` (id, nombre, email, edad), desarrollada con Java 25, Spring Boot 3.5.0 y Spring Data JPA sobre PostgreSQL. Incluye un frontend simple en `static/index.html` para probar el CRUD desde el navegador.

Proyecto para el Laboratorio N°2 del curso Desarrollo de Soluciones en la Nube — Tecsup.

## Endpoints

| Método | Ruta                  | Acción                       |
|--------|-----------------------|------------------------------|
| GET    | `/api/usuarios`       | Listar todos los usuarios    |
| GET    | `/api/usuarios/{id}`  | Buscar un usuario por id     |
| POST   | `/api/usuarios`       | Crear un usuario             |
| PUT    | `/api/usuarios/{id}`  | Actualizar un usuario        |
| DELETE | `/api/usuarios/{id}`  | Eliminar un usuario          |

## Ejecutar en local

1. Crear la base de datos en PostgreSQL:
   ```sql
   CREATE DATABASE usuarios_db;
   ```
2. Ajustar credenciales si son distintas a las predeterminadas en `src/main/resources/application.properties`, o exportarlas como variables de entorno:
   ```bash
   export SPRING_DATASOURCE_URL=jdbc:postgresql://localhost:5432/usuarios_db
   export SPRING_DATASOURCE_USERNAME=postgres
   export SPRING_DATASOURCE_PASSWORD=postgres
   ```
3. Compilar y ejecutar:
   ```bash
   mvn clean package -DskipTests
   java -jar target/crud-usuarios-0.0.1-SNAPSHOT.jar
   ```
4. Abrir `http://localhost:8080` en el navegador.

## Desplegar en Render

1. Crear una base de datos **PostgreSQL** en Render y copiar sus credenciales (host, usuario, contraseña, nombre de base de datos).
2. Crear un **Web Service** conectado a este repositorio de GitHub, con:
   - Entorno: `Java`
   - Comando de build: `mvn clean package -DskipTests`
   - Comando de inicio: `java -jar target/crud-usuarios-0.0.1-SNAPSHOT.jar`
3. En la sección **Environment** del servicio, agregar las variables:
   - `SPRING_DATASOURCE_URL`
   - `SPRING_DATASOURCE_USERNAME`
   - `SPRING_DATASOURCE_PASSWORD`

   con los datos de la base de datos creada en el paso 1.
4. Desplegar. Render construye el proyecto y expone la URL pública del servicio.

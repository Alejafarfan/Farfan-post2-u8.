# CRUD Estudiantes - Spring Boot + JPA/Hibernate

Aplicación web para gestionar estudiantes usando Spring Boot, Spring Data JPA e Hibernate con base de datos MySQL.

## Tecnologías usadas

- Java 17
- Spring Boot 3.x
- Spring Data JPA / Hibernate
- MySQL 8
- Thymeleaf
- Bean Validation

## Configuración de MySQL

Ejecutar en MySQL Command Line Client:

```sql
CREATE DATABASE estudiantes_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'appuser'@'localhost' IDENTIFIED BY 'apppass';
GRANT ALL PRIVILEGES ON estudiantes_db.* TO 'appuser'@'localhost';
FLUSH PRIVILEGES;
```

## Configuración de application.properties

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/estudiantes_db?useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true
spring.datasource.username=appuser
spring.datasource.password=apppass
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect

server.port=8080
```

## Cómo ejecutar

1. Clonar el repositorio
2. Configurar MySQL con los comandos de arriba
3. Verificar application.properties con tus credenciales
4. Ejecutar en la terminal:

```bash
./mvnw spring-boot:run
```

5. Abrir en el navegador: http://localhost:8080/estudiantes

## Estructura del proyecto
```
src/main/java/com/universidad/estudiantes/
├── EstudiantesApplication.java
├── controller/
│   └── EstudianteController.java
├── model/
│   └── Estudiante.java
├── repository/
│   └── EstudianteRepository.java
└── service/
    └── EstudianteService.java

src/main/resources/
├── application.properties
└── templates/
    └── estudiantes/
        ├── lista.html
        ├── formulario.html
        └── confirmar-eliminar.html
```
## Funcionalidades CRUD
- **Crear:** Formulario en `/estudiantes/nuevo` con validación de campos
- **Leer:** Lista completa en `/estudiantes`
- **Actualizar:** Formulario de edición en `/estudiantes/editar/{id}`
- **Eliminar:** Confirmación antes de borrar en `/estudiantes/eliminar/{id}`

## Capturas de pantalla

### Lista de estudiantes
1. Página principal con la lista de estudiantes
    <img src="https://res.cloudinary.com/dindlmikf/image/upload/v1776623682/Captura_de_pantalla_2026-04-19_131209_mgtgae.png" alt="Lista de estudiantes" width="600">

2. Formulario de creación de nuevo estudiante
   <img src="https://res.cloudinary.com/dindlmikf/image/upload/v1776623862/Captura_de_pantalla_2026-04-19_133722_hdclzj.png" alt="Crear estudiantes" width="600">

3. Lista de todos los estudiantes
 <img src="https://res.cloudinary.com/dindlmikf/image/upload/v1776623682/Captura_de_pantalla_2026-04-19_131156_d01evk.png" alt="mysql" width="600">
 <img src="https://res.cloudinary.com/dindlmikf/image/upload/v1776623682/Captura_de_pantalla_2026-04-19_131518_etq7ka.png" alt="listas de 3 estudiantes" width="600">
 <img src="https://res.cloudinary.com/dindlmikf/image/upload/v1776623682/Captura_de_pantalla_2026-04-19_133054_oal1bo.png" width="600">

4. Formulario de edición de estudiante
   <img src="https://res.cloudinary.com/dindlmikf/image/upload/v1776624485/Captura_de_pantalla_2026-04-19_134751_qmmxi9.png" alt="editar estudiantes" width="600">
   <img src="https://res.cloudinary.com/dindlmikf/image/upload/v1776623682/Captura_de_pantalla_2026-04-19_131643_jwvyaz.png" alt="editar estudiantes" width="600">


5. Pantalla de confirmación de eliminación
    <img src="https://res.cloudinary.com/dindlmikf/image/upload/v1776623682/Captura_de_pantalla_2026-04-19_131737_afawmn.png" alt="confirmar eliminación" width="600">
    <img src="https://res.cloudinary.com/dindlmikf/image/upload/v1776623682/Captura_de_pantalla_2026-04-19_131728_hpdirq.png" alt="confirmar eliminación" width="600">

6. Mensajes de validación de campos obligatorios
    <img src="https://res.cloudinary.com/dindlmikf/image/upload/v1776623682/Captura_de_pantalla_2026-04-19_133009_xy8tvc.png" alt="validación de campos" width="600">

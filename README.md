# Gestión Académica - Relación ManyToMany con Spring Boot y JPA
Sistema de gestión académica que implementa la relación @ManyToMany entre Curso y Estudiante usando Spring Data JPA e Hibernate.

## Tecnologías
- Java 17
- Spring Boot 3.5.13
- Spring Data JPA / Hibernate
- MySQL 8.0
- Thymeleaf
- Maven

## Estructura del proyecto

        estudiantes/
        ├── src/main/java/com/universidad/estudiantes/
        │   ├── EstudiantesApplication.java          # Clase principal
        │   ├── model/
        │   │   ├── Estudiante.java                  # Entidad con lado inverso @ManyToMany
        │   │   └── Curso.java                       # Entidad propietaria con @JoinTable
        │   ├── repository/
        │   │   ├── EstudianteRepository.java        # Repositorio JPA de estudiantes
        │   │   └── CursoRepository.java             # Repositorio con JOIN FETCH para evitar N+1
        │   ├── service/
        │   │   ├── EstudianteService.java           # Lógica CRUD de estudiantes
        │   │   └── CursoService.java                # Lógica de inscripcion y desinscripcion
        │   └── controller/
        │       ├── EstudianteController.java        # Rutas /estudiantes
        │       └── CursoController.java             # Rutas /cursos e inscripciones
        └── src/main/resources/
        ├── templates/
        │   ├── estudiantes/                     # Vistas de estudiantes
        │   └── cursos/                          # Vistas de cursos e inscripcion
        └── application.properties              # Configuracion de base de datos

## Qué hace cada componente

- Estudiante.java: entidad JPA con lado inverso de la relacion ManyToMany. Usa mappedBy para indicar que Curso es el lado propietario.
- Curso.java: entidad JPA propietaria de la relacion. Define la tabla de union curso_estudiante con @JoinTable. Incluye helper methods agregarEstudiante y quitarEstudiante para sincronizar ambos lados de la relacion.
- CursoRepository.java: usa @Query con LEFT JOIN FETCH para cargar los estudiantes de cada curso en una sola consulta, evitando el problema N+1.
- CursoService.java: gestiona las operaciones de inscripcion y desinscripcion usando los helper methods de la entidad Curso dentro de transacciones.

## Cómo ejecutar

1. Clonar el repositorio:
   git clone https://github.com/Alejafarfan/Farfan-post2-u8.git

2. Configurar la contraseña de MySQL en application.properties

3. Ejecutar:
   ./mvnw spring-boot:run

4. Abrir en el navegador:
    - Estudiantes: http://localhost:8080/estudiantes
    - Cursos e inscripciones: http://localhost:8080/cursos

## Operaciones disponibles

- Crear, editar y eliminar estudiantes
- Crear cursos con nombre y creditos
- Inscribir estudiantes en cursos
- Desinscribir estudiantes de cursos
- Ver cuántos estudiantes tiene cada curso

## Verificar en MySQL
    USE estudiantes_db;
    SHOW TABLES;
    SELECT * FROM curso_estudiante;
    SELECT * FROM estudiantes;

## Capturas
1. crear cursos:
   <img alt="crear cursos" src="https://res.cloudinary.com/dindlmikf/image/upload/v1776639304/Captura_de_pantalla_2026-04-19_175452_sjouyx.png">
2. lista de cursos:
   <img alt="lista de cursos" src="https://res.cloudinary.com/dindlmikf/image/upload/v1776639180/Captura_de_pantalla_2026-04-19_174056_xpdap1.png">
3. inscripcion a cursos:
   <img alt="cursos inscripcion" src="https://res.cloudinary.com/dindlmikf/image/upload/v1776639180/Captura_de_pantalla_2026-04-19_174115_kwaly2.png">
4. desinscripcion a cursos:
   <img alt="cursos desinscripcion" src="https://res.cloudinary.com/dindlmikf/image/upload/v1776639180/Captura_de_pantalla_2026-04-19_174430_a0ihci.png">
5. base de datos de cursos:
   <img alt="Base de datos de cursos y estudiantes" src="https://res.cloudinary.com/dindlmikf/image/upload/v1776639180/Captura_de_pantalla_2026-04-19_174419_s0c0e3.png" >


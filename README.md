# Sistema de Gestión Escolar

Este proyecto es un **Sistema de Gestión Escolar** desarrollado con **Spring Boot** (backend) y **React** (frontend) . 

El objetivo es brindar una solución integral para instituciones educativas, permitiendo gestionar alumnos, docentes, preceptores, materias, calificaciones, reportes y usuarios con distintos roles del sistema de manera eficiente.

---

## Tecnologías utilizadas

### ➡️ Backend
- **Spring Boot** (Core del ecosistema Java)
- **Spring Data JPA** (Persistencia de datos y repositorios)
- **Spring Security** con **JWT** (Autenticación basada en tokens)
- **MySQL** (Base de datos relacional)
- **Lombok** & **Validation** (Optimización de código y validación de DTOs)

### ➡️ Frontend
- **React + Vite** 
- **React Router DOM** (Enrutamiento dinámico)
- **Context API** (Gestión global de autenticación y roles)
- **Bootstrap / CSS** (Diseño responsivo y componentes visuales)
- **React Icons** & **React Toastify** (Notificaciones interactivas)

---

## Funcionalidades principales

* **Gestión de Usuarios:** Creación, edición y eliminación de usuarios con asignación estricta de permisos.
* **Gestión de Docentes:** Administración de datos personales, contacto, materias asignadas, disponibilidad y desempeño.
* **Gestión de Alumnos:** Registro de información académica, tutores, legajos y estados de regularidad.
* **Gestión de Materias y Cursos:** Creación de materias, asignación de docentes y organización de cursos/divisiones.
* **Preceptores:** Asignación de preceptores a cursos y seguimiento de alumnos.
* * **Reportes Académicos:**
    - Legajo de alumnos
    - Alumnos libres
    - Notas por período y materia
    - Asistencia y llegadas tarde
    - Ranking de alumnos
    - Informe anual de desempeño docente
    - Carga horaria docente
    - Y más...

* **Autenticación y Seguridad:** Login  mediante JWT y control de accesos por roles en todas las rutas.

---

## Control de Accesos 

El sistema segmenta los permisos en el frontend según el perfil del usuario autenticado:

* `ROLE_ADMIN`: Acceso completo e ilimitado a todas las funcionalidades y configuraciones del sistema.
* `ROLE_DIRECTOR`: Gestión avanzada (usuarios clave, reportes, organización) según configuración.
* `ROLE_PRECEPTOR`: Gestión de alumnos y asistencia; acceso a reportes específicos.
* `ROLE_DOCENTE`: Carga de calificaciones, generación de reportes pedagógicos y reserva de espacios físicos.
* `ROLE_AUXILIAR`: Solo puede gestionar  los **Espacios Áulicos** (Ruta: *Configuración → Gestionar Espacios*). No posee acceso al resto de las secciones.

---

## Capturas del sistema

### Login y autenticación

<img width="885" height="709" alt="image" src="https://github.com/user-attachments/assets/bbfd0d5e-f1d9-4c19-9058-b5d9bdc8705f" />


### Dashboard Principal
<img width="1919" height="919" alt="image" src="https://github.com/user-attachments/assets/bbf1e620-6ea1-4b2b-bc6a-0ba2722904fb" />


### Materias
<img width="1920" height="918" alt="image" src="https://github.com/user-attachments/assets/9244fd49-d7f3-491a-98a9-7c4efaf1189d" />


### Asistencia de alumnos
<img width="1918" height="918" alt="image" src="https://github.com/user-attachments/assets/501dfa42-6a7b-4516-a031-e50e4e03aace" />

### Gestión de usuarios y roles
<img width="1919" height="918" alt="image" src="https://github.com/user-attachments/assets/ebfc5926-b0be-48f4-aff3-27441312aeae" />


### Mesa de Examen
<img width="1919" height="916" alt="image" src="https://github.com/user-attachments/assets/262c57a0-d870-49a0-9af3-3427efa71c00" />


### Reportes del Sistema
<img width="1920" height="916" alt="image" src="https://github.com/user-attachments/assets/55306c7a-123d-46ed-9998-24272dfeb604" />

---

## 📂 Estructura del proyecto (Frontend)

```text
/frontend
├── src
│   ├── Components/     # Componentes reutilizables de la interfaz
│   ├── Context/        # Estado global (Autenticación y Roles)
│   ├── Pages/          # Vistas principales del sistema
│   ├── Routes/         # Definición y protección de rutas
│   ├── Services/       # Consumo de APIs (Cliente HTTP)
│   ├── App.jsx         # Componente raíz
│   └── main.jsx        # Punto de entrada de la aplicación
```

## 📂 Estructura del proyecto (Backend)

```text
/backend/src/main/java/com/luterano/app
├── auth/               # Configuración de Spring Security y filtros JWT
├── command/            # Comandos del sistema o lógica CQRS
├── config/             # Clases de configuración global (CORS, Beans, Swagger)
├── controller/         # Endpoints REST (Controladores de la API)
├── dto/                # Objetos de Transferencia de Datos (Data Transfer Objects)
├── entities/           # Modelos y entidades de persistencia (JPA / Hibernate)
├── event/              # Manejo de eventos internos del sistema
├── exceptions/         # Centralización y manejo global de errores (Exception Handler)
├── listener/           # Escuchadores de eventos asíncronos o de ciclo de vida
├── mappers/            # Conversión manual o automática entre Entidades y DTOs
├── repository/         # Interfaces de acceso a datos (Spring Data JPA)
├── request/            # Modelos específicos para validar peticiones entrantes
├── response/           # Estructuras unificadas para respuestas de la API
├── service/            # Capa de lógica de negocio (Servicios)
├── specification/      # Consultas dinámicas avanzadas con Criteria API
├── utils/              # Clases de utilidad general y helpers
├── validation/         # Anotaciones y validadores personalizados
├── Datalnitializer.java # Inicialización de datos maestros del sistema
└── LuteranoApplication.java # Clase principal y punto de entrada de Spring Boot
```

---

##  Configuración de entorno (`application.properties`)

El backend centraliza sus credenciales y variables operativas mediante el sistema de propiedades de Spring Boot. Gracias a la configuración de Hibernate, **las tablas de la base de datos se generan y actualizan de forma automática** al iniciar la aplicación.

### Gestión de archivos de propiedades


| Archivo | ¿Se trackea en Git? | Uso Principal |
| :--- | :---: | :--- |
| `application.properties.example` | **Sí** | Plantilla de referencia pública con variables vacías. |
| `application.properties` | **No** | Configuración local (Conexión a MySQL local, llaves secretas). |

### 🛠️ Pasos para desarrollo local

1. Crea tu archivo de propiedades local duplicando la plantilla de ejemplo:
   ```bash
   cp src/main/resources/application.properties.example src/main/resources/application.properties
   ```
2. Abre `application.properties` y configura los accesos a tu servidor de MySQL y el servicio de mensajería:
   ```properties
   spring.application.name=luterano

   # Configuración de Base de Datos (MySQL)
   # Nota: 'createDatabaseIfNotExist=true' creará el esquema automáticamente si no existe.
   spring.datasource.url=jdbc:mysql://localhost:3306/luterano?createDatabaseIfNotExist=true&serverTimezone=America/Argentina/Buenos_Aires
   spring.datasource.username=tu_usuario_root
   spring.datasource.password=tu_contraseña_mysql
   spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

   # Configuración de Hibernate (Mapeo Automático)
   spring.jpa.properties.hibernate.globally_quoted_identifiers=true
   spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect
   spring.jpa.hibernate.ddl-auto=update
   spring.datasource.initialization-mode=always

   # Configuración de Correo Electrónico (Servidor SMTP)
   spring.mail.host=smtp.gmail.com
   spring.mail.port=587
   spring.mail.username=tu_correo@gmail.com
   spring.mail.password=tu_token_de_aplicacion_smtp
   spring.mail.properties.mail.smtp.auth=true
   spring.mail.properties.mail.smtp.starttls.enable=true
   email.enabled=false
   ```
3. Asegúrate de tener levantado tu servidor local de MySQL con el esquema creado (`luterano_db`).
4.Ejecuta el backend utilizando tu IDE preferido (como IntelliJ IDEA) o mediante la terminal usando el servidor embebido de Maven:
   ```bash
   ./mvnw spring-boot:run
   ```

> [!TIP]
> ###  Automatización del Esquema
> Al tener la propiedad `ddl-auto=update`, no necesitas importar ningún archivo `.sql` externo para levantar el sistema. Spring Boot creará la estructura completa por ti en tu primer arranque.

### ¿Cómo funciona la seguridad y los Roles en el Backend?
Spring Security intercepta cada petición HTTP entrante a través de un filtro personalizado (`JwtAuthenticationFilter`).

1. **Extracción:** El filtro lee la cabecera `Authorization: Bearer <token>`.
2. **Validación:** Comprueba que la firma coincida con la propiedad `jwt.secret` y que el token no haya expirado.
3. **Inyección:** Extrae los claims del token (como los roles `ROLE_ADMIN`, `ROLE_DOCENTE`) y los inyecta en el contexto de seguridad de Spring (`SecurityContextHolder`).

Esto permite proteger los endpoints directamente en los controladores usando anotaciones de resguardo:
```java
@PreAuthorize("hasRole('ADMIN')")
@PostMapping("/usuarios/crear")
public ResponseEntity<?> crearUsuario(@Valid @RequestBody UsuarioRequest request) {
    // Lógica protegida
}
```

> [!WARNING]
> ### 🚨 Buenas prácticas en el Backend
> - **Exclusión estricta:** Comprueba siempre que `src/main/resources/application.properties` esté listado en tu archivo `.gitignore` para evitar fugas de contraseñas de bases de datos.
> - **Semillas de datos seguras:** Los archivos de semillas (`AlumnoNombresComunesSeeder.java`, `CalificacionSeed.java`) solo deben ejecutarse automáticamente en entornos de desarrollo (`spring.profiles.active=dev`). Evita ejecuciones accidentales que limpien datos en producción.
> - **Validación obligatoria:** Utiliza `@Valid` en los parámetros de tus controladores para asegurar el tipado y restricciones de los DTOs antes de procesar cualquier lógica en los servicios.


---

## 🧑‍💻 Equipo de desarrollo

* **Agostina Torres** –  Análisis Funcional / Frontend 👩‍💻
* **German Monti Rubio** –  Backend / Base de Datos 👨‍💻
* **Rocio Cordoba** – Análisis Funcional / Backend 👩‍💻

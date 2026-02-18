# Prompts para construir la plataforma de portafolio

> Usa estos prompts con GitHub Copilot (o modelos similares) en tu IDE. 
> Adáptalos con tus nombres de paquetes, URLs y proyectos.

---

## 1) Setup del backend (microservicio existente)

**Prompt:**  
“Sobre el microservicio base que ya existe en este proyecto (Spring Boot 3, Java 17 y Maven con `pom.xml`), revisa sus dependencias actuales y configuración común.  
Propón los cambios mínimos necesarios en el `pom.xml` para soportar el endpoint de portafolio (por ejemplo, `spring-boot-starter-web`, `spring-boot-starter-validation`, Lombok y H2 si aún no están) manteniendo el mismo estilo y convenciones del proyecto.”

---

## 2) Modelo y DTOs del perfil

**Prompt:**  
“En este proyecto de Spring Boot, crea clases DTO para un currículum: `ProfileDTO`, `ExperienceDTO` y `SkillDTO`. 
`ProfileDTO` debe tener: `fullName`, `role`, `summary`, `linkedinUrl`, `githubUrl`, `experiences` y `skills`.  
`ExperienceDTO` debe tener: `company`, `position`, `startDate`, `endDate`, `highlights`.  
`SkillDTO` debe tener: `name`, `level`, `years`.  
Usa anotaciones de Lombok (`@Data`, `@Builder`, etc.) y mantén las clases limpias y enfocadas a transferencia de datos.”

---

## 3) Servicio de dominio (mock inicial)

**Prompt:**  
“Crea un servicio de Spring llamado `ResumeService` que retorne un `ProfileDTO` con datos de ejemplo (perfil, experiencias y skills).  
El servicio debe exponer un método público `getProfile()` que construya y devuelva el DTO con información mock.”

---

## 4) Controlador REST con CORS restringido

**Prompt:**  
“Crea un controlador REST en Spring Boot llamado `ResumeController` que exponga el endpoint `GET /api/resume` y devuelva un `ProfileDTO` como JSON.  
Inyecta `ResumeService` y llama al método `getProfile()`.  
Configura CORS usando `@CrossOrigin` para permitir peticiones únicamente desde `https://<mi-dominio-frontend>`.”

---

## 5) Persistencia con H2 (extensión para la tarea)

**Prompt:**  
“Refactoriza el servicio actual `ResumeService`, que hoy usa datos mock, para que use persistencia con H2 y Spring Data JPA.  
Crea entidades JPA para perfil, experiencia y skills, repositorios correspondientes y una capa de mapeo que convierta entidades a `ProfileDTO`, `ExperienceDTO` y `SkillDTO`.  
Asegúrate de que el endpoint `/api/resume` siga funcionando sin romper el contrato JSON.”

---

## 6) Filtro/Interceptor para validar `X-API-KEY`

**Prompt:**  
“En esta aplicación Spring Boot, implementa un filtro o interceptor que valide un header HTTP `X-API-KEY` para todos los endpoints bajo `/api/**`.  
Si el header falta o es inválido, retorna HTTP 401 con un cuerpo JSON de error (por ejemplo: `timestamp`, `status`, `error`, `message`, `path`).  
Haz que el valor esperado de la API key se pueda configurar vía `application.properties`.”

---

## 7) Manejo global de errores (API)

**Prompt:**  
“Agrega un manejador global de errores en Spring Boot usando `@RestControllerAdvice`.  
Maneja al menos: errores de validación, recursos no encontrados y excepciones genéricas.  
Devuelve respuestas JSON consistentes con campos como: `timestamp`, `status`, `error`, `message`, `path`.”

---

## 8) Setup del frontend (React)

**Prompt:**  
“Crea la estructura base de una aplicación React (puede ser con TypeScript) para una página de portafolio.  
Define un componente principal `PortfolioPage` que será el punto de entrada de la vista.  
Incluye un layout simple con encabezado, sección principal y pie de página, preparado para mostrar los datos de un currículum.”

---

## 9) Hook de datos para consumir la API

**Prompt:**  
“Crea un custom hook de React llamado `useResume` que reciba la URL de una API de currículum.  
El hook debe manejar los estados `data`, `isLoading` y `error` usando `useState` y `useEffect`, hacer la petición `fetch` y devolver un objeto `{ data, isLoading, error }`.”

---

## 10) Componente con estados de loading, éxito y error

**Prompt:**  
“Implementa el componente `PortfolioPage` para consumir la API `https://<mi-api>.azurewebsites.net/api/resume` usando el hook `useResume`.  
Muestra:
- Un indicador de carga mientras `isLoading` es verdadero.
- Un mensaje de error visible si `error` no es nulo.
- El contenido del currículum (nombre, rol, skills, experiencia) cuando `data` existe.”

---

## 11) Skeleton Screen para mejorar UX

**Prompt:**  
“En lugar de un simple spinner, crea un componente `ResumeSkeleton` que muestre un skeleton screen del currículum (bloques grises para el nombre, resumen, tarjetas de experiencia y lista de skills).  
Integra `ResumeSkeleton` en `PortfolioPage` para usarlo mientras `isLoading` es verdadero.”

---

## 12) Manejo de errores con reintento

**Prompt:**  
“Mejora el manejo de errores en `PortfolioPage` agregando una tarjeta de error con un botón de `Reintentar`.  
Cuando el usuario haga clic en `Reintentar`, vuelve a ejecutar la llamada a la API sin recargar toda la página.  
Implementa la lógica de reintento reutilizando el hook `useResume` o creando una pequeña función de recarga.”

---

## 13) Scripts de build y deploy del frontend

**Prompt:**  
“Configura los scripts de `package.json` para poder construir y desplegar la app de React en GitHub Pages.  
Agrega los scripts `build` y `deploy`, configura el campo `homepage` con la URL de GitHub Pages y explica brevemente en el README cómo usar `npm run build` y `npm run deploy`.”

---

## 14) Documentación de despliegue en Azure (backend)

**Prompt:**  
“Escribe una sección corta de documentación en Markdown explicando cómo desplegar esta API de Spring Boot en Azure App Service usando Azure CLI.  
Incluye comandos de ejemplo para `az login`, `az group create` (si aplica) y `az webapp up --name <app-name> --runtime "JAVA:17-java17"`.  
Explica también cómo configurar variables de entorno como la API key en Azure.”

---

## 15) Tests unitarios del `ResumeController`

**Prompt:**  
“Genera pruebas unitarias para `ResumeController` usando Spring Boot Test y MockMvc.  
Cubre al menos: 
- El caso exitoso donde el endpoint `/api/resume` retorna HTTP 200 y un JSON con el perfil.  
- El caso donde falta el header `X-API-KEY` o es incorrecto y se devuelve HTTP 401 con un cuerpo JSON de error.  
Asegúrate de comprobar el status y algunos campos clave del JSON.”

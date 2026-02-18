# US-01 — Portafolio de Ingeniería de Alto Impacto

**ID:** US-01  
**Título:** Visualización de Perfil Profesional Automatizado en la Nube

---

## 📄 Descripción de la Historia de Usuario

**COMO** estudiante de Ingeniería de Software,  
**QUIERO** disponer de una arquitectura Full-Stack (Frontend + API) desplegada en la nube que exponga mi perfil técnico,  
**PARA** generar oportunidades laborales demostrando mis habilidades reales de desarrollo y arquitectura desde el "segundo cero" de contacto con un reclutador.

---

## ✅ Criterios de Aceptación (Definition of Done)

Para considerar esta historia como **Done**, se deben cumplir todos los siguientes criterios técnicos:

1. **Desacoplamiento (Backend)**  
   - La información del perfil debe ser servida por una **API REST** construida en **Spring Boot 3**.
   - La respuesta expone un **objeto JSON estructurado** (por ejemplo: datos personales, skills, experiencia).

2. **Interactividad (Frontend)**  
   - La interfaz en **React** consume la API de forma **asíncrona**.
   - Se manejan estados de **loading** (carga en progreso) y **error** (fallo en la petición) con feedback visual claro.

3. **Seguridad de Acceso (CORS)**  
   - El backend está configurado para permitir peticiones **únicamente** desde el dominio donde se aloja el frontend (por ejemplo, **GitHub Pages**).

4. **Disponibilidad Cloud**  
   - El sistema completo (API + Frontend) es accesible mediante una **URL pública** desplegada en **Azure App Service** (u otro servicio equivalente definido en la clase).

5. **Clean Code y Diseño (DTO)**  
   - El backend utiliza el patrón **DTO (Data Transfer Object)** para separar la lógica de negocio de la representación de la respuesta.
   - No se exponen directamente entidades internas del dominio en la API pública.

---

## 🔍 Definition of Ready (Lo necesario para empezar)

Para poder iniciar el desarrollo de esta historia (por ejemplo, en los 10 minutos de demo en vivo), se requiere que:

1. **Backend listo para extenderse**  
   - Proyecto base de **Spring Boot** generado (Maven o Gradle) y corriendo localmente.

2. **Infraestructura Cloud prelista**  
   - **Azure App Service** pre-configurado o listo para usar con `az webapp up`.

3. **Asistencia de IA habilitada**  
   - **GitHub Copilot** activo en el IDE para apoyar con scaffolding de controladores, DTOs y componentes de UI.

4. **Repositorio versionado**  
   - Repositorio en **GitHub** creado y conectado al entorno de desarrollo, para que los cambios puedan versionarse y compartirse.

---

## 🧩 Alcance y No Alcance (Scope)

- **Incluye:**
  - Un endpoint público de lectura del perfil profesional (por ejemplo, `GET /api/resume`).
  - Una vista principal en React que consuma y muestre la información del perfil.
  - Manejo básico de errores de red (timeout, error 500, etc.).

- **No incluye (en esta US):**
  - Panel de administración para editar el perfil.
  - Autenticación compleja (OAuth2, JWT, etc.).
  - Persistencia avanzada (microservicios, colas de mensajes, etc.).

---

## 📝 Notas de Implementación (Guía rápida)

- Sugerencia de estructura de DTO (ejemplo):
  - `ProfileDTO` (nombre, rol, resumen, links).
  - `ExperienceDTO` (empresa, rol, periodo, logros clave).
  - `SkillDTO` (tecnología, nivel, años de experiencia).

- El frontend puede iniciar con un único componente principal (por ejemplo, `PortfolioPage`) que:
  - Llama a la API en `useEffect`.
  - Usa estados `isLoading`, `error` y `data`.
  - Muestra un skeleton o spinner mientras carga y un mensaje amigable si falla.

---

## 🎯 Resultado esperado para el jurado

Al abrir la URL pública compartida por el estudiante, el jurado debe poder:

- Ver un **perfil técnico completo** cargado dinámicamente desde la API.
- Percibir una **UI responsiva** que reacciona a estados de carga y error.
- Validar que el sistema está **desplegado en la nube**, no solo en local.
- Revisar el código fuente en GitHub y encontrar una estructura **limpia y desacoplada** basada en DTOs.

# Diapositivas — Clase Modelo Full‑Stack Cloud‑Native

> Sugerencia: cada sección corresponde a 1 diapositiva. 
> Usa máximo 3–5 bullets por slide.

---

## Slide 1 — Portada
- **Título:** Ecosistema Full‑Stack Cloud‑Native en 30 minutos
- **Subtítulo:** De idea a URL pública en Azure
- **Profesor:** Beto (Ninko) — Senior Software Engineer
- **Universidad:** UTEC — Ingeniería de Software
- **Call to action:** Deja tu LinkedIn listo, hoy lo vas a potenciar.

---

## Slide 2 — El Gancho: Empleabilidad
- El 80% de los perfiles son filtrados por **algoritmos**.
- No compites solo con personas, compites con **sistemas de ranking**.
- Tu **activo digital** vale más que tu CV en PDF.
- Pregunta disparadora: ¿Qué ve un reclutador tuyo en los primeros 10 segundos?

---

## Slide 3 — Objetivo de la Sesión
- Pasar **de una idea** a una **URL pública** en 30 minutos.
- Construir un **portafolio técnico vivo** (no una demo estática).
- Integrar: **Spring Boot (API)** + **React (Frontend)** + **Azure (Cloud)**.
- Usar **GitHub Copilot** como copiloto, no como piloto.

---

## Slide 4 — Agenda (30 minutos)
- Warm‑up — Empleabilidad y contexto (4 min)
- Design — Arquitectura + User Story (4 min)
- Develop — Live coding (10 min)
- Ship — Despliegue en Azure (4 min)
- Check — Q&A + verificación (3 min)
- Close — Reto técnico / tarea (5 min)

---

## Slide 5 — User Story US‑01
- **ID:** US‑01 — Portafolio de Ingeniería de Alto Impacto
- COMO: estudiante de Ingeniería de Software.
- QUIERO: arquitectura Full‑Stack en la nube que exponga mi perfil.
- PARA: demostrar mis habilidades reales desde el segundo cero.
- Ver detalle completo en: US‑01 (documento de historia de usuario).

---

## Slide 6 — Criterios de Aceptación (US‑01)
- API REST en **Spring Boot 3** devolviendo **JSON** estructurado.
- Frontend en **React** consumiendo la API con **loading** y **error**.
- **CORS** configurado solo para el dominio del frontend.
- Sistema accesible vía **URL pública en Azure**.
- Uso de **DTOs** para separar dominio y respuesta.

---

## Slide 7 — Arquitectura de Referencia
- Frontend: **React SPA** (GitHub Pages / Static Web App).
- Backend: **Spring Boot API** (Azure App Service).
- Comunicación vía **HTTP/JSON** sobre HTTPS.
- CORS restringido al dominio del frontend.
- Código versionado en **GitHub** (CI/CD opcional).

*(Inserta aquí un diagrama simple: Browser → Frontend → API → Cloud)*

---

## Slide 8 — Definition of Ready (DoR)
- Proyecto base de **Spring Boot** generado y corriendo.
- **Azure App Service** creado o listo para `az webapp up`.
- Proyecto de **React** inicializado (`create-react-app`, Vite, etc.).
- **GitHub Copilot** activo en el IDE.
- Repositorio en **GitHub** listo para push.

---

## Slide 9 — Live Coding: Backend (Plan)
- Crear endpoint `GET /api/resume`.
- Definir DTOs: `Profile`, `Experience`, `Skill`.
- Devolver JSON mock de perfil profesional.
- Configurar `@CrossOrigin` para el dominio del frontend.
- Comprobar respuesta con Postman/Insomnia o el navegador.

---

## Slide 10 — Prompt Ejemplo Backend (Copilot)
- *Prompt sugerido:*  
  "Create a Spring Boot REST Controller for a Resume. Include DTOs for Experience and Skills. Add @CrossOrigin for my GitHub Pages URL. Use Lombok."
- Ajustar nombres de paquetes y DTOs al estándar de la clase.
- Revisar el código generado antes de ejecutarlo.

---

## Slide 11 — Live Coding: Frontend (Plan)
- Crear componente principal: `PortfolioPage`.
- Hacer `fetch` a `/api/resume` (URL de Azure).
- Manejar `isLoading`, `error`, `data`.
- Renderizar nombre, rol, skills y experiencia.
- Preparar diseño simple pero profesional (dark/light theme).

---

## Slide 12 — Prompt Ejemplo Frontend (Copilot)
- *Prompt sugerido:*  
  "Create a React component to fetch resume data from Azure. Use Tailwind CSS for a professional dark-themed UI. Include a LoadingSpinner and ErrorBoundary."
- Ajustar la URL de la API.
- Comprobar que el estado de error se vea claramente.

---

## Slide 13 — Despliegue en Azure (Backend)
- Concepto: de local a **URL pública**.
- Pasos tipo:
  - `az login`
  - `az webapp up --name <app-name> --runtime "JAVA:17-java17"`
- Verificar la URL generada: `https://<app-name>.azurewebsites.net`.
- Probar la ruta `/api/resume` en vivo.

---

## Slide 14 — Despliegue Frontend (GitHub Pages)
- Crear repo en GitHub y hacer push.
- Ejecutar en local:
  - `npm install`
  - `npm run build`
  - `npm run deploy` (según script configurado).
- Ajustar CORS en el backend con el dominio de GitHub Pages.

---

## Slide 15 — Checkpoint: ¿Qué Hemos Logrado?
- Tenemos una **API pública** con tu perfil técnico.
- Tenemos un **frontend** que consume esa API.
- Todo corre en la **nube** con URL compartible.
- Hemos usado **Copilot** como acelerador, no como sustituto.

---

## Slide 16 — Reto Técnico (Tarea)
- Migrar mock de datos a **H2** con repositorio JPA.
- Añadir validación de `X-API-KEY` (filtro/interceptor).
- Implementar `Skeleton Screen` en el frontend.
- Agregar tests unitarios para el controller.

---

## Slide 17 — Criterios de Evaluación de la Tarea
- API responde con JSON válido y consistente.
- `X-API-KEY` es requerido y validado.
- UI maneja **loading**, **error** y estado exitoso.
- Repositorio con README claro (cómo correr y desplegar).

---

## Slide 18 — Siguientes Pasos y Recursos
- Refinar tu portafolio con más endpoints (proyectos, logros, blog).
- Integrar pruebas automatizadas en CI.
- Recursos:
  - Spring Boot docs, React docs, Azure App Service docs.
- Preguntas / Q&A.

---

## Slide 19 — Cierre
- Tu **primer filtro** ya no es un CV, es tu **sistema en producción**.
- Lo que hiciste hoy puede crecer a un portafolio profesional completo.
- Invita a los reclutadores a probar tu URL.
- Gracias por tu tiempo — ¡a construir!

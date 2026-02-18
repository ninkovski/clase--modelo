Markdown
# Clase Modelo — Full‑Stack Cloud‑Native (30 min)

**Profesor:** Beto (Ninko) — Senior Software Engineer

Breve guía de la sesión: transformar una idea en un servicio público en Azure y una UI consumidora en 30 minutos.

---

## Resumen
- **Objetivo:** Desde User Story hasta una URL pública (API + UI). 
- **Duración total:** **30 minutos**.
- **Audiencia:** Estudiantes con conocimientos básicos de Java/Spring y React.

---

## Agenda (cronograma)

| Fase | Actividad | Tiempo (min) | Objetivo |
|---|---|---:|---|
| Warm‑up | Reflexión sobre empleabilidad y estadísticas de reclutamiento | 4 | Conectar la sesión con caso real |
| Design | Dibujo de arquitectura y maduración de la User Story | 4 | Alinear alcance y criterios de aceptación |
| Develop | Live coding asistido por Copilot (Spring + React) | 10 | Implementar API mínima y consumo desde UI |
| Ship | Publicación en Azure y demostración del link real | 4 | Desplegar backend y verificar URL pública |
| Check | Verificación de aprendizaje y Q&A | 3 | Resolver dudas y validar criterios |
| Close | Síntesis y planteamiento del reto técnico (Tarea) | 5 | Dejar tarea clara y objetivos de evaluación |
| **Total** |  | **30** |  |

---

## Resultados de aprendizaje
- Entender la trazabilidad desde User Story hasta despliegue.
- Implementar una API REST mínima con Spring Boot.
- Consumir la API desde una SPA React y desplegar ambos en la nube.

---

## Requisitos previos y recursos
- Laptop con Java 17, Node.js y Git instalados.
- Cuenta en GitHub y Azure (o permiso para desplegar).
- Repositorio base con plantilla Spring Boot + React (opcional).

Recursos útiles:
- Spring Boot: https://spring.io/projects/spring-boot
- React: https://reactjs.org/
- Azure App Service: https://learn.microsoft.com/azure/app-service/

---

## Detalle por fase

- **Warm‑up (4 min):** Preguntas guiadas sobre empleabilidad y por qué un CV público es un activo digital.
- **Design (4 min):** Dibujo rápido de arquitectura (frontend ←→ backend ←→ despliegue). Definir la User Story:
  - COMO reclutador
  - QUIERO una API con el perfil del candidato
  - PARA validar habilidades en entorno real.
  - Criterios de aceptación: respuesta válida, manejo de errores, despliegue funcional.
- **Develop (10 min):** Live coding
  - Backend: REST endpoint `/api/resume` con DTOs `Experience`, `Skill`.
  - Frontend: Componente que consume `/api/resume`, muestra lista de skills y experiencia.
  - Usar Copilot para acelerar scaffolding y tests.
- **Ship (4 min):** Despliegue rápido
  - Backend: `az webapp up --name <app-name> --runtime "JAVA:17-java17"`  (ejemplo de comando, opcional)
  - Frontend: construir y publicar en GitHub Pages o Azure Static Web Apps.
- **Check (3 min):** Probar la URL pública y validar criterios de aceptación.
- **Close (5 min):** Resumen y planteamiento de la tarea.

---

## Comandos rápidos (ejemplos)

Backend (ejemplo):
```bash
# Inicia sesión en Azure
az login

# Despliega la app Java (ejemplo básico)
az webapp up --name my-cv-api --runtime "JAVA:17-java17"
```

Frontend (ejemplo GitHub Pages):
```bash
npm install
npm run build
# deploy script depende de la plantilla; por ejemplo: npm run deploy
```

Reemplaza `<app-name>` por el nombre deseado; la URL resultante tendrá el formato: https://<app-name>.azurewebsites.net

---

## Reto técnico (Tarea)
Objetivo: Consolidar lo aprendido completando y mejorando el repositorio usado en clase.

- **Refactorización:** Cambiar el mock del Controller por H2 (persistencia en memoria) y repositorio JPA.
- **Seguridad:** Implementar un filtro/interceptor que valide un header `X-API-KEY` para el endpoint.
- **Frontend:** Añadir un `Skeleton Screen` y pruebas básicas de interacción (E2E o unitarias).

Criterios de evaluación:
- API responde con JSON válido y campos esperados.
- Validación del `X-API-KEY` en el backend (prueba incluida).
- UI muestra datos correctos y tiene manejo de error/loading.

---

## Evaluación rápida
- Entrega: PR en GitHub con branch `tarea/<apellidos>`.
- Tests: incluir test unitario para el controller (o mock del servicio) que valide respuesta no nula.
- Documentación: actualizar `README.md` con pasos para ejecutar y desplegar.

---

## Contacto y notas finales
- Para recursos y plantillas, solicita el repositorio base al profesor.
- Si necesitas ayuda con el despliegue en Azure, trae la pantalla y lo resolvemos en clase.

---

© 2026 — Clase Modelo UTEC
'@ | Set-Content -Path 
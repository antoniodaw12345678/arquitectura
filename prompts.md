# Registro de prompts — Práctica 2 (UT2)

Sesión hecha con OpenCode en modo Plan y configuración de solo lectura (`opencode.json`). El agente no modificó ningún fichero de la aplicación.

| Nº | Prompt (resumido) | Qué hizo el agente | Qué corregí yo |
|---|---|---|---|
| 1 | «Hazme un resumen de la aplicación» | Resumen de los 5 servicios, flujos, red, volúmenes y secretos, con referencias `fichero:línea` | Comprobé el listado de ficheros (11) y que no hay README ni tests, como indicó |
| 2 | «Lista los servicios y rellena la tabla: imagen, puerto exterior, puerto interno, volúmenes, dependencias, qué hace» | Tabla completa con evidencia por servicio | Verifiqué celda a celda en `docker-compose.yml` (p. ej. solo el proxy tiene `ports`) |
| 3 | «¿Cuántos servicios son accesibles desde fuera del equipo y por qué?» | 1 de 5 (solo el proxy, 8080); explicó publicar ≠ escuchar | Verificado con `grep -n "ports" docker-compose.yml` → solo líneas 4-5 |
| 4 | «Clasifica los recursos (estático, código, datos, dependencias, configuración, secretos, registros); comprueba si hay `.gitignore` y propón uno» | Clasificación completa + propuesta de `.gitignore` | Comprobé que no había `.gitignore` (`ls -la`, `unzip -l`); se añadió al repositorio |
| 5 | «Dos diagramas Mermaid: `GET /api/libros` (con caché) y `POST /api/pedidos` (cola + worker)» | Diagramas + tabla de verificación línea a línea; rutas internas correctas (`/libros` sin `/api`) | Revisé las líneas citadas (`server.js:15-18` y `:29`; `worker.js:9-10`) |
| 6 | «¿Qué modelo de arquitectura sigue la aplicación y por qué?» | Servicios distribuidos estilo microservicios mínimo; señaló generalidades de manual que no se sostienen | Contrasté con la teoría de la unidad y con los ficheros (una sola BD, sin REST entre servicios) |
| 7 | «Redacta la ficha de implantación para producción» | Ficha completa (10 apartados) distinguiendo «ya lo trae» (✅) de «añadir» (➕) | Verifiqué fechas de soporte con fuentes oficiales (Node 20: fin 30-04-2026; PostgreSQL 16: hasta 09-11-2028) |
| 8 | «Caza de afirmaciones falsas» | Afirmaciones falsas típicas, desmentidas con `fichero:línea` | Verifiqué cada desmentido directamente en el código |
| 9 | «Hazme un commit y súbelo a github.com/antoniodaw12345678/arquitectura» | `git init`, `.gitignore`, commit `061fc8a` y push a `main` | El primer push dio error 403: al token le faltaba el permiso *Contents: Read and write*; corregido |

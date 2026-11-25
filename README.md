# Planillas de Seguridad Social (PILA)

Autor: **Gabriel Romero, Ingeniero Civil**.

Aplicativo web para leer planillas PILA (seguridad social) en PDF y exportarlas
a Excel. Es un sitio **estático** (un solo
`index.html`, sin servidor ni build), desplegado en **Cloudflare**.

## Cómo correrlo localmente
Abre `index.html` con doble clic en el navegador (Chrome, Edge o Safari). No
requiere instalar nada.

## Despliegue automático
El repositorio está conectado directamente a Cloudflare (Workers Builds,
proyecto **planillascorban**). Cada `push` a la rama `main` publica el sitio
automáticamente; no hay que configurar nada en GitHub.

- El resultado de cada publicación aparece en GitHub como el check
  **"Workers Builds: planillascorban"** del commit.
- El detalle y el historial están en https://dash.cloudflare.com →
  **Workers & Pages → planillascorban**.
- Los archivos que no deben publicarse se listan en `.assetsignore`.

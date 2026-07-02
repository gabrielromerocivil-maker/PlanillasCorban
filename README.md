# Planillas Corban

Aplicativo web interno de Grupo Corban SAS para leer planillas PILA (seguridad
social) en PDF y exportarlas a Excel. Es un sitio **estático** (un solo
`index.html`, sin servidor ni build), desplegado en **Cloudflare Pages**.

## Cómo correrlo localmente
Abre `index.html` con doble clic en el navegador (Chrome, Edge o Safari). No
requiere instalar nada.

## Despliegue automático (GitHub Actions → Cloudflare Pages)
Cada vez que se hace `push` a la rama `main`, el flujo de
[`.github/workflows/deploy.yml`](.github/workflows/deploy.yml) publica el sitio
en Cloudflare Pages automáticamente.

### Configuración inicial (una sola vez)
Para que el despliegue funcione hay que hacer **3 cosas**:

**1. Crear un API Token en Cloudflare**
- Entra a https://dash.cloudflare.com/profile/api-tokens → **Create Token**.
- Usa la opción **"Create Custom Token"** con este permiso:
  - `Account` → `Cloudflare Pages` → `Edit`.
- Crea el token y **copia el valor** (solo se muestra una vez).

**2. Obtener el Account ID**
- En https://dash.cloudflare.com → **Workers & Pages**.
- A la derecha aparece **Account ID**; cópialo.

**3. Guardar ambos como secretos en GitHub**
- En el repositorio: **Settings → Secrets and variables → Actions →
  New repository secret**. Crea estos dos:
  - `CLOUDFLARE_API_TOKEN` → el token del paso 1.
  - `CLOUDFLARE_ACCOUNT_ID` → el ID del paso 2.

### Nombre del proyecto
En `.github/workflows/deploy.yml`, en la línea `--project-name=planillascorban`,
usa el nombre **exacto** de tu proyecto en Cloudflare Pages. Si el proyecto aún
no existe con ese nombre, se crea en el primer despliegue.

### Probar el despliegue
Tras configurar los secretos, entra a la pestaña **Actions** del repositorio y
ejecuta el flujo **"Desplegar a Cloudflare Pages"** (botón *Run workflow*), o
simplemente haz un nuevo `push` a `main`.

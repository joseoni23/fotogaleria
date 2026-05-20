# 📸 Galería Fotográfica — Netlify + Decap CMS

Sitio estático de portafolio para fotógrafo con panel de administración.
El fotógrafo sube fotos desde `/admin` sin tocar código.

---

## Estructura de archivos

```
/
├── index.html          ← Galería pública
├── netlify.toml        ← Config de Netlify
├── admin/
│   ├── index.html      ← Panel Decap CMS
│   └── config.yml      ← Config del CMS
├── content/
│   └── photos.json     ← Base de datos de fotos (manejada por CMS)
└── images/             ← Fotos subidas (manejadas por CMS)
```

---

## 🚀 Deployment — paso a paso

### 1. Subir a GitHub

```bash
git init
git add .
git commit -m "init: galería fotográfica"
git remote add origin https://github.com/TU_USUARIO/TU_REPO.git
git push -u origin main
```

### 2. Conectar con Netlify

1. Entra a [app.netlify.com](https://app.netlify.com)
2. **Add new site → Import an existing project**
3. Conecta tu repositorio de GitHub
4. En Build settings:
   - Build command: *(dejar vacío)*
   - Publish directory: `.`
5. Clic en **Deploy site**

### 3. Habilitar Netlify Identity

1. En tu sitio en Netlify → **Site configuration → Identity**
2. Clic en **Enable Identity**
3. En **Registration preferences** → selecciona **Invite only**
4. En **Services → Git Gateway** → clic en **Enable Git Gateway**

### 4. Invitar al fotógrafo como usuario admin

1. Netlify → Identity → **Invite users**
2. Ingresa el email del fotógrafo
3. El fotógrafo recibirá un email para crear su contraseña

### 5. Acceder al panel de administración

- URL: `https://tu-sitio.netlify.app/admin/`
- El fotógrafo inicia sesión con su email y contraseña
- Puede subir fotos, editarlas, cambiar categorías
- Los cambios se publican en ~30 segundos

---

## 🖼️ Cómo subir fotos (para el fotógrafo)

1. Ir a `tusitio.com/admin/`
2. Iniciar sesión
3. Clic en **Galería de Fotos → Fotos**
4. Clic en el botón **+** para agregar foto
5. Llenar: título, categoría, subir imagen
6. Clic en **Publish**
7. En ~30 segundos aparece en el sitio público ✅

---

## ✏️ Personalización

### Cambiar nombre del fotógrafo
Abre `index.html` y busca **"CARLOS VEGA"** — reemplaza con el nombre real.
También cambia el email de contacto.

### Cambiar categorías
Abre `admin/config.yml` y edita la sección `options` bajo `category`.
Las mismas opciones deben existir en los botones de filtro en `index.html`.

### Cambiar colores
En `index.html`, al inicio del `<style>`:
```css
:root {
  --accent: #c9a96e;  /* ← color dorado, cambia aquí */
}
```

---

## 🔑 Notas importantes

- Las imágenes se guardan en el repositorio de GitHub (`/images/`).
- Para fotos muy pesadas (>5MB), considera usar Cloudinary como media library.
- El sitio funciona sin build step — es HTML puro + JSON.
- Netlify redespliega automáticamente al guardar cambios en el CMS.

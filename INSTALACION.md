# 🚀 Instalación — Inventario Escolar Pro v2

## Paso 1: Actualizar en GitHub (si ya tienes la app)

Si ya tienes la app funcionando:

1. **Ve a tu repositorio** (ej: `LeapInventory`) en GitHub
2. **Sube los 3 archivos nuevos, sobrescribiendo:**
   - `index.html` (la app completa)
   - `sw.js` (Service Worker)
   - `manifest.json` (configuración PWA)

3. **Espera 2-3 minutos**
4. **Recarga la app en tu iPhone** (o cierra y reabre Safari)

Los datos antiguos se conservan automáticamente. La app debería verse más moderna con la nueva interfaz.

---

## Paso 2: Instalación limpia (si es la primera vez)

Si **no tienes la app aún**, sigue estos pasos:

### En GitHub (una sola vez)

1. **Crea un repositorio nuevo:**
   - Ve a [github.com/new](https://github.com/new)
   - Nombre: `inventario-escolar` (o tu nombre preferido)
   - Descripción: "Aplicación de inventario escolar con escaneo"
   - Público ✓
   - Create repository

2. **Sube los archivos:**
   - Click en "Add file" → "Upload files"
   - Arrastra estos 4 elementos:
     - `index.html`
     - `manifest.json`
     - `sw.js`
     - Carpeta `icons/` (con las 3 imágenes dentro)
   - "Commit changes"

3. **Activa GitHub Pages:**
   - Ve a **Settings** (pestaña del repo)
   - Lateral izquierdo: **Pages**
   - "Build and deployment":
     - Source: "Deploy from a branch"
     - Branch: `main` / `/ (root)`
     - Save
   - Espera 1-2 minutos

4. **Tu app estará en:**
   ```
   https://tu-usuario.github.io/inventario-escolar/
   ```

### En tu iPhone

1. **Abre el enlace en Safari:**
   ```
   https://tu-usuario.github.io/inventario-escolar/
   ```
   (tiene que ser Safari, no Chrome)

2. **Instala como app:**
   - Toca el botón de compartir (↗️ cuadrado con flecha)
   - "Añadir a pantalla de inicio"
   - Confirma
   - Aparecerá un ícono en la pantalla principal

3. **Primera vez que escanees:**
   - iOS te pedirá permiso para usar la cámara
   - Acepta

---

## Paso 3: Qué hacer con los iconos

La carpeta `icons/` debe contener 3 imágenes:
- `icon-192.png` (192x192 píxeles)
- `icon-512.png` (512x512 píxeles)
- `apple-touch-icon.png` (180x180 píxeles)

**Opción A:** Usa los que tenías antes (son compatibles)
**Opción B:** Crea unos nuevos:
- Fondo: azul `#1e40af`
- Símbolo: `📦` (emoji) o un ícono personalizado
- Dale a cada uno el tamaño que dice su nombre

---

## Actualizar la app después

Si necesitas cambios en el futuro:

1. **Edita el archivo localmente** (en tu compu)
2. **Sube a GitHub:**
   - Ve al repo
   - Click en `index.html` (u otro archivo)
   - Click en el lápiz (✎ Edit this file)
   - Cambia lo que necesites
   - "Commit changes"
3. **Recarga en el iPhone:**
   - Cierra Safari completamente
   - Reabre la app
   - En 30 segundos, el Service Worker actualiza

---

## URLs útiles

- **Tu app:** `https://tu-usuario.github.io/inventario-escolar/`
- **GitHub repo:** `https://github.com/tu-usuario/inventario-escolar`
- **GitHub Pages settings:** `https://github.com/tu-usuario/inventario-escolar/settings/pages`

---

## Troubleshooting

### "No puedo instalarla como app"
- Asegúrate de estar en Safari, no Chrome
- iOS 13+
- Toca el botón de compartir (↗️)

### "El escaneo no funciona"
- Mejora la luz (factor #1)
- Abre en HTTPS (GitHub Pages = automático)
- Acepta los permisos de cámara

### "Quiero cambiar el repositorio de nombre"
- GitHub → Settings → Rename
- Tu app seguirá funcionando (redirige automáticamente)

### "Los datos se borraron"
- Revisa en Safari → Settings → Privacy → Website Data
  - Asegúrate de que el dominio de tu app no está en "Remove All"
- Los datos están en IndexedDB del navegador

---

## Soporte

Si algo no funciona:
1. Cierra Safari completamente
2. Reabre desde el ícono de la pantalla principal
3. Intenta nuevamente

Si persiste, puedes:
- Limpiar caché: Safari → Settings → Privacy → Remove All Website Data
- Reinstalar: elimina el ícono, vuelve a añadir a pantalla

**Los datos NO se pierden** — están guardados en IndexedDB, no en Safari cache.

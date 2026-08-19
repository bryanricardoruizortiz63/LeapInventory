# Inventario Escolar

App web (PWA) para escanear códigos de barras/QR y llevar el inventario de la escuela desde el iPhone. Funciona sin conexión una vez instalada, guarda todo en el propio dispositivo (no hay límite de artículos) y permite exportar todo a Excel en cualquier momento.

## Qué incluye esta carpeta

- `index.html` — la app completa (interfaz, escáner, formularios, exportación).
- `manifest.json` — hace que Safari pueda "instalarla" como app en la pantalla de inicio.
- `sw.js` — Service Worker: cachea la app para que funcione sin internet después de la primera carga.
- `icons/` — ícono de la app (192px, 512px y versión para iOS).

## Paso 1 — Publicar en GitHub Pages (una sola vez)

El escaneo con cámara solo funciona si la app se abre desde una dirección **https**, así que hay que subirla a un hosting gratuito. GitHub Pages es la opción más sencilla si ya tienes cuenta de GitHub.

1. Entra a [github.com](https://github.com) y crea un repositorio nuevo. Por ejemplo, llámalo `inventario-escolar`. Puede ser público o privado (GitHub Pages funciona con ambos en cuentas normales; si es una cuenta gratuita y lo quieres privado, revisa que tu plan permita Pages en repos privados — si no, créalo público, no hay datos sensibles en estos archivos, ya que el inventario se guarda solo en tu iPhone, no en GitHub).
2. Dentro del repositorio, usa el botón **"Add file" → "Upload files"** y arrastra los 4 elementos de esta carpeta: `index.html`, `manifest.json`, `sw.js` y la carpeta `icons` completa (con sus 3 imágenes dentro). Confirma el "commit" (guardar cambios).
3. Ve a **Settings → Pages** (en el menú lateral del repositorio).
4. En "Build and deployment", selecciona **Source: Deploy from a branch**, rama **main** y carpeta **/ (root)**. Guarda.
5. Espera 1-2 minutos. GitHub te mostrará un enlace parecido a:
   `https://tu-usuario.github.io/inventario-escolar/`

Ese es el enlace de tu app. Ábrelo primero en el navegador para confirmar que carga bien.

## Paso 2 — Instalar en el iPhone

1. Abre ese enlace en **Safari** (tiene que ser Safari, no Chrome, para poder instalarla).
2. Toca el botón de compartir (el cuadrado con la flecha hacia arriba).
3. Elige **"Añadir a pantalla de inicio"**.
4. Confírmalo. Aparecerá un ícono de la app en tu pantalla de inicio, y se abrirá a pantalla completa como una app normal.
5. La primera vez que uses "Escanear código", iOS te pedirá permiso para usar la cámara — acepta.

## Cómo se usa

- **Escanear código**: abre la cámara y detecta automáticamente códigos de barras (EAN, UPC, Code128, etc.) y códigos QR. Si el código ya existe en el inventario, te deja elegir entre editar ese artículo, sumarle 1 a la cantidad, o crear un registro nuevo de todas formas. Si es un código nuevo, abre el formulario para completarlo.
- **Añadir manual**: agrega un artículo sin necesidad de escanear nada.
- **Tocar un artículo** en la lista lo abre para editar cualquier campo o eliminarlo.
- **Buscar**: filtra por nombre, código, categoría, salón, etc. Los "chips" debajo del buscador filtran por categoría.
- **⚙️ Gestionar campos** (arriba a la derecha): agrega campos nuevos (texto, número, fecha o lista de opciones) o quita los que no necesites. "Nombre" y "Código" son fijos porque identifican cada artículo escaneado; todo lo demás (Categoría, Cantidad, Ubicación, Estado, Responsable, Notas, Fecha, y cualquier campo que agregues) se puede quitar o reordenar.
- **⬇︎ Exportar** (arriba a la derecha): genera un archivo `.xlsx` con todo el inventario actual y lo descarga al iPhone (desde ahí puedes guardarlo en Archivos, enviarlo por correo, subirlo a Drive, etc.).

## Sobre el guardado de datos

Todo el inventario se guarda **en el propio iPhone** (en el almacenamiento del navegador, técnicamente "IndexedDB"), no en un servidor. Por eso:

- Los datos siguen ahí aunque cierres la app o reinicies el teléfono.
- Solo se ven desde ese iPhone/navegador específico — no se sincronizan automáticamente entre varios dispositivos ni con una computadora.
- Como buena práctica (igual que recomienda Orca Scan y cualquier app de este tipo), exporta a Excel de vez en cuando como respaldo, sobre todo antes de actualizar iOS o si vas a borrar la app.
- Si necesitas usar el inventario desde varios teléfonos o compartirlo con más personas del equipo en tiempo real, eso ya requeriría una base de datos en la nube (por ejemplo Google Sheets o Airtable como backend); avísame si más adelante quieres que lo conectemos a algo así.

## Actualizar la app más adelante

Si en el futuro quieres que le agregue o cambie algo, dime qué necesitas, te mando los archivos actualizados y solo tienes que volver a subirlos (sobrescribiendo los mismos nombres) en el mismo repositorio de GitHub. El ícono en tu iPhone se actualizará solo la próxima vez que abras la app con internet.

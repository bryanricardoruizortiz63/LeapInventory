# 📦 B Scan Inventory

App web (PWA) de inventario con escaneo de códigos de barras/QR, inspirada en las
funciones clave de [Orca Scan](https://apps.apple.com/us/app/barcode-scanner-orca-scan/id1161117971):
escaneo con cámara o lector Bluetooth, campos personalizados por proyecto, fotos,
ubicación GPS, historial de auditoría por artículo, exportación a Excel/CSV y
sincronización en la nube entre varios dispositivos. Funciona offline y no
requiere servidor propio: todo corre en el navegador y los datos viven en
IndexedDB, con sincronización opcional vía Supabase.

## Instalación

1. Sube `index.html`, `manifest.json`, `sw.js` y la carpeta `icons/` a un repo de
   GitHub y activa **GitHub Pages** (Settings → Pages → Deploy from branch → `main` / `root`).
2. Abre la URL resultante en el teléfono con Safari (iOS) o Chrome (Android).
3. Usa "Compartir → Añadir a pantalla de inicio" (iOS) o el menú "Instalar app"
   (Android/Chrome) para instalarla como app.

## Conceptos

- **Proyecto**: un inventario independiente (ej. "Escuela Norte", "Bodega
  central"). Puedes tener varios a la vez desde **⚙︎ Ajustes → Proyectos**;
  solo se muestran/exportan los artículos del proyecto activo, y su nombre
  se usa como nombre del archivo al exportar a Excel.
- **Artículo**: una hoja de inventario independiente dentro del proyecto
  activo (ej. "Chromebooks", "Herramientas", "Armario"). Cada artículo
  define sus propios campos.
- **Ubicaciones**: la lista de ubicaciones del proyecto activo (ej. "Salón 1"
  a "Salón 32") se administra en un solo lugar, **⚙︎ Ajustes → Ubicaciones**,
  y se comparte automáticamente entre todos sus artículos — no hay que
  configurarla en cada uno por separado. Al escanear, eliges el artículo
  arriba y la ubicación en la barra de debajo.
- **Campos**: texto, número, texto largo, fecha, lista de opciones, foto o
  ubicación GPS. Un campo puede marcarse como:
  - **Escanear**: se llena automáticamente durante el flujo de escaneo rápido
    (cámara o lector Bluetooth).
  - **Obligatorio**: no se puede guardar el artículo escaneado sin llenarlo.
  - **Usar para filtrar/agrupar** (solo campos de lista): sus opciones se
    toman de la lista de Ubicaciones del proyecto. Agrega una barra de
    filtros arriba de la lista. Al exportar a Excel, los artículos que
    comparten este campo se combinan en una hoja por cada ubicación.

## Escaneo

Dentro de un artículo, toca **📱 Escanear nuevo**:
- **📷 Cámara**: usa la cámara del teléfono para leer códigos de barras/QR
  (no requiere hardware adicional).
- **Lector Bluetooth**: el campo de texto del banner recibe el código
  automáticamente si tienes un lector conectado por Bluetooth/USB (modo
  teclado).
- **⌨️ Escribir**: entrada manual si no puedes escanear.

Tras completar los campos marcados como "Escanear", el artículo escaneado se
guarda solo y el escaneo continúa de inmediato; aparece un aviso rápido con
opciones para editar o borrar ese último artículo.

## Fotos, GPS e historial

En el formulario de cada artículo escaneado puedes adjuntar una foto (se
comprime antes de guardarse) y capturar la ubicación GPS actual. Cada
creación/edición queda registrada en el **Historial** (fecha y qué cambió).

## Exportar e importar

Desde **⚙︎ Ajustes → Exportar** (siempre del proyecto activo):
- **Excel**: se llama como el proyecto activo. Si dos o más artículos
  seleccionados comparten el mismo campo de agrupación, sus hojas se
  combinan en una por cada valor de ese campo (ej. una por ubicación, con
  todos los tipos de artículo mezclados ahí); el resto mantiene una hoja
  propia. Incluye una hoja de **RESUMEN**.
- **CSV**: todos los artículos seleccionados en un solo archivo.
- **Respaldo JSON**: copia completa de tus datos (proyectos, artículos y
  fotos) para guardar o transferir a otro dispositivo. Se restaura desde
  **⚙︎ Ajustes → Datos → Restaurar respaldo**.

## Sincronización en la nube

Ver [SYNC.md](./SYNC.md).

## Migración desde versiones anteriores

Si ya usabas la versión escolar (grupos + salones), tus datos se migran
automáticamente la primera vez que abres esta versión: cada "grupo" se
convierte en un "artículo" y "salón" se convierte en un campo de tipo lista
marcado como agrupador. Si venías de una versión sin proyectos, todos tus
artículos existentes se colocan dentro de un proyecto nuevo llamado
"Mi inventario".

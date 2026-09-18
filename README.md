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

- **Proyecto**: una hoja de inventario independiente (ej. "Chromebooks",
  "Herramientas", "Equipos de oficina"). Cada proyecto define sus propios
  campos.
- **Campos**: texto, número, texto largo, fecha, lista de opciones, foto o
  ubicación GPS. Un campo puede marcarse como:
  - **Escanear**: se llena automáticamente durante el flujo de escaneo rápido
    (cámara o lector Bluetooth).
  - **Obligatorio**: no se puede guardar el artículo sin llenarlo.
  - **Usar para filtrar/agrupar** (solo campos de lista): agrega una barra de
    filtros arriba de la lista y divide el Excel exportado en una hoja por
    cada opción (ej. una hoja por ubicación).

## Escaneo

Dentro de un proyecto, toca **📱 Escanear nuevo**:
- **📷 Cámara**: usa la cámara del teléfono para leer códigos de barras/QR
  (no requiere hardware adicional).
- **Lector Bluetooth**: el campo de texto del banner recibe el código
  automáticamente si tienes un lector conectado por Bluetooth/USB (modo
  teclado).
- **⌨️ Escribir**: entrada manual si no puedes escanear.

Tras completar los campos marcados como "Escanear", el artículo se guarda
solo y aparece un aviso con botones para continuar, cambiar de proyecto,
editar o borrar.

## Fotos, GPS e historial

En el formulario de cada artículo puedes adjuntar una foto (se comprime antes
de guardarse) y capturar la ubicación GPS actual. Cada creación/edición queda
registrada en el **Historial** del artículo (fecha y qué cambió).

## Exportar e importar

Desde **⚙︎ Ajustes → Exportar**:
- **Excel**: una hoja por proyecto (o por cada opción del campo de
  agrupación, si tiene uno) más una hoja de **RESUMEN**.
- **CSV**: todos los proyectos seleccionados en un solo archivo.
- **Respaldo JSON**: copia completa de tus datos (proyectos, artículos y
  fotos) para guardar o transferir a otro dispositivo. Se restaura desde
  **⚙︎ Ajustes → Datos → Restaurar respaldo**.

## Sincronización en la nube

Ver [SYNC.md](./SYNC.md).

## Migración desde versiones anteriores

Si ya usabas la versión escolar (grupos + salones), tus datos se migran
automáticamente la primera vez que abres esta versión: cada "grupo" se
convierte en un "proyecto" y "salón" se convierte en un campo de tipo lista
marcado como agrupador.

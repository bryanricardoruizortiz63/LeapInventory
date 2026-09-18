# ☁︎ Sincronización en la nube

B Scan Inventory puede compartir el mismo inventario entre varios dispositivos
usando un backend en Supabase ya creado y conectado a la app (no necesitas
crear ni configurar nada tú mismo).

## Cómo usarla

1. Abre **⚙︎ Ajustes → Sincronización**.
2. Toca **🎲 Generar código nuevo** (o escribe uno propio) y **Guardar**.
3. En cada otro dispositivo, entra el **mismo código** en esa misma pantalla.
4. Todos los dispositivos con ese código verán y editarán el mismo
   inventario. La app sincroniza sola cada ~30 segundos, al reconectarse a
   internet y unos segundos después de cada cambio; también puedes tocar
   **☁︎ Sincronizar ahora** en cualquier momento.

Si nunca configuras un código, la app sigue funcionando 100% local/offline
como antes — la sincronización es opcional.

## Modelo de seguridad (importante)

Este es un modelo de **"código de equipo" tipo enlace compartido**, no de
cuentas de usuario:

- No hay contraseñas ni inicio de sesión. Cualquiera que tenga el código
  puede leer y escribir en ese espacio de trabajo.
- Trata el código como compartirías un enlace de Google Drive: no lo publiques
  en un lugar accesible al público.
- Los códigos generados por la app usan 9 caracteres al azar (sin 0/O/1/I
  para evitar confusiones), suficiente para que no sea adivinable por
  fuerza bruta casual, pero **no** es un sistema de autenticación real.
- Las fotos adjuntas **no** se sincronizan a la nube todavía; solo viven en
  el dispositivo donde se tomaron. Los demás campos (texto, número, fecha,
  listas, GPS, notas e historial) sí se sincronizan.

Si en el futuro necesitas cuentas de usuario reales, permisos por persona o
sincronizar fotos, el siguiente paso sería añadir Supabase Auth y un bucket
de Storage — no está incluido en esta versión para mantener el uso simple
(un código, sin registro).

## Detalles técnicos

- Backend: proyecto Supabase dedicado (`leapinventory`), tablas
  `li_projects` y `li_items`.
- El cliente nunca lee/escribe las tablas directamente: todo pasa por 4
  funciones RPC (`li_get_projects`, `li_get_items`, `li_upsert_project`,
  `li_upsert_item`) que reciben el código de equipo como parámetro. Las
  tablas tienen Row Level Security activado y sin acceso directo
  (`revoke all ... from anon, authenticated`), así que la única forma de
  leer o escribir datos es conociendo un código de equipo válido.
- Resolución de conflictos: "quien edita último gana" comparando la fecha de
  actualización de cada artículo/proyecto. Si dos dispositivos editan el
  mismo artículo sin conexión, se queda el cambio más reciente.
- Los artículos y proyectos borrados se marcan como eliminados (no se borran
  físicamente) para poder avisar a otros dispositivos que también deben
  ocultarlos al sincronizar.

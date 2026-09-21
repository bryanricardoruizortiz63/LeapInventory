# ☁︎ Sincronización en la nube

B Scan Inventory puede compartir el mismo inventario entre varios dispositivos
usando un backend en Supabase ya creado y conectado a la app (no necesitas
crear ni configurar nada tú mismo).

## Cómo usarla

La sincronización es **por proyecto**: cada proyecto (⚙︎ Ajustes →
Proyectos) tiene su propio código de equipo independiente. Sincronizar el
proyecto "Escuela Norte" nunca mezcla sus datos con los del proyecto
"Bodega central", aunque ambos estén sincronizados a la vez en el mismo
dispositivo.

1. Abre **⚙︎ Ajustes → Sincronización**. Arriba hay un selector
   **"Proyecto a sincronizar"** con todos tus proyectos locales (y una
   opción para crear uno nuevo ahí mismo) — elige a cuál va a pertenecer el
   código.
2. Toca **🎲 Generar código nuevo** (o escribe uno propio) y **Guardar**.
3. En cada otro dispositivo, usa ese mismo selector para elegir o crear el
   proyecto que va a recibir los datos, y entra el **mismo código** en esa
   pantalla.
4. Todos los dispositivos con ese código verán y editarán los artículos de
   ese proyecto — absolutamente todos, con todo lo ya escaneado en ellos, no
   solo algunos. La app sincroniza sola cada ~30 segundos, al reconectarse a
   internet y unos segundos después de cada cambio; también puedes tocar
   **☁︎ Sincronizar ahora** en cualquier momento (sincroniza todos los
   proyectos que tengan código configurado en este dispositivo).

Si nunca configuras un código, la app sigue funcionando 100% local/offline
como antes — la sincronización es opcional, y lo es proyecto por proyecto.

## Dispositivos conectados

En **⚙︎ Ajustes → Sincronización** puedes ponerle un nombre a este
dispositivo (ej. "iPhone de Bryan"). Con un código configurado, verás la
lista de todos los dispositivos que han usado ese mismo código, cada uno
con:

- 🟢 **En línea** si sincronizó en el último minuto y medio, o
- **Última vez:** la fecha/hora de su sincronización más reciente.

Esto es solo informativo (para saber quién más está usando el inventario y
si sus cambios ya llegaron); no bloquea ni requiere aprobar dispositivos.

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
  `li_projects` (nivel "artículo" en la app), `li_items` (artículos
  escaneados) y `li_devices` (presencia de dispositivos).
- El cliente nunca lee/escribe las tablas directamente: todo pasa por
  funciones RPC (`li_get_projects`, `li_get_items`, `li_upsert_project`,
  `li_upsert_item`, `li_get_devices`, `li_upsert_device`) que reciben el
  código de equipo como parámetro. Las tablas tienen Row Level Security
  activado y sin acceso directo (`revoke all ... from anon, authenticated`),
  así que la única forma de leer o escribir datos es conociendo un código de
  equipo válido.
- Resolución de conflictos: "quien edita último gana" comparando la fecha de
  actualización de cada artículo. Si dos dispositivos editan el mismo
  artículo escaneado sin conexión, se queda el cambio más reciente.
- Los artículos y artículos escaneados borrados se marcan como eliminados
  (no se borran físicamente) para poder avisar a otros dispositivos que
  también deben ocultarlos al sincronizar.
- El **proyecto** en sí (su nombre, y cuáles artículos le pertenecen) es
  local a cada dispositivo y no tiene tabla propia en la nube. Lo que viaja
  por un código de equipo son los artículos y sus artículos escaneados; cada
  dispositivo decide en qué proyecto local los clasifica al recibirlos.

# Guía: Flujo de Escaneo Continuo

## 🎯 Cómo funciona ahora

### 1. Configurar el Preset (una sola vez)
```
⚙️ Gestionar → Editar "Chromebook"
  ↓
En "Campos":
  - Código de barras (Tipo: Texto, ✓ Escaneo continuo)
  - Número de serie (Tipo: Texto, ✓ Escaneo continuo)
  - Cantidad (Tipo: Número, sin escaneo)
  - Condición (Tipo: Lista, sin escaneo)
  - Ubicación (Tipo: Texto, sin escaneo)
  ↓
Guardar
```

### 2. Escanear un Artículo

```
💻 Selecciona "Chromebook"
  ↓
[📷 Escanear]
  ↓
Se abre cámara
Ves: "📍 1 de 2 - CÓDIGO DE BARRAS"
  ↓
Apunta a código de barras del Chromebook
  → Se detecta automáticamente ✓
  → Vibra
  → Indicador se pone VERDE
  ↓
AUTOMÁTICAMENTE espera el siguiente
Ves: "📍 2 de 2 - NÚMERO DE SERIE"
(cámara sigue abierta, NO presionas nada)
  ↓
Apunta a serial
  → Se detecta ✓
  → Vibra
  → Indicador VERDE
  ↓
No hay más escaneos
  → Cámara se cierra automáticamente
  ↓
Se abre formulario con:
  ✓ Nombre: "Chromebook" (del preset)
  ✓ Código: "CB-12345" (escaneado)
  ✓ Serial: "ABC789" (escaneado)
  ☐ Cantidad: [vacío, lo rellenas]
  ☐ Condición: [selecciona]
  ☐ Ubicación: [rellena]
  ↓
[Guardar]
  ↓
"✓ Guardado"
```

### 3. Si Falla un Escaneo

Si la cámara no detecta el código:
- El indicador sigue azul
- Intenta de nuevo (no hay timeout)
- O toca [⌨️] para escribir a mano

---

## ⚡ Cambios principales

✅ **Escaneo continuo automático** - No presionas botones entre códigos
✅ **UI clara** - Ves exactamente qué campo espera
✅ **Datos se guardan** - Los códigos escaneados van a IndexedDB
✅ **Sin checkboxes** - Los campos fijos se definen en el preset, no en cada item
✅ **Formulario pre-relleno** - Los datos escaneados ya están ahí

---

## 🔧 Editar un Preset

Para cambiar qué campos se escanean:

```
⚙️ Gestionar
  ↓
[✎] en "Chromebook"
  ↓
Ir a "Campos"
  ↓
[✎] Código de barras
  → Marcar/desmarcar "Escaneo continuo"
  → Cambiar nombre, tipo, etc.
  ↓
[Guardar]
```

Importante: **Solo campos de Tipo "Texto" pueden tener escaneo continuo**

---

## 📝 Crear un Nuevo Preset

```
⚙️ Gestionar
  ↓
[➕ Nuevo]
  ↓
Nombre: "Smartboard" 
Icono: "📺"
Nombre fijo: "Smartboard" (opcional)
  ↓
[Crear]
  ↓
Automáticamente crea 3 campos:
  - Nombre (fijo, no editable)
  - Código de barras (continuo)
  - Cantidad (número)
  ↓
[✎] para editar y agregar más campos
```

---

## ✓ Checklist para que funcione

- [ ] Archivo `index.html` actualizado en GitHub
- [ ] Recargaste iPhone (Cmd+Shift+R en Safari)
- [ ] El preset tiene **al menos 1 campo continuo**
- [ ] Los campos continuos son de **Tipo: Texto**
- [ ] Esperas a que detecte (no presionas nada entre códigos)
- [ ] Si falla, presionas [⌨️] para escribir a mano

---

## 🐛 Si aún no se guarda

1. Abre DevTools (F12) en tu Mac
2. Consola → ve si hay errores rojos
3. Abre IndexedDB → Aplicación → inventarioPro → stores
4. Revisa si hay datos en "items"

Si necesitas limpiar y empezar:
```javascript
// En consola:
indexedDB.deleteDatabase('inventarioPro')
location.reload()
```

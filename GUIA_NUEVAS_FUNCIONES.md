# 📦 Inventario Escolar Pro v2 — Guía Completa

## ✨ Novedades principales

### 1. **Sistema de Grupos/Presets Dinámicos**
La app ahora organiza el inventario en **grupos personalizables**:
- **Chromebooks** — campos para código de barras, serial, condición, ubicación
- **Smartboards** — campos para código, serial del PC, serial interno, estado
- **Crea tus propios grupos** — mobiliario, proyectores, tablets, etc.

Cada grupo tiene:
- **Nombre fijo** (opcional) — "Chromebook" se auto-completa al escanear
- **Campos personalizados** — define qué datos recopilar para cada tipo
- **Icono/emoji** — visual rápido para identificarlos
- **Exportación separada** — cada grupo en su propia pestaña en Excel

**Cómo usar:**
1. Toca en la barra superior (donde dice "💻 Chromebooks")
2. Cambia entre grupos deslizando horizontalmente
3. El panel azul debajo muestra el grupo activo y sus campos

**Crear un grupo nuevo:**
1. Toca ⚙️ (arriba a la derecha)
2. "Nuevo grupo"
3. Nombre, icono, nombre fijo (opcional)
4. ¡Listo! Aparecerá en la barra superior

**Editar un grupo:**
1. Toca "Editar" en el panel azul del grupo
2. Cambia nombre, icono, descripción, nombre fijo
3. O **elimina el grupo** y todos sus artículos

---

### 2. **Escaneo Continuo (Modo Rápido)**
El escaneo ahora es **ultra rápido** para múltiples artículos:

**Flujo:**
1. Toca 📷 **Escanear**
2. Escanea un código → se crea el artículo automáticamente
3. Si el código ya existe, **suma +1 a la cantidad**
4. **Sigue escaneando** sin cerrar la cámara
5. El contador en la esquina muestra cuántos has escaneado en la sesión

**Vibración + sonido:** Cada escaneo confirma con vibración (70-50-70ms)

**Ejemplo de flujo real:**
```
1. [Escanea código Chromebook #1] ✓ registrado
   → Scanner aún abierta, listo para el siguiente
2. [Escanea código Chromebook #2] ✓ registrado
3. [Escanea mismo código Chromebook #1] → cantidad +1 automático
4. [Escanea QR de Smartboard] → pregunta porque es otro grupo
5. Cierra scanner cuando termines (botón ✕)
```

**Características:**
- ⌨️ **Escribir código a mano** — si el escaneo falla, tecleas el código
- 💡 **Linterna** — controla la luz del iPhone (útil en salones oscuros)
- 📍 **Sesión activa** — muestra cuántos artículos escaneaste en esta sesión

---

### 3. **Exportación Excel Profesional**
El Excel ahora es mucho más completo:

**Automáticamente incluye:**
- ✅ **Una pestaña por grupo** (Chromebooks, Smartboards, etc.)
- ✅ **Encabezados coloreados** con estilos profesionales
- ✅ **Pestaña de resumen** con totales por grupo
- ✅ **Orden alfabético** dentro de cada grupo
- ✅ **Campos solo relevantes** — cada grupo solo sus campos

**Ejemplo de estructura Excel:**
```
Pestaña 1: "Chromebooks"
├─ Nombre | Código | Serial | Cantidad | Condición | Ubicación | Fecha
├─ Chromebook HP | CB-001 | ABC123 | 1 | Nuevo | Aula 301 | 2026-08-21
├─ Chromebook HP | CB-002 | DEF456 | 2 | Bueno | Aula 302 | 2026-08-20
└─ ...

Pestaña 2: "Smartboards"
├─ Nombre | Código | Serial PC | Serial Interno | Estado | Salón | Notas
├─ Smartboard | SB-001 | PC-111 | INT-111 | Funcionando | Aula 401 | Bien calibrado
└─ ...

Pestaña 3: "Resumen"
├─ Grupo | Total de artículos | Cantidad total
├─ Chromebooks | 15 | 18
├─ Smartboards | 3 | 3
└─ Total general | 18 | 21
```

---

## 🎯 Casos de uso prácticos

### Caso 1: Inventario de Chromebooks
```
1. Crea grupo "Chromebooks" 💻
   - Nombre fijo: "Chromebook"
   - Campos: código, serial, cantidad, condición, ubicación, fecha

2. Escanea 20 Chromebooks:
   - Abre scanner
   - Escanea código barras + serial (2 campos)
   - Selecciona condición y salón
   - Sigue con el siguiente

3. Exporta → Excel con pestaña "Chromebooks"
   - Listo para enviar a dirección
```

### Caso 2: Inventario de Smartboards
```
1. Crea grupo "Smartboards" 📺
   - Campos: código, serial PC, serial interno, estado, salón, notas

2. Por cada Smartboard:
   - Escanea código + serial PC + serial interno
   - Anota si funciona o necesita reparación

3. Exporta → Pestaña separada en Excel
   - Resumen automático de estados
```

### Caso 3: Inventario Mixto (múltiples grupos)
```
1. Crea 3 grupos:
   - Chromebooks 💻
   - Smartboards 📺
   - Proyectores 🎬

2. A lo largo del mes:
   - Escanea según corresponda
   - Cambia de grupo en la barra superior
   - La app guarda todo separado

3. Exporta → Excel con 4 pestañas
   - Cada grupo en su propia pestaña
   - + Resumen ejecutivo
   - Listo para directiva, gerencia, etc.
```

---

## 🔄 Flujo detallado: cómo trabaja la app

### Pantalla principal
```
Header azul: "📦 Inventario Escolar Pro"  [⬇ Exportar] [⚙ Configurar]
    ↓
Barra de grupos: [💻 Chromebooks] [📺 Smartboards] [➕ Nuevo]
    ↓
Panel azul: "💻 Chromebooks — Escanea código, serial"  [Editar]
    ↓
Estadísticas:
  • 45 Artículos totales
  • 52 Unidades (cantidad)
  • 15 En este grupo
    ↓
Búsqueda + Ordenar
    ↓
Lista de artículos en este grupo
    ↓
[➕ Añadir]  [📷 Escanear]
```

### Botones principales
- **📷 Escanear** — abre cámara en modo continuo
- **➕ Añadir** — formulario manual sin escanear
- **⬇ Exportar** — descarga Excel profesional
- **⚙ Configurar** — crear/editar/eliminar grupos

### Dentro del escaneo
```
Pantalla negra + cámara abierta
    ↓
Recuadro central = zona a escanear
    ↓
[⌨️ Escribir a mano] [💡 Linterna] [✕ Cerrar]
    ↓
Contador superior derecha: "Escaneados: 5"
    ↓
"Apunta la cámara. Se detecta automáticamente."
    ↓
[Escanea] → vibra, cierra scanner automáticamente
    ↓
Formulario aparece = complete o escanee más campos
```

---

## 🛠 Personalización avanzada

### Editar campos de un grupo
*(Nota: por ahora, los campos se definen al crear el grupo. Para cambiarlos, elimina y recrea el grupo.)*

**Campos disponibles por tipo:**
- **Texto** — nombres, salones, notas cortas
- **Texto largo** — descripciones, observaciones extensas
- **Número** — cantidad, precio, año
- **Fecha** — cuándo se registró, fecha de compra
- **Lista** — opciones predefinidas (Nuevo/Usado/Dañado, etc.)

### Nombre fijo por grupo
Si dejas "Nombre fijo" vacío → debe escanearse o escribirse
Si pones "Chromebook" → se auto-completa automáticamente

Útil para:
- Chromebooks (siempre es "Chromebook")
- Smartboards (siempre es "Smartboard")
- Pero no para proyectores (hay varios modelos)

---

## 📊 Reportes y análisis

### Desde Excel (después de exportar)
- Cuenta artículos por grupo
- Suma cantidades
- Filtra por estado/condición
- Crea gráficos de distribución

### Desde la app
- Busca rápido por nombre, código, ubicación
- Filtra por grupo automáticamente
- Ordena alfabético, por cantidad, por fecha

---

## ⚡ Tips de rendimiento

### Escaneo rápido
1. **Buena luz** — es el factor #1
2. **Código lleando el recuadro** — no pequeñito
3. **Mano firme** — evita temblores
4. **Distancia 15-20cm** — típico del iPhone
5. **Si falla** → ⌨️ escribe a mano

### Sesiones largas
- Export cada 30-50 artículos como respaldo
- Usa modo continuo (scanner abierta) — es más rápido
- Cambia de grupo con un toque en la barra

---

## 🔒 Privacidad y datos

- ✅ **Todos los datos guardan en tu iPhone** — no en nube
- ✅ **No hay servidor** — funciona 100% offline
- ✅ **Exporta a Excel** — tienes copia de seguridad
- ✅ **Si cambias de iPhone** — puedes exportar e importar (Excel)

---

## 📱 Requisitos

- **iPhone** con Safari (iOS 13+)
- **Primera vez:** carga la app con internet (descarga librerías)
- **Después:** funciona sin internet

---

## 🆘 Solución de problemas

### "No detecta códigos de barras"
- ✓ Mejora la luz (el factor más importante)
- ✓ Acerca más el código (~15cm)
- ✓ Usa ⌨️ para escribir a mano
- ✓ Cierra y reabre scanner

### "La app se cierra al cambiar de grupo"
- Cierra Safari completamente
- Reabre la app
- Los datos están guardados en IndexedDB

### "Excel no se descarga"
- Revisa si Safari tiene permiso de descargas
- Intenta desde WiFi (no celular)
- Usa Chrome en PC si es necesario

### "Quiero cambiar de iPhone"
1. Exporta a Excel desde tu iPhone
2. En el nuevo iPhone, abre la app
3. Recrea los grupos manualmente
4. Usa "Añadir manual" para ingresar de nuevo desde Excel

---

## 🚀 Próximos pasos posibles

Si en el futuro necesitas:
- **Sincronizar entre varios iPhones** → conectar a Google Sheets o Firebase
- **Más campos dinámicos** → editor visual de campos por grupo
- **Importar desde Excel** → leer archivos existentes
- **Códigos QR personalizados** → generar códigos con info del artículo
- **Fotos de artículos** → capturar imágenes junto al código

Avísame y los agregamos. 🎯

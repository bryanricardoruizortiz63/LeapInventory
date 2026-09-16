# 🏫 Versión v3.2 - SALONES + EXCEL MULTI-HOJA

**Fecha:** 2026-09-16  
**Estado:** ✅ LISTA PARA PRODUCCIÓN  
**Archivo:** `inventario-escolar-v3-2-SALONES.html` (44 KB)

---

## 🎯 ¿QUÉ CAMBIÓ EN v3.2?

### ✅ Gestión de Salones
- **32 salones predefinidos** (Salón 1 → Salón 32)
- **Agregar salones** personalizados
- **Eliminar salones** (confirma antes)
- **Tab nuevo en ⚙️** para gestionar salones

### ✅ Campos actualizados
- ❌ **Eliminado:** Campo "Condición" (Excelente, Buena, etc)
- ✅ **Agregado:** Campo "Notas" (texto largo para equipo en hogar)
- ✅ **Agregado:** Campo "Salón" (select obligatorio)

### ✅ Exportación Excel MEJORADA
- 📊 **Una hoja por salón** (Salón 1, Salón 2, ..., Salón 32)
- 📊 **Hoja TOTALES** (consolidado por tipo de equipo)
- 📊 **Formato profesional** con columnas anchas
- 📊 **Editable en Excel** - cambias datos y guardan en el archivo
- 📊 **Nombre automático:** `Inventario_2026-09-16.xlsx`

### ✅ Visualización mejorada
- Items agrupados por salón en la lista
- Muestra notas en vista previa (primeros 20 caracteres)

---

## 🚀 CÓMO FUNCIONA v3.2

### 1️⃣ ESCANEAR ARTÍCULO

```
1. Presionas 📱 Escanear nuevo
   ↓
2. Scanner Bluetooth captura códigos secuenciales
   ↓
3. Se abre formulario pre-llenado
   ↓
4. Completas:
   - Nombre (pre-llenado, ej: "Chromebook")
   - Código (escaneado)
   - Serial (escaneado)
   - Cantidad
   - Ubicación (dónde está en el salón)
   - Notas (si está en hogar, quién la tiene, etc)
   - Salón (SELECT OBLIGATORIO)
   ↓
5. Guardas
```

### 2️⃣ VER INVENTARIO POR GRUPO

```
[💻 Chromebooks]  [🖥️ Smartboards]  [🛒 ChromeCart]
          ↓
Muestra todos los artículos agrupados POR SALÓN
```

### 3️⃣ GESTIONAR SALONES (⚙️ → Salones)

```
┌──────────────────────────┐
│ Grupos  |  Salones  |  Config
├──────────────────────────┤
│                          │
│ Salón 001                │
│ 5 artículos              │
│ [✕ Eliminar]            │
│                          │
│ Salón 002                │
│ 8 artículos              │
│ [✕ Eliminar]            │
│                          │
│ Salón 003                │
│ 3 artículos              │
│ [✕ Eliminar]            │
│                          │
│ [➕ Nuevo salón]         │
│                          │
└──────────────────────────┘
```

**Crear salón:**
- Presiona **[➕ Nuevo salón]**
- Ingresa número (ej: 50)
- ¡Listo! Aparece como "Salón 050"

**Eliminar salón:**
- Presiona **[✕]** en cualquier salón
- Confirma (también borra sus artículos)

### 4️⃣ EXPORTAR A EXCEL (⬇︎)

```
Presiona ⬇︎ en header
   ↓
Genera Excel automáticamente
   ↓
Descarga: Inventario_2026-09-16.xlsx
```

**El Excel tiene:**

#### 🏫 Hojas de Salones (1 por salón)

**Salón 101:**
```
Tipo Equipo | Nombre    | Código | Serial | Cantidad | Ubicación    | Notas
Chromebook  | Chromebook| CB-001 | ABC123 | 1        | Escritorio   | En hogar - Juan
Smartboard  | Smartboard| SB-001 | XYZ789 | 1        | Pared frontal| 
```

**Salón 102:**
```
Tipo Equipo | Nombre    | Código | Serial | Cantidad | Ubicación | Notas
Chromebook  | Chromebook| CB-002 | ABC124 | 1        | Mesa 1    |
```

#### 📊 Hoja TOTALES

```
Tipo Equipo    | Cantidad Total
Chromebooks    | 24
Smartboards    | 5
ChromeCarts    | 3
TOTAL GENERAL  | 32
```

---

## 📝 EJEMPLO: Inventario Completo

### Situación:
- Escuela con 3 salones de clases
- Cada salón tiene Chromebooks y 1 Smartboard
- Algunos Chromebooks están en hogar

### Proceso:

#### 1. Crear salones
- ⚙️ → Salones → ➕ Nuevo → 101, 102, 103

#### 2. Escanear Chromebooks Salón 101
- 💻 Escanear nuevo
- Scanner: **CB-001**
- Scanner: **ABC123**
- Cantidad: **1**
- Ubicación: **Estante A**
- Notas: **(vacío)**
- Salón: **Salón 101** ← OBLIGATORIO
- Guardar

- 💻 Escanear nuevo
- Scanner: **CB-002**
- Scanner: **ABC124**
- Cantidad: **1**
- Ubicación: **Escritorio**
- Notas: **En hogar - María García**
- Salón: **Salón 101**
- Guardar

#### 3. Escanear Smartboard Salón 101
- 🖥️ Escanear nuevo
- Scanner: **SB-001**
- Scanner: **XYZ789**
- Ubicación: **Pared frontal**
- Notas: **(vacío)**
- Salón: **Salón 101**
- Guardar

#### 4. Repetir para Salón 102, 103, etc

#### 5. Exportar Excel
- ⬇︎ Presiona botón exportar
- Descarga: `Inventario_2026-09-16.xlsx`

**Resultado en Excel:**
```
Inventario_2026-09-16.xlsx
├─ Salón 101 (lista de items)
├─ Salón 102 (lista de items)
├─ Salón 103 (lista de items)
└─ TOTALES
   Chromebooks: 6
   Smartboards: 3
   TOTAL: 9
```

---

## 🎨 CAMPOS EN v3.2

| Campo | Tipo | Obligatorio | Escaneo | Ejemplo |
|-------|------|-------------|---------|---------|
| Nombre | Texto (fijo) | ✅ | No | "Chromebook" |
| Código | Texto | ✅ | ✅ | "CB-001" |
| Serial | Texto | ✅ | ✅ | "ABC123" |
| Cantidad | Número | No | No | "1" |
| Ubicación | Texto | No | No | "Escritorio Prof" |
| Notas | Texto largo | No | No | "En hogar - Juan" |
| Salón | Select | ✅ | No | "Salón 101" |

---

## 💾 PERSISTENCIA EN EXCEL

**Importante:** El Excel NO está conectado "en vivo" a la app.

**Cómo funciona:**
1. Escaneas en app → se guarda en IndexedDB
2. Presionas [⬇︎] → genera Excel desde datos actuales
3. Editas en Excel → **cambios locales** (archivo Excel)
4. Guardas Excel en tu computadora
5. **La app sigue con su copia en BD**

**Si quieres sincronizar Excel de vuelta a app:**
- Necesitarías importar (requiere más código)
- Por ahora: **la app es la fuente de verdad**, Excel es el "reporte"

**Ventajas:**
- ✅ Sin servidor, sin API
- ✅ Rápido (todo es local)
- ✅ Seguro (datos en el dispositivo)
- ✅ Offline (funciona sin internet)

---

## 🧪 TESTING EN NAVEGADOR

1. Descarga: `inventario-escolar-v3-2-SALONES.html`
2. Abrelo en navegador (doble click)
3. Presiona ⚙️
4. Ve a tab "Salones"
5. Verás los 32 salones predefinidos
6. Presiona ➕ Nuevo salón
7. Ingresa: 50
8. Crea artículo:
   - 💻 Escanear
   - Código: TEST-001
   - Serial: XYZ
   - Cantidad: 1
   - Ubicación: Prueba
   - Notas: Esta es una prueba
   - Salón: Salón 050
9. Presiona [⬇︎ Exportar]
10. Se descarga `Inventario_YYYY-MM-DD.xlsx`
11. Abre en Excel → ¡Verás las hojas!

---

## 🚀 DESPLEGAR EN GITHUB

### 1. Preparar
```bash
Descarga: inventario-escolar-v3-2-SALONES.html
Renombra a: index.html
```

### 2. Subir a GitHub
- Opción A: GitHub Desktop
  - Abre repo LeapInventory
  - Reemplaza index.html
  - Commit: "Feature v3.2: Salones + Excel multi-hoja"
  - Push

- Opción B: GitHub web
  - Ve a repo
  - Edita index.html
  - Pega contenido de v3.2
  - Commit

### 3. Actualizar sw.js
```javascript
const CACHE_VERSION = 'v15';  // ← Era v14
```

### 4. Hard-reload en dispositivo
```
iPhone: Cmd+Shift+R
Android: Ctrl+Shift+R
Cierra app completamente
Reabre
```

---

## 📋 CHECKLIST

- [ ] Descargaste v3.2
- [ ] Probaste en navegador
- [ ] Creaste salones nuevos
- [ ] Escaneaste artículos con salones
- [ ] Exportaste Excel
- [ ] Abriste Excel y viste las hojas
- [ ] Estás listo para GitHub

---

## ⚡ RESUMEN v3.2

| Feature | v3 | v3.2 |
|---------|----|----|
| Gestión de grupos | ✅ | ✅ |
| Gestión de salones | ❌ | ✅ |
| Campo Salón | ❌ | ✅ |
| Campo Notas | ❌ | ✅ |
| Campo Condición | ✅ | ❌ |
| Exportación CSV | ✅ | ❌ |
| Exportación Excel | ❌ | ✅ |
| Multi-hoja Excel | ❌ | ✅ |
| Hoja Totales | ❌ | ✅ |
| Items por salón | ❌ | ✅ |

---

## 🎉 ¡LISTO!

v3.2 es la versión **COMPLETA** con **salones** y **Excel profesional**.

Descarga → Prueba → Despliega → ¡Usa! 🚀

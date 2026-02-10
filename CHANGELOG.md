# Q3 Map Config Generator - Changelog

## [v2.0] - 2026-02-10 - Sistema Dinámico de Detección de Modos

### ✨ Nuevas Características
- **Sistema dinámico de detección de modos de juego**: Ya no requiere configuración manual para cada modo nuevo
- **Auto-detección inteligente**: El sistema detecta automáticamente qué tipo de generador usar basándose en el nombre del modo:
  - Modos tipo CTF (contienen "ctf"): usan `caplimit`
  - Modos tipo Duel (contienen "duel", "1v1", "2v2", "tourney"): usan formato duel
  - Modos RA3: usan formato especial con campo `arena`
  - Otros modos: usan formato FFA con `fraglimit` por defecto

### 🔧 Mejoras Backend
- Eliminado filtro de tipos soportados - ahora acepta **cualquier tipo** que venga en los archivos `.arena`
- Nueva función `determine_generator_type()` que clasifica automáticamente el tipo de generador
- Generación automática de nombres de archivo: `{tipo}maps.txt`
- Código más mantenible y extensible

### 🎨 Mejoras Frontend
- **Stats dinámicos**: Muestra automáticamente todos los modos encontrados, no solo una lista fija
- **Tarjetas dinámicas**: Genera tarjetas de configuración para modos nuevos con valores por defecto inteligentes
- Etiquetas mejoradas para modos nuevos con indicador "(Auto-detected)"
- Ordenamiento alfabético de modos en panel de estadísticas

### 📋 Modos Preconfigurados (con configuraciones optimizadas)
- FFA, CTF, CTFS, Tourney, 1v1, 2v2
- Team, TDM, RA, RA3
- CA (Clan Arena), FT (Freeze Tag), HM (HoonyMode)
- DA (Duel Arena), NTF (No Team Flags), FTAG (Flag Tag)

### 🚀 Ventajas del Sistema Dinámico
1. **Extensibilidad**: Soporta modos futuros sin modificar código
2. **Flexibilidad**: Detecta modos custom de mapas de comunidad
3. **Automatización**: Elimina la necesidad de actualizar listas manualmente
4. **Compatibilidad**: Mantiene todas las configuraciones existentes

### 🔍 Ejemplo de Auto-Detección
```
Modo en .arena: "newctf"      → Detecta CTF → Genera con caplimit
Modo en .arena: "customduel"  → Detecta Duel → Genera con fraglimit (formato tourney)
Modo en .arena: "zombies"     → Default FFA → Genera con fraglimit
```

### 📦 Archivos Modificados
- `app_gui.py`: Sistema de clasificación dinámica y función `determine_generator_type()`
- `templates/index.html`: Generación dinámica de stats y tarjetas con detección inteligente

---

## [v1.0] - 2026-02-09 - Versión Inicial

### Características Originales
- Escaneo de archivos .pk3 y extracción de .arena
- Generación de configuraciones para 15+ modos de juego
- Interfaz web responsive con Flask
- GUI nativa con PyWebView
- Detección automática de puerto disponible (5000-5009)
- Detección de IP LAN para acceso en red
- Soporte RA3 con dual output path
- Ejecutable standalone sin dependencias Python

# ⚡ Q3 Map Config Generator v2.0

> **Sistema Dinámico de Generación Automática** de archivos de configuración de mapas para Quake 3 Arena CPMA

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-3.1.2-green.svg)](https://flask.palletsprojects.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 🚀 Características Principales

### ✨ Versión 2.0 - Sistema Dinámico
- 🤖 **Auto-detección de modos de juego**: Detecta automáticamente modos nuevos sin configuración manual
- 🎯 **Clasificación inteligente**: Identifica automáticamente si un modo usa `fraglimit`, `caplimit` o formato especial
- 📊 **Stats dinámicos**: Muestra todos los modos encontrados, no solo una lista fija
- 🎨 **Tarjetas auto-generadas**: Crea interfaces de configuración para modos desconocidos
- ♾️ **Extensibilidad infinita**: Soporta cualquier modo que aparezca en archivos `.arena`

### 🎮 Funcionalidades Core
- 🔍 Escanea automáticamente todos los archivos .pk3 en baseq3
- 📋 Parsea archivos .arena y extrae metadata de mapas
- 🎯 Clasifica mapas por tipo automáticamente
- ⚙️ Interfaz web responsive para configurar parámetros
- 💾 Genera archivos de configuración listos para usar
- 👁️ Previsualización en tiempo real antes de generar
- 🪟 Ventana GUI nativa (no necesitas navegador)
- 🔌 Detección automática de puerto disponible (5000-5009)
- 🌐 Acceso por LAN con IP detectada automáticamente

### 🎲 Modos Soportados (+ Infinitos Más)

**Preconfigurados con valores optimizados:**
- **FFA** - Free For All
- **CTF / CTFS** - Capture The Flag / Strawberry
- **Tourney / 1v1 / DA** - Duelos
- **Team / TDM** - Team Deathmatch
- **CA** - Clan Arena
- **FT** - Freeze Tag
- **HM** - HoonyMode
- **RA / RA3** - Rocket Arena
- **NTF** - No Team Flags
- **2v2** - Two vs Two
- **FTAG** - Flag Tag

**Y cualquier modo nuevo** que aparezca en tus archivos `.arena` será detectado y configurado automáticamente.

## 📦 Versiones Disponibles

### 🪟 Versión GUI (Ventana Integrada) - RECOMENDADA
- Ejecutable independiente con interfaz gráfica propia
- No necesitas abrir el navegador manualmente
- Ventana nativa de Windows con la aplicación embebida
- Más profesional y fácil de usar
- **Archivo:** `dist\Q3MapConfigGenerator.exe`

### 🌐 Versión Solo Servidor
- Inicia un servidor web local
- Debes abrir manualmente el navegador
- Útil si prefieres usar tu navegador favorito
- **Archivos:** `app.py` o `run.bat` o `run_exe.bat`

## Instalación y Uso

### Opción 1: Ejecutable con GUI (¡RECOMENDADO!)

**¡La forma más fácil! Ventana propia con la aplicación integrada**

1. Haz doble clic en `run_gui.bat` o ejecuta directamente `dist\Q3MapConfigGenerator.exe`
2. La aplicación se abrirá en su propia ventana
3. ¡No necesitas abrir el navegador!

### Opción 2: Ejecutable modo web

1. Haz doble clic en `run_exe.bat` (versión solo servidor)
2. Abre tu navegador en: http://localhost:5000

### Opción 3: Con Python

1. Asegúrate de tener Python 3.8+ instalado

2. Instala las dependencias:
```bash
pip install -r requirements.txt
```

3. Ejecuta la aplicación:
```bash
python app.py
```
O simplemente haz doble clic en `run.bat`

4. Abre tu navegador en: http://localhost:5000

## Pasos para Usar la Aplicación

1. **Configurar Rutas** (primera vez):
   - Haz clic en el botón de configuración (⚙️)
   - Ingresa la ruta de tu carpeta baseq3 de Quake 3
   - Ingresa la ruta donde quieres guardar los archivos generados
   - Guarda la configuración

2. Haz clic en "Escanear Archivos .pk3" para analizar todos los mapas

4. Configura los parámetros para cada tipo de mapa:
   - **Min Players**: Número mínimo de jugadores
   - **Max Players**: Número máximo de jugadores
   - **Fraglimit/Caplimit**: Límite de frags o capturas
   - **Timelimit**: Límite de tiempo en minutos

5. Usa "Previsualizar" para ver cómo quedará el archivo

6. Haz clic en "Generar Archivo" para crear la configuración

## Archivos Generados

Los archivos se guardan en: `G:\Games\Quake3\cpma\cfg-maps\`

**Modos individuales:**
- `ffamaps.txt` - Mapas Free For All
- `1v1maps.txt` - Mapas 1v1 / Duel
- `tourneymaps.txt` - Mapas Tourney
- `damaps.txt` - Mapas Duel Arena
- `hmmaps.txt` - Mapas HoonyMode
- `2v2maps.txt` - Mapas 2 vs 2

**Modos de equipo:**
- `teammaps.txt` - Mapas Team
- `tdmmaps.txt` - Mapas Team Deathmatch
- `ctfmaps.txt` - Mapas Capture The Flag
- `ctfsmaps.txt` - Mapas CTF Strawberry
- `ntfmaps.txt` - Mapas No Team Flags
- `ftagmaps.txt` - Mapas Flag Tag

**Modos especiales:**
- `camaps.txt` - Mapas Clan Arena
- `ftmaps.txt` - Mapas Freeze Tag
- `mamaps.txt` - Mapas Rocket Arena

## Estructura de Archivos .arena

El programa busca archivos con esta estructura dentro de los .pk3:

```
{
map         "ASSault"
longname    "Levelord®'s ASSault"
bots        "Sarge Hunter Klesk Anarki"
fraglimit   17
timelimit   17
type        "ffa team tourney"
}
```

## Tipos de Mapas Soportados

**Modos de 1-4 jugadores:**
- **FFA** - Free For All
- **1v1 / Tourney** - Duelo 1vs1
- **DA** - Duel Arena
- **HM** - HoonyMode
- **2v2** - Two vs Two

**Modos de equipo:**
- **Team** - Equipo genérico
- **TDM** - Team Deathmatch
- **CTF** - Capture The Flag
- **CTFS** - CTF Strawberry
- **NTF** - No Team Flags
- **FTAG** - Flag Tag

**Modos especiales:**
- **CA** - Clan Arena
- **FT** - Freeze Tag
- **RA** - Rocket Arena

## Tecnologías

- **Backend**: Python + Flask
- **Frontend**: HTML5 + CSS3 + JavaScript
- **Parser**: Expresiones regulares para archivos .arena
- **ZIP**: Librería zipfile para leer .pk3

## Autor

Generado con GitHub Copilot

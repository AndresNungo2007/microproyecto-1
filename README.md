# Microproyecto 1: Generar secuencias notas musicales.

## Librería FluidSynth

### Tabla de Compatibilidad Multiplataforma

| Componente | Windows | macOS | Linux |
|-----------|---------|-------|-------|
| **Biblioteca FluidSynth** | `libfluidsynth-3.dll` | `libfluidsynth.dylib` | `libfluidsynth.so` |
| **Driver de Audio** | `dsound` | `coreaudio` | `alsa` |
| **Ubicación típica biblioteca** | `C:\Tools\FluidSynth\bin\` | `/opt/homebrew/lib/`<br>`/usr/local/lib/` | `/usr/lib/`<br>`/usr/lib64/` |
| **Ubicación típica soundfont** | `.\soundfonts\` | `/opt/homebrew/share/soundfonts/`<br>`/usr/local/share/soundfonts/` | `/usr/share/soundfonts/`<br>`/usr/share/sounds/sf2/` |
| **Gestor de paquetes** | Manual | Homebrew | apt/yum |

**El código detecta automáticamente** tu sistema operativo y usa las configuraciones correctas.

### Inicio Rápido por Sistema Operativo

#### Para usuarios de **macOS** (como tú):
```bash
# 1. Instalar FluidSynth
brew install fluid-synth

# 2. Descargar soundfont
mkdir -p soundfonts
curl -o soundfonts/FluidR3_GM.sf2 https://member.keymusician.com/Member/FluidR3_GM/FluidR3_GM.sf2

# 3. Ejecutar las celdas 13, 57 y 59 del notebook
```

#### Para usuarios de **Linux**:
```bash
# 1. Instalar FluidSynth y soundfont
sudo apt-get update
sudo apt-get install fluidsynth libfluidsynth-dev fluid-soundfont-gm

# 2. El soundfont ya está instalado en /usr/share/sounds/sf2/
# 3. Ejecutar las celdas 13, 57 y 59 del notebook
```

#### Para usuarios de **Windows**:
```powershell
# 1. Descargar FluidSynth desde GitHub y extraer a C:\Tools\FluidSynth\
# 2. Descargar soundfont manualmente y guardar en .\soundfonts\FluidR3_GM.sf2
# 3. Ejecutar las celdas 13, 57 y 59 del notebook
```


**Sistema Operativo:** Windows 11 x64    

En el disco local, si es posible en la raíz del disco, cree la siguiente carpeta `Tools`, luego `FluidSynth`.
Ejemplo: _**ruta**_ `C:\Tools\FluidSynth`.

Luego, descargue el archivo comprimido [FluidSynth 2.4.8](https://github.com/FluidSynth/fluidsynth/releases/tag/v2.4.8) que contiene las dependencias de la librería `libfluidsynth-3.dll`. Archivo: `fluidsynth-2.4.8-win10-x64.zip`.  
Copie todos los archivos y ubiquelos dentro de _**ruta**_.

Luego, descargue el archivo comprimido [FluidSynth 2.5.0](https://github.com/FluidSynth/fluidsynth/releases/tag/v2.5.0) el cual se debe copiar y reemplazar en `bin` → `C:\Tools\FluidSynth\bin`. Archivo a descargar: `fluidsynth-v2.5.0-win10-x64-glib.zip`.  
- fluidsynth.exe
- libfluidsynth-3.dll

Con esto queda funcional el notebook `Microproyecto1.ipynb`.

## Archivo soundfont
- Descarguelo de [Soundfont](https://member.keymusician.com/Member/FluidR3_GM/index.html) y ubiquelo en la carpeta `soundfonts` de este proyecto.

## 6.1. Configuración de FluidSynth (Multiplataforma)

Esta sección configura FluidSynth para convertir archivos MIDI a WAV. El código es **compatible con Windows, macOS y Linux**.

### Instalación de FluidSynth por sistema operativo:

#### **macOS**
```bash
# Con Homebrew
brew install fluid-synth

# Verificar instalación
which fluidsynth
```

#### **Linux (Ubuntu/Debian)**
```bash
# Instalar FluidSynth y librerías de desarrollo
sudo apt-get update
sudo apt-get install fluidsynth libfluidsynth-dev

# Opcional: Instalar soundfont
sudo apt-get install fluid-soundfont-gm
```

#### **Windows**
1. Descargar FluidSynth desde: https://github.com/FluidSynth/fluidsynth/releases
2. Extraer a `C:\Tools\FluidSynth\`
3. Asegurarse que `libfluidsynth-3.dll` esté en `C:\Tools\FluidSynth\bin\`

### Soundfonts necesarios:

Para renderizar audio, necesitas un archivo `.sf2` (soundfont):
- **Descarga recomendada**: [FluidR3_GM.sf2](https://member.keymusician.com/Member/FluidR3_GM/FluidR3_GM.sf2)
- **Ubicación**: Guardar en `./soundfonts/FluidR3_GM.sf2`
- **Tamaño**: ~142 MB

El código busca automáticamente soundfonts en las ubicaciones estándar de cada sistema operativo.
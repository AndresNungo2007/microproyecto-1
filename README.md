# Microproyecto 1: Referencia instalaciones a tener en cuenta

## Librería FluidSynth

### Instalación de FluidSynth por sistema operativo:
Esta sección configura FluidSynth para convertir archivos MIDI a WAV. El código es **compatible con Windows, macOS y Linux**.

#### Para usuarios de **macOS**:
```bash
# 1. Instalar FluidSynth
brew install fluid-synth

# Verificar instalación
which fluidsynth

# 2. Descargar soundfont
mkdir -p soundfonts
curl -o soundfonts/FluidR3_GM.sf2 https://member.keymusician.com/Member/FluidR3_GM/FluidR3_GM.sf2
```

#### Para usuarios de **Linux (Ubuntu/Debian)**:
```bash
# 1. Instalar FluidSynth y soundfont
sudo apt-get update
sudo apt-get install fluidsynth libfluidsynth-dev fluid-soundfont-gm

# 2. El soundfont ya está instalado en /usr/share/sounds/sf2/
sudo apt-get install fluid-soundfont-gm
```

#### Para usuarios de **Linux (Coursera)**:
Se debe compilar este archivo `fluidsynth_local.zip` en un sistema operativo Linux, en este caso se uso Ubuntu 24.04:
```
git clone https://github.com/FluidSynth/fluidsynth.git
cd fluidsynth
git checkout master
git pull origin master
rm -rf build
mkdir build && cd build
cmake ..   -DCMAKE_INSTALL_PREFIX=../../fluidsynth_local/install   -Denable-alsa=ON   -Denable-aufile=ON   -Denable-pipewire=OFF   -Denable-pulseaudio=OFF   -Denable-jack=OFF   -Denable-sdl2=OFF   -Denable-dbus=OFF
make -j$(nproc)
make install
cd ../../
zip -r fluidsynth_local.zip fluidsynth_local/
```
De esta manera se genera el archivo `fluidsynth_local.zip` listo para importar a Jupyter en Coursera.

Estando en Jupyter, se debe cargar este archivo `fluidsynth_local.zip`, y ya el _notebook_  `Microproyecto1.ipynb` se encarga de realizar unzip y usar las dependencias.


#### Para usuarios de **Windows**:
```powershell
# 1. Descargar FluidSynth desde GitHub y extraer a C:\Tools\FluidSynth\
# 2. Descargar soundfont manualmente y guardar en .\soundfonts\FluidR3_GM.sf2
``` 

En la raíz del disco local, cree la siguiente carpeta `Tools`, luego `FluidSynth`.
Ejemplo: _**ruta**_ `C:\Tools\FluidSynth`.

Luego, descargue el archivo comprimido [FluidSynth 2.4.8](https://github.com/FluidSynth/fluidsynth/releases/tag/v2.4.8) que contiene las dependencias de la librería `libfluidsynth-3.dll`. Archivo: `fluidsynth-2.4.8-win10-x64.zip`.  
Copie todos los archivos y ubiquelos dentro de _**ruta**_.

Luego, descargue el archivo comprimido [FluidSynth 2.5.0](https://github.com/FluidSynth/fluidsynth/releases/tag/v2.5.0) el cual se debe copiar y reemplazar en `bin` → `C:\Tools\FluidSynth\bin`. Archivo a descargar: `fluidsynth-v2.5.0-win10-x64-glib.zip`.  
- fluidsynth.exe
- libfluidsynth-3.dll

Con esto queda funcional el _notebook_ `Microproyecto1.ipynb`.


## Archivo soundfont
Para renderizar audio, necesitas un archivo `.sf2` (soundfont):
- **Descarga recomendada**: Descárguelo de [FluidR3_GM.sf2](https://keymusician01.s3.amazonaws.com/FluidR3_GM.zip) y ubíquelo en la carpeta `soundfonts` al mismo nivel donde se ejecuta el _notebook_.
- **Ubicación**: Guardar en `./soundfonts/FluidR3_GM.sf2`
- **Tamaño**: ~142 MB

El código busca automáticamente soundfonts en las ubicaciones estándar de cada sistema operativo.
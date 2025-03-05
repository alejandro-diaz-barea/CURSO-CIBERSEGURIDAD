# Apuntes análisis de RAM

```bash
vol.py -f adquisicion imageinfo
```


```bash
vol.py -f adquisicion --profile=perfil pslist
```
Lista los procesos activos en el sistema según el perfil especificado

```bash
vol.py -f adquisicion --profile=perfil netscan
```
Muestra las conexiones de red activas y puertos abiertos en el momento del volcado

```bash
vol.py -f adquisicion --profile=perfil psscan
```
Realiza un escaneo profundo de la memoria en busca de estructuras de procesos, incluyendo procesos terminados u ocultos

```bash
vol.py -f adquisicion --profile=perfil procdump -p <PID> -D outout/
```
Extrae la memoria del proceso con el PID indicado y la guarda en el directorio "outout/"

```bash
vol.py -f adquisicion --profile=perfil modules
```
Lista los módulos cargados en memoria (drivers, librerías, etc.) en el sistema volcado

```bash
vol.py -f adquisicion --profile=perfil svcscan
```
Examina el registro del sistema para listar los servicios y sus estados

```bash
vol.py -f adquisicion --profile=perfil cmdscan
```
Extrae el historial de comandos ejecutados en sesiones de CMD del sistema

```bash
vol.py -f adquisicion --profile=perfil console
```
Muestra las sesiones de consola activas o recientes en el sistema volcado

```bash
vol.py -f adquisicion --profile=perfil dumpfiles -D output/
```
Extrae archivos de la imagen de memoria y los guarda en el directorio "output/"

```bash
vol.py -f adquisicion --profile=perfil strings
```
Extrae todas las cadenas de texto legibles de la imagen de memoria para su análisis

```bash
vol.py -f adquisicion --profile=perfil hivelist
```
Lista las colmenas del registro (hives) cargadas en la imagen de memoria

```bash
vol.py -f adquisicion --profile=perfil envars
```
Muestra las variables de entorno de los procesos activos en el sistema

```bash
vol.py -f adquisicion --profile=perfil usbenvs
```
Muestra las variables de entorno relacionadas con dispositivos USB en el sistema volcado

```bash
vol.py -f adquisicion --profile=perfil pstree
```
Muestra la jerarquía de procesos en forma de árbol, permitiendo ver las relaciones entre procesos

```bash
vol.py -f adquisicion --profile=perfil filescan
```
Realiza un escaneo de la memoria en busca de archivos, mostrando rutas y offsets donde se encuentran

```bash
vol.py -f adquisicion --profile=perfil mftparser  > mft.txt
```
Analiza la Master File Table (MFT) para recuperar información de archivos del sistema y la guarda en "mft.txt"

```bash
vol.py -f adquisicion --profile=perfil handles
```
Lista todos los manejadores de objetos abiertos por los procesos en el sistema volcado, incluyendo archivos y otros recursos
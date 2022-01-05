# PDF Quirk


**PDF Quirk** es una pequeña herramienta de oficina de ayuda para generar archivos PDF a partir de imágenes de manera fácil y rápida para compartirlos en línea.

Admite el origen de las imágenes desde un medio de almacenamiento de nuestro equipo u obtenerlas directamente desde un escáner.

![Screenshot](https://github.com/dragotin/pdfquirk/raw/master/resources/screenshot1.png)

**PDF Quirk** utiliza herramientas de código abierto especializadas, en vez de reinventar la rueda.

## Características

Estas son las funcionalidades que tiene **PDF Quirk**:

- Una interfaz simple aunque potente, agradable de utilizar para hacer exactamente su trabajo.
- Creación de documentos PDF multipáginas de alta calidad desde imágenes.
- Archivos PDF de pequeño tamaño, aunque de alta calidad.
- Soporte para escáneres a través del paquete SANE.
- Manipulación básica de imágenes como rotación de imágenes o cambio de secuencia.
- Enderezamiento de las imágenes escaneadas.
- Opciones de salida de PDF básicas como margen, tamaño de papel y orientación.

## Descargas y publicaciones

**PDF Quirk** está mantenido en [Github](https://github.com/dragotin/pdfquirk).

La forma de utilizar **PDF Quirk** es tanto con los paquetes de software para la distribución deseada como mediante la AppImage, que pueden ser descargadas desde aquí.

### Publicaciones

La publicación actual es la versión 0.95 que fue publicada el 30 de diciembre de 2021 [Changelog](Changelog.md)

Está disponible desde la [página de publicaciones de Github](https://github.com/dragotin/pdfquirk/releases/tag/v0.95).

### Paquetes

Aún no muchas distribuciones de Linux tienen en sus paquetes **PDF Quirk**, pero hay paquetes disponibles para openSUSE desde mi [página de openSUSE Buildservice](https://software.opensuse.org/package/pdfquirk).

A medida que **PDF Quirk** mejore, estará disponible en los repositorios de mas distribuciones. Permanezca al tanto de las novedades.

### AppImage

**PDF Quirk** está disponible como una compilación automática en formato [AppImage](https://appimage.org/). Puede ser [descargada desde Github](https://github.com/dragotin/pdfquirk/releases/tag/v0.95).

Con la AppImage, **PDF Quirk** puede ser utilizada directamente en la mayoría de las instalaciones de Linux. Simplemente descargue el archivo, añada permisos de ejecución y ejecute la aplicación. [Cómo ejecutar una AppImage (enlace en inglés)](https://docs.appimage.org/introduction/quickstart.html#how-to-run-an-appimage)

### Compilado desde el código fuente

La rama de desarrollo del código fuente de **PDF Quirk** puede ser clonada desde la [página de Github](https://github.com/dragotin/pdfquirk).

Los archivos tarballs de las publicaciones estables se pueden encontrar en [la página de publicaciones de Github](https://github.com/dragotin/pdfquirk/releases).

Para compiar **PDF Quirk**, se necesita una configuración de desarrollo de Qt 5.x o Qt 6.x.

Desempaquete el archivo fuente y vaya al directorio superior de la fuente. A partir de ahí, realice los siguientes pasos:

```
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=/usr/local ..
make
make install
```

Esto instalará pdfquirk en la ruta `/usr/local/bin` de su equipo.

### Dependencias

Para ejecutarse, se necesita la herramienta [convert](https://imagemagick.org/script/convert.php) del paquete [ImageMagick](https://imagemagick.org/script/index.php). La utilidad `scanimage` de SANE es utilizada para el escaneo de imágenes (opcional).
Se recomienda instalarlos mediante el administrador de paquetes de su distribución de Linux, a menos que se utilice **PDF Quirk** mediante AppImage.

Para poder alinear las imágenes, **PDF Quirk** admite de manera opcional la herramienta [deskew](https://galfar.vevb.net/wp/projects/deskew/). Si está instalada y disponible, será utilizada para enderezar las imágenes. De lo contrario será utilizada la función de enderezar las imágenes.

## Configuración

Para configurar **PDF Quirk**, abra el área de configuración haciendo clic en el campo del menú de Configurar. Dos líneas editables permiten establecer una línea de comando para escaneo monocromático y en color.

### SANE scanimage

**PDF Quirk** utiliza la utilidad para la línea de comandos `scanimage` para obtener las imágenes desde un escáner. Viene con los paquetes SANE que son estándar para los escáneres en Linux.

Para escanear con **PDF Quirk**, se debe encontrar y establecer en la configuración un comando `scanimage` òptimo para el escáner. Ya que todos los dispositivos son tan diferentes y ofrecen diferentes opciones de escaneo, no tiene mucho sentido establecer aquí unos valores predeterminados.

Para obtener un resultado razonable para el PDF, el escaneo debe

1. tener una resolución de 150 o 200 dpi,
2. ser escaneado en modo escala de grises en monocromo o color,
3. no tener una profundidad de color muy grande.

Tanbién asegúrese de configurar el tamaño adecuado de escaneo. **PDF Quirk** asumirá que toda la página es escaneada.

Para aprender más sobre el proyecto SANE y la herramienta scanimage, puede encontrar más información en la [página de ayuda de scanimage](http://www.sane-project.org/man/scanimage.1.html).

Si tiene una manera más adecuada de obtener las imágenes, también es posible hacer que **PDF Quirk** la utilice.

`scanimage` de manera predeterminada envía los datos de la imagen escaneada a la salida estándar. **PDF Quirk** está preparado para ello y recoge los datos desde allí.

Una línea de comandos típica de scanimage podría tener un aspecto similar a este:
```
scanimage --mode '24bit Color[Fast]' --resolution 150 -l 0 -t 0 -x 210 -y 297 --format png
```

Si se debe usar otra herramienta para crear PDF que escriba su salida directamente en un archivo en lugar de en la salida estándar, la línea de comando puede contener el marcador de posición `%OUTFILE`. Si está en la cadena de línea de comando, **PDF Quirk** lo reemplazará por un nombre de archivo en el que la herramienta pueda escribir (desde la versión 0.91 en adelante).

**Atención**: Para citar los parámetros de la línea de comandos que contienen espacios, utilice *comillas simples*. No use comillas dobles, ya que el analizador **PDF Quirks** no puede manejarlo adecuadamente.

### Opciones de PDF

Desde la versión 0.95 **PDF Quirk** admite algunas opciones básicas de PDF. En la página de configuración, los usuarios pueden establecer el tamaño, la orientación o el margen de la página.

![Opciones de PDF](https://github.com/dragotin/pdfquirk/raw/master/resources/screenshot_configoptions.png)

Las configuraciones se quedan establecidas para todas las creaciones de PDF posteriores.

## Contribuciones

Por favor, informe de deseos y errores en el [seguidor de incidencias](https://github.com/dragotin/pdfquirk/issues).

¡Los aportes de código son muy bienvenidos!


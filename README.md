# PDF Quirk

PDF Quirk is a utility to create PDFs from images easily and fast. The images can either be loaded from storage or directly be scanned.

It is just a little office helper tool to generate PDFs easily to share them online.

![Screenshot](https://github.com/dragotin/pdfquirk/raw/master/resources/screenshot1.png)

PDF Quirk uses the very well functioning tools `convert` from [ImageMagick](https://imagemagick.org/index.php) and `scanimage` from the [SANE project](http://www.sane-project.org/) instead of reinventing the wheel.

## Downloads and Releases

### Releases
The current public release is version 0.93 which was released on June, 29th, 2020. 

It is available from the  [Github Release Page](https://github.com/dragotin/pdfquirk/releases/tag/v0.93).

The first public release of PDF Quirk has the version number 0.9 and is available from the [Github Release Page](https://github.com/dragotin/pdfquirk/releases/tag/v0.9).

### Packages

Not many distros are packaging it PDF Quirk yet - but packages for openSUSE are available from my [openSUSE Buildservice Page](https://software.opensuse.org/package/pdfquirk).

As soon as PDF Quirk improves, it will make it's way into the repositories of distributions.

### AppImage

PDF Quirk is available as an automatic built [AppImage](https://appimage.org/). It can be [downloaded from Github](https://github.com/dragotin/pdfquirk/releases/tag/continuous).

With the AppImage, PDF Quirk can be used on most Linux installations right away. Just download the file, add executable permissions, and run. [How to run an AppImage](https://docs.appimage.org/introduction/quickstart.html#how-to-run-an-appimage)

### Building from Source

The PDF Quirk source code development branch can be cloned on the [Github page](https://github.com/dragotin/pdfquirk). 

Stable release tarballs can be found on the [Github release page](https://github.com/dragotin/pdfquirk/releases).

To build PDF Quirk, a Qt 5.x development setup is needed. 

Unpack the source archive and go to the top directory of the source. From there, perform the following steps:

```
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=/usr/local ..
make
make install
```

This will install pdfquirk to `/usr/local/bin` on the computer. 

On runtime, the tool `convert` from [ImageMagick](https://imagemagick.org/script/convert.php) is needed to convert to pdf. The utility `scanimage` from SANE is used for scanning (optional). It is recommended to install these through the package manager of the Linux distribution.

## Configuration

### SANE scanimage

PDF Quirk uses the command line utility `scanimage` to produce images from the scanner. It comes with the SANE packages which are standard for scanners under linux.

To scan with PDF Quirk, an optimal `scanimage` command for the scanner device must be found and put into the configuration. Since all the scanner devices are so different and offer different scan options, it does not make too much sense to use a default here.

To get a reasonable result for the PDF, the scan should

1. have a resolution of 150 or 200 dpi.
2. be scanned in mode Grayscale for monochrome of Color.
3. not have a too big color depth

Also be sure to configure the right scan size. PDF Quirk assumes that a whole page
is scanned.

To learn more about the SANE project and the scanimage tool, refer to the [scanimage manpage](http://www.sane-project.org/man/scanimage.1.html) for details.

If you have a better way of producing images, it is also possible to make PDF Quirk use that.

### Configuration

To configure PDF Quirk, open the configuration area by clicking the Configure menu item. Two editable line allow to apply a command line for monochrome and color scan.

Note that `scanimage` by default sends the scanned image to standard out. PDF Quirk is prepared to that and reads it from there.

If another tool should be used to create PDF that writes its output directly to a file rather than to stdout, the commandline may contain the placeholder `%OUTFILE`. If that is in the command line string, PDF Quirk will replace that by a filename the tool can write to (From version 0.91 on).s

**Attention**: To quote command line parameters which contain spaces only the use of *single quotes* is supported. Do not use double quotes, as PDF Quirks parser can not properly deal with that.

## Contributions

Please report wishes and bugs in the [Issue Tracker](https://github.com/dragotin/pdfquirk/issues).

Pull requests that change code are very welcome!




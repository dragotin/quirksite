# PDF Quirk


PDF Quirk is a little office helper tool to generate PDFs from images easily and fast to share them online.

The source images can either be loaded from disk or directly be acquired from a scan device.

![Screenshot](https://github.com/dragotin/pdfquirk/raw/master/resources/screenshot1.png)

PDF Quirk utilizes specialized open source tools rather than reinventing the wheel.

## Features

These features are supported by PDF Quirk:

- Simple yet powerful and nice user interface for exactly one job.
- Creation of high quality multi page PDF documents from images.
- Small PDF file size, yet high quality.
- Support for scanners through the SANE package.
- Basic image manipulation like rotating images or sequence change.
- Deskewing of scanned images
- Basic PDF output options like margin, paper size and -orientation.

## Downloads and Releases

PDF Quirk is maintained on [Github](https://github.com/dragotin/pdfquirk).

The recommended way of using PDF Quirk is either via packages from the distribution or via the AppImage that can be downloaded here.

### Releases

The current public release is version 0.95 which was released on December, 30th, 2021. [Changelog](Changelog.md)

It is available from the  [Github Release Page](https://github.com/dragotin/pdfquirk/releases/tag/v0.95).

### Packages

Not many Linux distros are packaging PDF Quirk yet - but packages for openSUSE are available from my [openSUSE Buildservice Page](https://software.opensuse.org/package/pdfquirk).

As PDF Quirk improves, it will make it's way into the repositories of distributions. Stay tuned.

### AppImage

PDF Quirk is available as an automatic built [AppImage](https://appimage.org/). It can be [downloaded from Github](https://github.com/dragotin/pdfquirk/releases/tag/v0.95).

With the AppImage, PDF Quirk can be used on most Linux installations right away. Just download the file, add executable permissions, and run. [How to run an AppImage](https://docs.appimage.org/introduction/quickstart.html#how-to-run-an-appimage)

### Building from Source

The PDF Quirk source code development branch can be cloned on the [Github page](https://github.com/dragotin/pdfquirk).

Stable release tarballs can be found on the [Github release page](https://github.com/dragotin/pdfquirk/releases).

To build PDF Quirk, a Qt 5.x or Qt 6.x development setup is needed.

Unpack the source archive and go to the top directory of the source. From there, perform the following steps:

```
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=/usr/local ..
make
make install
```

This will install pdfquirk to `/usr/local/bin` on the computer.

### Runtime Dependencies

At runtime, the tool [convert](https://imagemagick.org/script/convert.php) from the [ImageMagick](https://imagemagick.org/script/index.php)-package is needed. The utility `scanimage` from SANE is used for scanning (optional).
It is recommended to install these through the package manager of the Linux distribution unless PDF Quirk is used through the AppImage.

To use deskewing for images, PDF Quirk optionally supports the tool [deskew](https://galfar.vevb.net/wp/projects/deskew/). If it is installed and available, it will be used to deskew images. Otherwise the convert deskew function is used.

## Configuration

To configure PDF Quirk, open the configuration area by clicking the Configure menu item. Two editable lines allow to set a command line for monochrome and color scan.

### SANE scanimage

PDF Quirk uses the command line utility `scanimage` to produce images from the scanner. It comes with the SANE packages which are standard for scanners under linux.

To scan with PDF Quirk, an optimal `scanimage` command for the scanner device must be found and put into the configuration. Since all the scanner devices are so different and offer different scan options, it does not make too much sense to set a default here.

To get a reasonable result for the PDF, the scan should

1. have a resolution of 150 or 200 dpi.
2. be scanned in mode Grayscale for monochrome of Color.
3. not have a too big color depth

Also be sure to configure the right scan size. PDF Quirk assumes that a whole page is scanned.

To learn more about the SANE project and the scanimage tool, refer to the [scanimage manpage](http://www.sane-project.org/man/scanimage.1.html) for details.

If you have a better way of producing images, it is also possible to make PDF Quirk use that.

`scanimage` by default sends the scanned image data to standard out. PDF Quirk is prepared to that and reads it from there.

A typical scanimage command line might look like
```
scanimage --mode '24bit Color[Fast]' --resolution 150 -l 0 -t 0 -x 210 -y 297 --format png
```

If another tool should be used to create PDF that writes its output directly to a file rather than to stdout, the commandline may contain the placeholder `%OUTFILE`. If that is in the command line string, PDF Quirk will replace that by a filename the tool can write to (From version 0.91 on).

**Attention**: To quote command line parameters which contain spaces, use*single quotes*. Do not use double quotes, as PDF Quirks parser can not properly deal with that.

### PDF Options

Since version 0.95 PDF Quirk supports some basic PDF options. On the configuration page, user can set the page size, the page orientation and the page margin.

![PDF Options](https://github.com/dragotin/pdfquirk/raw/master/resources/screenshot_configoptions.png)

The settings are adjusted for all subsequent PDF creations.

## Contributions

Please report wishes and bugs in the [Issue Tracker](https://github.com/dragotin/pdfquirk/issues).

Pull requests that change code are very welcome!


# PDF Quirk

PDF Quirk is a utility to create PDFs from images easily and fast. The images can either be loaded from storage or directly be scanned.

It is just a little office helper tool to generate PDFs easily to share them online.

![Screenshot](https://github.com/dragotin/pdfquirk/raw/master/resources/screenshot1.png)

PDF Quirk uses the very well functioning tools `convert` from [ImageMagick](https://imagemagick.org/index.php) and `scanimage` from the [SANE project](http://www.sane-project.org/) instead of reinventing the wheel.

## Downloads and Releases

### Releases

The first public release of PDF Quirk has the version number 0.9 and is available from the [Github Release Page](https://github.com/dragotin/pdfquirk/releases/tag/v0.9). 

### Packages

Not many distros are packaging it PDF Quirk yet - but packages for openSUSE are available from my [openSUSE Buildservice Page](https://software.opensuse.org/package/pdfquirk).

As soon as PDF Quirk improves, it will make it's way into the repositories of distributions.

### Building from Source

Currently, the PDF Quirk source code can be cloned on the [Github page](https://github.com/dragotin/pdfquirk). 

## Configuration

To scan with PDF Quirk, an optimal `scanimage` command for the scanner device must be configured. Since all the scanner devices are so different and offer different scanner options, it does not make too much sense to use a default here.

To learn more about the SANE project and the scanimage tool, refer to the [scanimage manpage](http://www.sane-project.org/man/scanimage.1.html) for details.

## Contributions

Please report wishes and bugs in the [Issue Tracker](https://github.com/dragotin/pdfquirk/issues).

Pull requests that change code are very welcome!




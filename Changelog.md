# PDF Quirk Changelog

## PDF Quirk Version 0.95

Released in December 2021

- FEATURE: Add support for deskewing by utilizing the tool
  deskew from https://galfar.vevb.net/wp/projects/deskew/
- FEATURE: If the deskew tool is not available, use converts deskew.
- FEATURE: Support for Translations. Add German translation.
- FEATURE: Cleanup GUI a bit.
- FEATURE: Add support for basic PDF Options (Paper size, margin and orientation)
- FEATURE: Use built in, Qt based PDF converter to reduce dependencies.
- BUILD: Support Qt6 and Qt5
- FIX: Avoid crash when terminating
- FIX: Do not use QRegExp bc of version deps
- FIX: rework the handling of temporary image files
- FIX: Handle busy cursor properly
- FIX: Improve error handling with external tools


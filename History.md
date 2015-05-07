# Version History #

## 1.2 - 8/9/2006 ##
  * Updated to new del.icio.us API address. This seems to have resolved the bug where MySQLicious would randomly delete all bookmarks or inappropriatlely mirror all bookmarks when a tag was specified.
  * Added logXml option to help with future troubleshooting.

## 1.1.1 - 12/6/2005 ##
  * Fixed $this->$newline bug -- Thanks, Richard!.
  * Clarified licensing (MySQLicious is BSD licensed) -- Thanks, Walter!.

## 1.1 - 4/2/2005 ##
  * Fixed an issue with URLs that have single quotes in them.
  * Added the setOutputMode() function to change between command line, html, and silent modes.
  * Dramatically improved error handling and reporting.
  * Various internal improvements.

## 1.0.1 - 3/23/2005 ##
  * Replaced example.php with mirror.php, which is a fully working implementation of MySQLicious.

## 1.0a - 3/21/2005 ##
  * Fix semicolon bug in example.php Thanks, Roger!

## 1.0 - 3/20/2005 ##
  * Initial release.
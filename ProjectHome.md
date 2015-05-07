## About ##
MySQLicious provides automated mirroring/backups of [Delicious](http://del.icio.us) bookmarks into a MySQL database.

Note that MySQLicious does not provide a mechanism for displaying bookmarks after they're in your database; that part is up to you.

## Requirements ##
  * PHP 4 with cURL support
  * MySQL
  * Access to cron (or [pseudo-cron](http://www.bitfolge.de/pseudocron-en.html)).
  * A [Delicious](http://del.icio.us) account and some bookmarks.

## Usage ##
MySQLicious is designed to be run as a cron job. See the [tutorial](Tutorial.md) for more information. Here's a quick example of how MySQLicious is used:
```
<?php
require "MySQLicious.php";
$delicious = new MySQLicious("localhost", "MySQLdb", "MySQLuser", "MySQLpass");
$delicious->mirror("deliciousUser", "deliciousPass", "MySQLtable", "deliciousTag");
?>
```

## Warning ##
Do not run MySQLicious on every page load or you'll get banned from the del.icio.us server. See the tutorial for information on proper setup.
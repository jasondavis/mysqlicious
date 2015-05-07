# Advanced Documentation #

## See Also ##
There is a [tutorial](Tutorial.md) on setting my MySQLicious from scratch and a [FAQ](FaqTroubleshooting.md).

## Basics ##
### Initializing a MySQLicious Session ###
`$delicious = new MySQLicious(string $MySQL_host, string $MySQL_database, string $MySQL_username, string $MySQL_password);`
### Perform the Actual Mirroring ###
`$delicious->mirror(string $Delicious_username, string $Delicious_password, string $MySQL_table [, string $Delicious_tag]);`

  * When you use MySQLicious for the first time, a **MySQLicious** table will be created in the database you've specified. This will be used to store update times for the tag(s) you're mirroring.
  * `$MySQL_table` is the table into which the Delicious bookmarks will be placed. If the table doesn't exist, it will be created.
  * `%Delicious_tag` is the optional tag by which to filter. If it is not specified, all bookmarks will be mirrored.

## Advanced Configuration ##
After initializing a session (before mirroring), there are a few options that can be set.

**`$delicious->setOutputMode(<mode>);`**

Alter the output MySQLicious produces. 

&lt;mode&gt;

 can be one of the following:
  * `MYSQLICIOUS_OUTPUT_HTML` = HTML mode - use <br /> for line breaks.
  * `MYSQLICIOUS_OUTPUT_CMD` = Command line mode - Use \n (newline) for line breaks.
  * `MYSQLICIOUS_OUTPUT_NONE` = Silent - No output at all. Note that this even surpresses errors, so use with caution!

**`$delicious->logXml `=` <true/false>;`**

Turn on XML logging. This can be used to ensure that MySQLicious is actually making the changes it should be making.

**`$delicious->forceUpdate = true;`**

This will cause an update to happen regardless of whether del.icio.us has been updated recently. This is only recommended as a debugging measure. If you use it regularly enough, you may get banned from the Delicious servers.

**`$delicious->setAPIAddress("http://del.icio.us/apiLoc");`**

If the address of the del.icio.us API changes and I don't get a new version out quickly, this is an easy way to set point MySQLicious to the right location without having to mess with the code.

**`$delicious->MySQLiciousDataTable = "PlaceToStoreThings";`**

If you don't want MySQLicious to store its update data in the MySQLicious table, change that value here.
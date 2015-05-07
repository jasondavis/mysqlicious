# Tutorial #

## 1. Getting Started ##
This tutorial assumes a basic knowledge of PHP, MySQL, and cron (or [pseudo-cron](http://www.bitfolge.de/pseudocron-en.html)).

  1. Unzip the MySQLicious.zip file.
  1. Open mirror.php in a text editor and configure the settings (top half of the file). Do not remove the #!/usr/bin/php -q line at the beginning.
  1. Upload MySQLicious.php and mirror.php to your server.
  1. chmod the mirror.php file to be executable. This can be usually accomplished by using your FTP client -- look around for either a chmod command or in the Get Info or Properties window. Once you've found the chmod function, set it to 755 (or check all boxes for executable).

## 2. Testing ##
In your browser, open http://www.yourhost.com/path/to/mirror.php.

Ignore the `#!/usr/bin/php -q` line you'll see at the top and make sure you're not getting any error messages after that line. This will also perform the first mirroring, so if everything is set up right, you'll get a bunch of `Inserted...` lines.

If all looks well, proceed to the next step. If not, see the [FAQ/Troubleshooting](FaqTroubleshooting.md) page.

## 3. Setting Up Cron ##
The method of configuring cron jobs varies greatly from host to host. Many times there is a graphical way to set it up from the control panel, but not always. If you don't have it in your control panel but you do have SSH access, you can configure cron by typing `crontab -e`. I'm assuming you've figured out how to get to the cron configuration for your host.

If you don't have access to cron, fear not. You can use pseudo-cron instead!

Add the following line to your crontab:
`0 */2 * * * /path/to/mirror.php`
(replacing /path/to with the actual path to your mirror.php file). This will cause mirroring to happen every two hours.

### Warning ###
Do not run MySQLicious on every page load or you'll get banned from the Delicious server. You must use cron or pseudo-cron.

## 4. Getting Bookmarks Out ##
If you already know about getting data out of MySQL with php, you can probably stop reading. Still here? Ok, now that your bookmarks are stored in your MySQL database, how do you get them out? Just do a query and display them on the page. Here's some sample code to get you started:
```
// MySQL configuration
$MySQL_Host	= "localhost";	// address of your MySQL server
$MySQL_Database	= "db";		// name of the MySQL database you want to use
$MySQL_Table	= "delicious";	// name of the MySQL table your del.icio.us bookmarks are in
$MySQL_Username	= "username";	// MySQL username
$MySQL_Password	= "password";	// MySQL password
$bookmark_limit = 15;		// maximum number of bookmarks to display

// connect to MySQL server
$linkid = mysql_connect($MySQL_Host , $MySQL_Username, $MySQL_Password) or die("Could not connect to database server.");
$db_selected = mysql_select_db($MySQL_Database, $linkid) or die("Could not use database.");

// do query and display bookmarks
$sql = "SELECT * FROM `$MySQL_Table` ORDER BY date DESC LIMIT $bookmark_limit";
$result = mysql_query($sql, $linkid);
if ( $result and mysql_num_rows($result) > 0 ) {
	while ( $row = mysql_fetch_assoc($result) ) {
			echo "\t<p><a href=\"{$row['url']}\">";
			echo htmlentities($row['description']);
			echo "</a><br />";
			echo htmlentities($row['extended']);
			echo "</p>\n";
	}
}
```

## Advanced Usage ##
Other options and configuration settings for MySQLicious are described in the [documentation](Documentation.md).
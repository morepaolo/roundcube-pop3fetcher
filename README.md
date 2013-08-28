roundcube-pop3fetcher v1.5
==========================

Tested on RoundCube 8.4, 8.5, 9.0
Definitely not working in RoundCube 7.2 (due to the usage of rcmail::get_storage at line 104)

Pop3fetcher is a plugin for the popular Roundcube IMAP client, which allows Roundcube's users to add POP3 accounts and automatically fetch emails from them

Do you like this plugin, and wanna contribute to the development?
Follow this link, and offer me a coffee with Paypal!

https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=morepaolo%40gmail%2ecom&lc=IT&item_name=Roundcube%2dPop3fetcher&currency_code=EUR&bn=PP%2dDonationsBF%3abtn_donate_SM%2egif%3aNonHosted

HOW TO INSTALL:
===============

In order to install the plugin, just copy the folder named "pop3fetcher" in Roundcube's plugins folder.

mysql:

Then, you'll have to add the table to the database (Mysql version is provided in the SQL folder). Open the SQL/mysql.sql file, replace #REPLACE_WITH_YOUR_DB_NAME# 
with the correct name (e.g. if your roundcube's database name is "roundcubemail", the query should look like:

DROP TABLE IF EXISTS `roundcubemail`.`pop3fetcher_accounts`;
CREATE TABLE  `roundcubemail`.`pop3fetcher_accounts` (
  `pop3fetcher_id` int(10) unsigned NOT N...
  
And run the script. (Thanks to Achim Bleichner for this suggestion)

sqlite:

sqlite3 -init - sqlite.db < SQL/sqlite.sql↲


Finally, edit the main.inc.php file in the config folder, adding the plugin "pop3fetcher" at around line 378 (PLUGINS)

Now, login into RoundCube, go to the settings panel and add the POP3 accounts as you prefer 

CHANGELOG:
==========

1.6
Fixed German Translation (de_DE), thanks to glasklar, and added nl_NL (thanks to John Droppert)

1.5
Added zh_TW localization. Thanks to Anhsiou Tsai for the collaboration!
Fixed a bug notified by a user, in the settings panel the user interface button was hidden by the plugin

1.4
Added ru_RU localization. Thanks to Alexej Ruseckij for the collaboration!

1.3
Added auto-check-for-updates capability. Pop3fetcher will check on github if a new version of the software is available, suggesting you to install it.
This functionality can be disabled modifying pop3fetcher.php at line 29 ($config['automatically_check_for_updates'] = false)

1.2
Fixed a bug which didn't allowed to choose the default folder of POP3 account upon creation of the same (the folder was selectable only after the account saved and edited)
General refactoring of the debug code, adding a config['debug'] parameter to globally control the debug of the application. Remember to set it to false in production environment, because the POP3 logs can grow really fast!

1.1
Added capability of selecting target IMAP folder, to separate emails fetched from POP3 accounts and other emails separated



If you have any problem, please don't esitate contacting me at morepaolo@gmail.com. In order for me to organize emails, please write [roundcube-pop3fetcher] in the subject of the messages.

Thank you!!

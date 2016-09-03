roundcube-pop3fetcher v1.9
==========================

Manually Tested on RoundCube 8.2, 8.4, 8.5, 9.0, 9.1, 9.2, 9.3, 9.4
Definitely not working in RoundCube 7.2 (due to the usage of rcmail::get_storage at line 119)

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

GMAIL ISSUE:
===============
When enabling Gmail's POP3 capability, you may observe a strange behaviour, due to the fact that Gmail's POP3 is a bulk export feature, which is not thought to enable synch.
In fact, when you enable POP3, Gmail starts a queue which allows to export bundle of messages. This means that, until a bundle is exported, its last message uidl will be the most recent uidl available, even if new messages arrive.
But that uidl will be saved as last uidl (meaning "start from here") in pop3fetcher, so pop3fetcher will never find newer messages.

The trick is to allow to import also older messages with POP3fetcher, this way Gmail's queue will be emptied correctly. The threat is that you'll have to manually delete useless old emails imported from Gmail.


CHANGELOG:
==========
1.9.1
Removed deprecated functions to make pop3fetcher works on Roundcube 1.2+.  Added several additional languages.

1.9
Fixed auto-check of newly received messages not working since Roundcube 9.X, due to a change in asynchronous action name (from "check-recent" to "refresh")

1.8
Added fr_FR for french language, thanks to Matthias Dupont

1.7
Added cs_CZ for czech language, thanks to Daniel Bilik

Added option to import old messages when connecting a new account!!! (FAF, Frequently Asked Feature). Note that it's not possible to import messages for an already saved account, so if you want to import messages you'll have to delete the account and re-add it.

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

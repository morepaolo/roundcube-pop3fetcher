roundcube-pop3fetcher v1.1
==========================

Tested on RoundCube 8.4, 8.5, 9.0
Definitely not working in RoundCube 7.2 (due to the usage of rcmail::get_storage at line 104)

Pop3fetcher is a plugin for the popular Roundcube IMAP client, which allows Roundcube's users to add POP3 accounts and automatically fetch emails from them

HOW TO INSTALL:

In order to install the plugin, just copy the folder named "pop3fetcher" in Roundcube's plugins folder.

Then, you'll have to add the table to the database (Mysql version is provided in the SQL folder).

Finally, edit the main.inc.php file in the config folder, adding the plugin "pop3fetcher" at around line 378 (PLUGINS)

Now, login into RoundCube, go to the settings panel and add the POP3 accounts as you prefer 

CHANGELOG:

1.1

Added capability of selecting target IMAP folder, to separate emails fetched from POP3 accounts and other emails separated



If you have any problem, please don't esitate contacting me at morepaolo@gmail.com. In order for me to organize emails, please write [roundcube-pop3fetcher] in the subject of the messages.

Thank you!!
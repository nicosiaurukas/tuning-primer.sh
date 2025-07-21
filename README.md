# MySQL Tuning-Primer.sh
## How to use
Download and run <a href="https://raw.githubusercontent.com/BMDan/tuning-primer.sh/master/tuning-primer.sh">tuning-primer.sh</a>.

If you _don't_ like downloading anything and you _do_ like living dangerously, you could instead run it with something like this&sup1;:

```bash
curl -L https://raw.githubusercontent.com/BMDan/tuning-primer.sh/master/tuning-primer.sh | bash
```

## About this repository

This is the script originally developed by Matthew Montgomery, and previously hosted at Day32.com.  This version has been updated and improved for newer versions of MySQL, Percona Server, and MariaDB.  This Github repository was created with Matthew's permission by Dan Reif, but Matthew has no control over it; in other words, please don't bother Matthew with questions about this repository!

This repository will be used to handle ongoing development and bugfixes for this script.  Please file bug reports <a href="https://github.com/BMDan/tuning-primer.sh/issues">here</a>.  Pull requests are welcomed.

## About this script
This script takes information from `SHOW STATUS LIKE...` and `SHOW VARIABLES LIKE...` to produce sane recomendations for tuning server variables. 

It (attempts to be!) compatible with all versions of MySQL 3.23 and higher (including 5.x), as well as MariaDB, and Percona Server for MySQL.&sup2;

Currently it handles recomendations for the following:

* Slow Query Log
* Max Connections
* Worker Threads
* Key Buffer [MyISAM only]
* Sort Buffer
* Joins
* Temp Tables
* Table (Open & Definition) Cache
* Table Locking
* Table Scans (`read_buffer`) [MyISAM only]
* InnoDB Status

### Recent Changes

*Query Cache Checks: These are now automatically skipped in MySQL 8.0+ and an informative message is displayed.
*Deprecated Variables: These are ignored or zeroed (innodb_additional_mem_pool_size, table_cache, etc.) if the version is 8.0+.
*Conditional Checks: Functions have been added to detect MySQL 8.0+ or MariaDB, and the checks are adapted accordingly.
*Friendly Messages: If a variable no longer exists, a clear warning is displayed instead of failing.

---
### Legal Stuff

Use of this software is governed by its LICENSE, regardless of how it is accessed or by whom it is used.  Follow the license, dammit.

Some of the terms used in this script or in the documentation surrounding it may be copyrighted, trademarked, or otherwise owned by external entities including but not limited to Oracle, Percona, MariaDB Corporation Ab, and others.  These terms are used solely for identification of products, and the interoperability of this script with these or any other products, even if explicitly claimed, is nonetheless not guaranteed by any author.  No affiliation with or licensing from these entities is stated nor implied.  <a href="https://en.wikipedia.org/wiki/Whad%27Ya_Know%3F#Disclaimers">Anyone who says otherwise is itchin' for a fight.</a>

---
### Footnotes
&sup1;: Running it without downloading it and reading it first is a truly awful choice, and I arguably shouldn't put this command here.  Then again, if you are the sort of person who even _wonders how_ to run a script with _root access to your database_ by piping it into Bash, you're probably the sort of person I can't convince not to do so.  At least these instructions are ever-so-slightly safer than what'll appear on some Stack Overflow if I didn't put this here.

&sup2;: ... and anything else sufficiently MySQLish to export the status variables it uses to run.

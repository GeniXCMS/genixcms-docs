# DB Class

```
@filename: Db.class.php
@location: inc/lib/
@package: GeniXCMS
@since: 0.0.1
@author: Puguh Wijayanto (www.metalgenix.com)
@copyright: 2014-2015 Puguh Wijayanto
@license: MIT License
```

> This Documentation is still need improvement.


This class is for managing and for processing the database. Weare using MySQL database. Right now there are two database driver used, `mysql` and `mysqli`. And will be added in the next release for **PDO** driver.


## Constructor

Database connection is executed on the constructor. All database settings are defined at the config.php file located at `inc/config/`. 


## Connect Method

This method was used to connect into database. Currently the connection type is just `mysqli`. Will be added more soon. 

To use the method is simple. When you create an independent file and need a database connection just execute it before run the query. 

```
Db::connect();
```

When the configurations are not set, it takes fron the config.php file. But when you want to connect into the different database, just run this.

```
Db::connect($host,$user,$pass,$dbname);
```

## Query Method

This method is used to query the database. To call e query is simple. See te sample below. 

```

```




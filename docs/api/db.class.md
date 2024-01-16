# DB Class

```php
# filename: Db.class.php
# location: inc/lib/
# package: GeniXCMS
# since: 0.0.1
# author: Puguh Wijayanto (metalgenix.id)
# copyright: 2014-2024 Puguh Wijayanto
# license: MIT License
```

!!! info
    This Documentation is still need improvement.


This class is for managing and for processing the database. We are using MySQL database. Right now there are two database driver used `mysqli`. And will be added in the next release for **PDO** driver.


## Constructor

Database connection executed on the constructor. All database settings are defined at the **config.php** file located at `#!php inc/config/`. 

Constructor will connect database with configuration inside config.php on every load. The database configuration was defined during installation and saved on config.php file. 

## Connect Method

Usage: `#!php Db::connect();` 

Result: `#!php boolean`

This method was used to connect into database. Currently the connection type is just `#!php mysqli`. Will be added more soon. 

To use the method is simple. When you create an independent file and need a database connection just execute it before run the query. 

```php
Db::connect();
```

When the configurations are not set, it takes from the **config.php** file. But when you want to connect into the different database, just run this.

```php
Db::connect($host,$user,$pass,$dbname);
```

## Query Method

Usage: `#!php Db::query(string $var);`

Result: `#!php array`

This method is used to query the database. To call e query is simple. See the sample below. 

```php
Db::query("SELECT * FROM `table_name` WHERE 1 LIMIT 1");
```

Right now the query is still a simple query. In the future this had to be advanced query for better query.

## Result Method

Usage: `#!php Db::result(array $arr);`

Result: `#!php object`

This method used to get a list of data from table in an object structure. To use it see code below.

```php
$data = Db::result("SELECT * FROM `cat` ORDER BY `id` LIMIT 10");
```

This query will result :

```php
Array
(
    [0] => stdClass Object
        (
            [id] => 1
            [name] => News
            [slug] => news
            [parent] => 0
            [desc] => 
            [type] => post
        )

    [1] => stdClass Object
        (
            [id] => 2
            [name] => Info
            [slug] => info
            [parent] => 0
            [desc] => 
            [type] => post
        )
);
```

## Delete Method

Usage: `#!php Db::delete(int $id);`

Result: `#!php bool`

This method used to delete a row of data at the table by specified where clause. See sample below :

```php
$id = Typo::int($_GET['id']);
$vars = array(
          'table' => 'table', // table name
          'where' => array(
                         'id' => $id
                     ), // where
      );
$del = Db::delete($vars);
```

The code above will delete data in a row which had the `#!php $id` value.

See also: 

 - [Typo::int()](typo.class.md)

## Update Method

Usage: `#!php Db::update(array $var);`

This method will update the specified row in a table by specific `#!php $id`.

See sample below :

### Array Mode

This code used to insert data into database in array format.

```php
$vars = array(
          'table' => 'table', // table name
          'id' => $_POST['id'],
          'key' => array(
                         'name' => $_POST['name'],
                         'sex' => $_POST['sex']
                     ), // where
      );
$update = Db::update($var);

```

### Plain Mode

This code used to insert data into database in plain format.

```sql
$update = Db::update("UPDATE `table_name` SET `name`='{$_POST['name]}' WHERE `id` = '".$_POST['id']."')");
```

## Insert Method

Usage: `#!php Db::insert(array $var);`

This method will insert data into the table on the database. See sample below :
### Array Mode

This code used to insert data into database in array format.

```php
$vars = array(
          'table' => 'table', // table name
          'key' => array(
                         'name' => $_POST['name']
                         'sex' => $_POST['sex']
                     ), // where
      );
$del = Db::insert($var);
```

### Plain Mode

This code used to insert data into database in plain format.

```sql
$del = Db::insert("INSERT INTO `table_name` VALUES (null, '{$_POST['name]}')");
```


## Escape Method

Usage: `#!php Db::escape(string $string);`


This method used to escape string before submitted to database. We use MySQLi escape function to escape the characters.


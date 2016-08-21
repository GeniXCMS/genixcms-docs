# Install Class

```php
@filename: Install.class.php
@location: inc/lib/
@package: GeniXCMS
@since: 0.0.1
@author: Puguh Wijayanto (www.metalgenix.com)
@copyright: 2014-2016 Puguh Wijayanto
@license: MIT License
```

> This Documentation is still need improvement.

The Install Class used to install the script. It contains some method. 

## Make Config Method

Usage : `Install::makeConfig($file);`

Return: `string`

This method will create a config file inside `inc/config/` during the installation proccess. Data taken from session. 


## Create Table Method

Usage: `Install::createTable();`

Return: `boolean`

This will create the database table during the installation. 



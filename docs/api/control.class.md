# Control Class

```php
# filename: Control.class.php
# location: inc/lib/
# package: GeniXCMS
# since: 0.0.1
# author: Puguh Wijayanto (metalgenix.id)
# copyright: 2014-2024 Puguh Wijayanto
# license: MIT License
```

!!! info
    This Documentation is still need improvement.

This class is to load the controller at `#!php inc/lib/Control` directories. Controllers needed to proccess the procedure and view the result at themes. 

This is the hierarchy of MVC, as GeniXCMS is using MVC structure. 

The controller divided into some parts.

- Ajax
- Frontend
- Backend
- Error
- Install

This controller is flexible. You can create and add it at the **Control Class** to load it. 

## Handler Method

!!! warning
    This method is deprecated and will be removed on future updates

Usage: `#!php Control::handler((string) $vars)`

This method is to load the controller types.

Example: 

We want to call the **Frontend Controller**, so use this to load it. 

`#!php Control::handler('frontend');`

This will load the Frontend Controller.

## Frontend File Inclusion Method

Usage: `#!php Control::incFront((string) $vars);`

This method will load the file at the Frontend directory if the file is exist. If not it will load the **404** not found page. 

This method is needed by `#!php Control::frontend()` method. 



## Backend File Inclusion Method

Usage: `#!php Control::incBack((string) $vars);`

This method will load the file at the Backend directory if the file is exist. If not it will load the **404** not found page. 

This method is needed by `#!php Control::backend()` method. 

## Get Method 

Usage: `#!php Control::get(array $arr);`

This method used to get the http get request from URL. This work inside the Frontend method. On every get request, if the value is on the array the file will be include. This method is only run when the `#!php SMART_URL` is set as `#!php false`.

## Route Method

Usage: `#!php Control::route(array $arr);`

This method used when the `#!php SMART_URL` was set as `#!php true` and it will read the request uri at the url. On every value is match at the `#!php $arr` the file will be included.


## Frontend Method

Usage: `#!php Control::frontend();`

This will handle the controller which file will be included at the Frontend controller.

This method will call the file using `#!php self::incFront((string) $vars)`

If the controller is not found, the **404** error will loaded.

And Default controller is `#!php default.control.php`


### How to load your own controller

This is simple. If you want to create your own controller and want to load it at the frontpage. Just create your controller at the **Frontend Controller** : `#!php inc/lib/Control/Frontend` directory. 

After the file is ready, open the `#!php Control.class.php` file, and go to the `#!php public static method frontend()` method. 

There are some variables in arrays as the value; 

`#!php $arr = array ('post','page', 'cat', 'mod', 'sitemap', 'rss');`

Just add your controller name on it. If your file name is `#!php store.control.php`. So the arrays become like this :

`#!php $arr = array ('post','page', 'cat', 'mod', 'sitemap', 'rss', 'store');`


## Backend Method

Usage: `#!php Control::backend();`

This will handle the controller which file will be included at the Backend controller.

This method will call the file using `#!php self::incBack((string) $vars)`

If the controller is not found, the 404 error will loaded.

And Default controller is `default.control.php`



## ERROR Method

Usage: `#!php Control::error((string) $vars='',(string) $val'');`


This method is to load the Error handler. The default is 404 not found. 

There are some error page already built. Specially for the system error, eg: `404`, `400`, `403`, `500`

Those error page had specific header so when it loaded it will read by the system as it.

Anothere error pages are : 

- Database Error `#!php db`
- Unknown Error `#!php unknown`
- No Access error `#!php  noaccess`

### How to use Error Handler

Using error handle is simple. Below are some examples how to use it.

#### 404 Not Found Page
```php
$file = "/path/to/file.php";
if ( file_exists($file) ) {
    include($file);
}else{
    Control::error('404');
}
```


#### No Access / Restricted Access

```php
if(User::access(2)){
   echo "You are ready to go.";
}else{
   Control::error('noaccess');
}
```


#### Database Error 

```php
$mysqli = new mysqli($dbhost, $dbuser, $dbpass, $dbname);
$sql = 'SELECT * FROM `table` WHERE `id` = '{$id}'';
$db = $mysqli->query($sql);
if(!$db){
   Control::error('db', $mysqli->error);
}
```



### Creating Your own Error Page

If yo want to use your error handler, just create a file at Error directory inside the Control directory.

And load it when there is an error with your desired error pages.


## Ajax Method

This method used when we call the ajax request. All ajax file located at `#!php inc/lib/Control/Ajax`. 




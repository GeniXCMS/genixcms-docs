# Date Class

```php
@filename: Date.class.php
@location: inc/lib/
@package: GeniXCMS
@since: 0.0.3
@author: Puguh Wijayanto (www.metalgenix.com)
@copyright: 2014-2016 Puguh Wijayanto
@license: MIT License
```

This Class is used to format and manage the date and timezone. 

## Format Method 

Usage: `Date::format(string $date, string $format);`

Return `string`

This method will format the date for specific format. As default it will format as `j F Y H:i A T`, date format according to [PHP.NET Date Manual](http://php.net/manual/en/function.date.php). Please read it if you want to change the date format. 


## Local Method 

Usage: `Date::local(string $date, string $format);`

Return `string`


This method will result as Local Date format according to the local timezone. The timezone is set at the backend dashboard.


## Timezone Method

Usage: `Date::TimeZone();`

Return `array`


This method will result the list of Timezone in array.


## optTimeZone Method

Usage: `Date::optTimeZone();`

return `string`

This method will result a list of timezone in an options markup. 


## Country Options Dropdown

Usage: `Date::optCountry(string $val);`

return `string`

This method will result a list of Country in a dropdown options. If the value of the variable was set, the country which same with the variable will be selected.


## Country List Method

Usage: `Date::countryList();`

Return `string`

This method will result the list of country in array.


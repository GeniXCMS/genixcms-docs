# Image Class

```php
@filename: Images.class.php
@location: inc/lib/
@package: GeniXCMS
@since: 0.0.1
@author: Puguh Wijayanto (www.metalgenix.com)
@copyright: 2014-2016 Puguh Wijayanto
@license: MIT License
```

> This Documentation is still need improvement.

Image processor class. This Class used to process images.

## Resize Method

Usage: `Image::resize($src, $dst, $width, $height, $crop=0);`

Return: `boolean`

This method will resize image file and crop it in desired dimension. 

```php
$src = Source of the image
$dst = Destination of the resized image
$width = Desired width dimension
$height = Desired height dimension
$crop = Options to crop the image
```
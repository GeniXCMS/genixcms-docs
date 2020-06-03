# Image Class

```php
# filename: Images.class.php
# location: inc/lib/
# package: GeniXCMS
# since: 0.0.1
# author: Puguh Wijayanto (www.metalgenix.com)
# copyright: 2014-2019 Puguh Wijayanto
# license: MIT License
```

!!! info
    This Documentation is still need improvement.

Image processor class. This Class used to process images.

## Resize Method

Usage: `Image::resize($src, $dst, $width, $height, $crop=0);`

Return: `boolean`

This method will resize image file and crop it in desired dimension. 

```php
$src = "/path/to/image.jpg"; // Source of the image
$dst = "/path/to/resized.jpg"; // Destination of the resized image
$width = "470px"; // Desired width dimension
$height = "290px"; // Desired height dimension
$crop = "1"; // Options to crop the image

Image::resize($src, $dst, $width, $height, $crop);
```

That will resize image `/path/to/image.jpg` into `/path/to/resized.jpg` with width of **470px** and height **290px** and cropped.


## Compress Method

Usage: `Image::compress_png($path, $max_quality);`

Return: `boolean`

This method will compress selected `png` type image. This method need image processor called **pngquant** it's free and opensource image processor. You can download and install it manually. Download it from [https://pngquant.org](https://pngquant.org)

Ubuntu/Debian Server : `apt-get install pngquant`



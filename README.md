# wp-developer

## Problem

Developing for WordPress is a complex task. You need to take care of many common problems in lots of different areas. Although there are many ready-made solutions and approaches to most of them, they're scattered across the internet.  

## This solution

This is (becoming) a curated list of such snippets, techniques & tools that can make WordPress development faster, more manageable & convenient task.

## `functions.php`

### Self-versioning styles and scripts

PHP has a function - [filemtime](https://secure.php.net/manual/en/function.filemtime.php) - that can be very handy when dealing with browser cache busting. It gets file modification time and returns it as a Unix timestamp.

`int filemtime( string $filename )`

Example (in your theme's `functions.php`):

```php
$my_stylesheet_uri = get_template_directory_uri() . '/dist/style.min.css';

wp_enqueue_style( 
	'my-style',
	$my_stylesheet_uri, 
	array(), 
	filemtime( $my_stylesheet_uri ) 
);
```

outputs something like 

```html
<link rel='stylesheet' id='my-style-css' href='http://my-website.com/wp-content/themes/my-theme/style.min.css?ver=1512143428' type='text/css' media='all' />
```

Notice the `style.min.css?ver=1512143428` where `1512143428` is a Unix timestamp, which represents the last time you edited the file.

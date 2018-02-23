# wp-developer

[![license](https://img.shields.io/github/license/selrond/wp-developer.svg?style=flat-square)](https://choosealicense.com/licenses/mit/)

### The Problem

Developing for WordPress is a complex task. You need to take care of many common problems in lots of different areas. Although there are many ready-made solutions and approaches to most of them, they're scattered across the internet.  

### This solution

This is (becoming) a curated list of such snippets, techniques & tools that can make WordPress development faster, more manageable & convenient task.

---

## Useful general links

- [Code Reference](https://developer.wordpress.org/reference/)
- [WP-CLI Commands](https://developer.wordpress.org/cli/commands/)
- [[Handbook] - Theme Developer](https://developer.wordpress.org/themes/)
- [[Handbook] - Plugin Developer](https://developer.wordpress.org/plugins/)
- [[Handbook] - REST API](https://developer.wordpress.org/rest-api/)

## Sections

- [WP-CLI](wp-cli/README.md)

## `functions.php`

### Self-versioning styles and scripts

PHP function - [filemtime](https://secure.php.net/manual/en/function.filemtime.php) - comes in quite handy when dealing with browser cache busting. It gets file modification time and returns it as a Unix timestamp.

`int filemtime( string $filename )`

Example:

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
<link rel='stylesheet' id='my-style-css' href='http://my-website.com/wp-content/themes/my-theme/dist/style.min.css?ver=1512143428' type='text/css' media='all' />
```

Notice the `style.min.css?ver=1512143428` where `1512143428` is a Unix timestamp, which represents the last time you edited the file.

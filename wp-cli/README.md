# WP-CLI

> WP-CLI is the command-line interface for WordPress. You can update plugins, configure multisite installs and much more, without using a web browser.

- [Installation](http://wp-cli.org/#installing)


## Snippets

### Delete all comments from all sites in multisite

```sh
for url in $(wp site list --field=url); 
	do echo "Deleting all comments from $url"; 
	wp comment delete "$(wp comment list --field=ID --url="$url")" --url="$url" --force; 
done;
```
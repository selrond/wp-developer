# WP-CLI

> WP-CLI is the command-line interface for WordPress. You can update plugins, configure multisite installs and much more, without using a web browser.

- [Installation](http://wp-cli.org/#installing)


## Snippets

### Delete all comments from blog in multisite

```sh
wp comment list \
    --url="http://blog1.multisite.test" \
    --format=ids \
    | \
xargs wp comment delete \
    --url="http://blog1.multisite.test" \
    --force
```
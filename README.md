WP Migrate DB Pro Tweaks
========================

This is a WordPress plugin, meant as a starting point for developers to tweak WP Migrate DB Pro using WordPress filters.

Installation
------------

Create a /wp-migrate-db-pro-tweaks/ folder in /wp-content/plugins/ and simply drop the wp-migrate-db-pro-tweaks.php file into it. Then go to the Plugins page in your WordPress dashboard and activate it.

Setup
-----

Open the wp-migrate-db-pro-tweaks.php file and take a look at the `init()` function. You will notice that all the calls to `add_filter()` are commented out. So, at the moment the plugin does nothing even though it's activated. To enable a filter, simply uncomment the appropriate `add_filter()` line.

Usage
-----

Normally deploying between development, staging, and production wordpress sites will require you to go in and revert the read settings on a case by case basis.  For example, I don't want my staging site to be crawled so I turn read settings off on development before I deploy.  Later I deploy to production, only to forget to turn read settings back on.  This can negatively impact SEO in some instances, and cause all sorts of problems.  

##### This solves the issue by preventing read settings from being migrated in the first place.

Alternately, you can add something like this to your theme's functions.php file, or a utility plugin/mu-plugin on both sites:

```
add_filter('wpmdb_preserved_options', 'my_preserved_options' );
function my_preserved_options( $options ) {
  $options[] = 'blog_public';
  return $options;
}  
```

This also works, and in some cases may be easier.  

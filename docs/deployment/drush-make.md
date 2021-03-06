Drupal VM is configured to use Composer by default to build a Drupal site on the VM inside `/var/www/drupalvm/drupal/web` (in a folder that's synced to your local machine, so you can work with the Drupal codebase either locally or inside the VM).

If you want to build a Drupal site using a [Drush make file](http://www.drush.org/en/master/make/) instead, set `build_composer_project: false`, `build_makefile: true` and either use the `example.drupal.make.yml` file as a base, or use your own Drush make file: just place it or symlink it into the root of the Drupal VM folder with the filename `drupal.make.yml`. You can also set a separate path to the makefile using the `drush_makefile_path` variable.

```yaml
build_composer_project: false
build_makefile: true
```

Have a look at the defaults in `default.config.yml` and tweak the settings as you'd like in your `config.yml`, then run `vagrant up` as in the Quick Start Guide. Within a few minutes, you should have your site running and available at the `drupal_domain` configured in `config.yml`, falling back to the default `http://drupalvm.dev` set in `default.config.yml`.

With the default settings the Drupal site will be built on the VM inside `/var/www/drupalvm/drupal/web` but the `web/` subdirectory is only required for `composer` based projects and you can simplify this directory structure by setting `drupal_core_path` to `/var/www/drupalvm/drupal`.

```yaml
build_composer_project: false
build_makefile: true
drush_core_path: "/var/www/drupalvm/drupal"
```

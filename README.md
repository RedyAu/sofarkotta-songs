## Installing

- Start with a Drupal 11 site.
- Install whatever profile you like.
- Require the recipe with Composer so its module dependencies are installed too.

From the project root:

```shell
composer require boobaa/sofarkotta-songs
```

This recipe depends on these contrib modules:

- `field_group`
- `field_permissions`
- `multiselect_dropdown`

The recipe can then be applied with PHP in Drupal 11+.

### Standard docroot layout

If your Drupal web root is also the project root, run:

```shell
php core/scripts/drupal recipe recipes/contrib/sofarkotta-songs
```

### `drupal/recommended-project` layout

If your project uses the standard Composer layout with `web/` as the docroot, run this from the project root:

```shell
cd web
php core/scripts/drupal recipe ../recipes/contrib/sofarkotta-songs
```

### DDEV

If you are using DDEV with a `web/` docroot:

```shell
ddev exec -d /var/www/html/web php core/scripts/drupal recipe ../recipes/contrib/sofarkotta-songs
```

If you are using DDEV with a `docroot/` docroot:

```shell
ddev exec -d /var/www/html/docroot php core/scripts/drupal recipe recipes/contrib/sofarkotta-songs
```

If all goes well, you should see the following output:

```shell
 [OK] Sofarkotta Songs applied successfully
```

Clear the cache after the recipe is applied:

```shell
drush cr
```

When going back to the site, all the recipe configuration and customization has been applied.

You might want to place the `more_variations` ("További variációk") block in the content region,
below the content block, for the `song` node type pages.

Feel free to change/extend the allowed values for books ("Kottafüzet") by
visiting `/admin/structure/types/manage/song/fields/node.song.field_book`.

## Troubleshooting

If recipe application fails with one of these errors:

- `The "multiselect_dropdown" plugin does not exist`
- field storage config depending on `field_permissions`

then the recipe dependencies were not installed in the host project. Re-run:

```shell
composer require boobaa/sofarkotta-songs
```

and apply the recipe again from the correct Drupal web root.

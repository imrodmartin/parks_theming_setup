# Parks Theming Setup

The setup recipe for the Drupal 12 Layout and Theming course. Every trainee applies it in Exercise 1.2.1, whatever their starting point.

| | Starting fresh | Continuing from Site Building |
| --- | --- | --- |
| Content model (`parks_content_model`) | Added | Already there, skipped |
| Demo content (`parks_demo_content`) | Added | Already there, skipped |
| Parks Theme, its blocks and UI Patterns (`parks_theme_setup`) | Added, Parks Theme set as default | Already there. Parks Theme is set as default again. |
| Program list view at `/program-list` | Added | Added |

The Program list view (`parks_program_list`) lists every published Program in the Teaser view mode, sorted by title, with no pager. Learning Module 7 renders it through the card and card grid components. It lives at `/program-list` so it never collides with the Site Building course's *Find a Program* view at `/programs`.

## Applying

From the project root:

```
composer config repositories.parks_content_model '{"type": "vcs", "url": "https://github.com/imrodmartin/parks_content_model", "no-api": true}'
composer config repositories.parks_demo_content '{"type": "vcs", "url": "https://github.com/imrodmartin/parks_demo_content", "no-api": true}'
composer config repositories.parks_theme '{"type": "vcs", "url": "https://github.com/imrodmartin/parks_theme", "no-api": true}'
composer config repositories.parks_theme_setup '{"type": "vcs", "url": "https://github.com/imrodmartin/parks_theme_setup", "no-api": true}'
composer config repositories.parks_theming_setup '{"type": "vcs", "url": "https://github.com/imrodmartin/parks_theming_setup", "no-api": true}'
composer require imrodmartin/parks_theming_setup:^1.0
composer update imrodmartin/parks_theme
cd web && ../vendor/bin/dr cache:rebuild && ../vendor/bin/dr recipe:apply ../recipes/parks_theming_setup && ../vendor/bin/dr cache:rebuild && cd ..
```

`no-api` makes Composer download from GitHub directly instead of through GitHub's API, which allows only 60 anonymous requests an hour per network. A classroom on one connection runs out fast, and Composer then fails with a misleading "Permission denied (publickey)". `composer update imrodmartin/parks_theme` brings Site Building sites up to Parks Theme 1.1, which the theming course needs.

On DDEV, run `ddev ssh` first.

Recipes can't be un-applied. This one only adds what's missing, so it never changes a trainee's existing work.

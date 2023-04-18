## Adding CSS Snippets

The Custom CSS extension is for adding small snippets of CSS. Do not use this for building your entire theme - instead modify your themes CSS component stylesheets or use the custom.css file.

CSS selectors cannot use the `>` child selector in the Custom CSS field - it will convert to an entity because the field is sanitised using `Xss::filter()`.

This guidance is derived from my work to resolve this issue:
https://www.drupal.org/project/adaptivetheme/issues/3354762

Use of the tools provided at: 
/admin/appearance/settings/my_custom_theme 

will generate a file in the custom file at:
styles/css/generated/custom-css.css

To ensure that my custom styling work in the development environment survives promotion to uat environment, 
I took the following steps:

* ssh to my dev installation
* cd to custom theme
* used git status to inspect for changes
* migrated content from styles/css/generated/custom-css.css to styles/css/custom.css
* use git -m'commit message' styles/css/custom.css; git tag ; git push origin master --tags to push these changes to my remote repo
* ssh to my uat installation
* cd to custom theme
* git pull origin master --tags
* drush cr
* inspect results to find that my custom css is now being served


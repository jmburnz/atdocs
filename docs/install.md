# Theme Installation

Requirements:

* [https://www.drupal.org/project/adaptivetheme](https://www.drupal.org/project/adaptivetheme)
* [https://www.drupal.org/project/at_tools](https://www.drupal.org/project/at_tools)

### Adaptivetheme Base Theme
Download the latest version of Adaptivetheme for Drupal 8 and place in the `/themes/` directory.

Nothing will show visibly on the themes list page `~/admin/appearance`. This is normal, AT Core is a hidden theme that works in the background.

### AT Tools & AT Theme Generator Modules
Download the latest verions of AT Tools module for Drupal 8 and place in the `/modules/` directory. 

The AT Tools module includes the theme generator in a sub-module called AT Theme Generator. Enable both modules from the Extend page `~/admin/modules` in your Drupal site (or use Drush/Drupal console etc).

The next step is to [generate a new theme](theme-generator.md), or install an existing sub-theme, such as Pixture Reloaded, AT Magazine etc.



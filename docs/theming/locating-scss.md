## Determining which SCSS Files to Modify

The theme uses Source maps to map SCSS. Compliant browsers such as Chrome and Firefox can display SCSS map references in their inspectors. You may need to switch this on in the browser settings.


If you open any of the UIKit compiled SCSS files, e.g. base.css, at the bottom you’ll see a reference like this:


    /*# sourceMappingURL=base.css.map */


It is referring to the source map (you can see these in the same directory). Those source map files hold references to the original SCSS files.


When you inspect an element check the CSS file name, is it actually SCSS? If so that is the SCSS partial you likely need to edit.


If it’s a CSS file, then it’s highly likely to be one of the following: from Drupal core, a contrib  module or a generated CSS file from Adaptivetheme Extensions.

![Changing breakpoint group](../img/source-maps-basic_small.png)

### Further Reading

http://blog.teamtreehouse.com/introduction-source-maps

Google dev docs: 
https://developers.google.com/web/tools/chrome-devtools/javascript/source-maps?hl=en


Most of the info into those links refers to JS, but it applies in much the same way to CSS.
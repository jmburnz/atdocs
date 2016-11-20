## File Structure

Skin type themes are, in essense, a CSS file. They provide one library with one CSS file.

All you need is the most basic Drupal theme files, however it's what we include in the info.yml that is most important.

Lets examine the files of a typical skin theme:

    theme_name
      theme_name.info.yml
      theme_name.libraries.yml
      styles
       - theme.css
      logo.svg
      screenshot.png

### Important Files to Note
      
#### 1. theme_name.info.yml
 
Here we include the usual entries for info files. 

The most important keys to be ware of are: base theme, subtheme type, layout, regions and libraries.

<dl>
<dt>base theme: base_theme_name</dt>
<dd>You must declare the base theme - this is the theme you want your skin theme to inherit it's major styles, theme settings, and layout from. This must be an existing Adaptivetheme sub-theme with the subtheme type of `adaptive_subtheme`.</dd>

<dt>'base theme original': 8.x-1.0</dt>
<dd>This is the base theme version. Adaptivetheme uses this internally to track it's subthemes and maintain version integrity.</dd>

<dt>subtheme type: adaptive_skin</dt>
<dd>Skin themes must have this set as <code>adaptive_skin</code>. This triggers Adaptivetheme to treat this theme in a vastly different way, allowing it to inherit extension settings, layout, color settings etc.</dd>

<dt>layout: flex-builder</dt>
<dd>This must match the base themes layout library. Hopefully this will be deprecated and removed in future versions, for now though it is a requirement.</dd>

<dt>regions:</dt>
<dd>Drupal core does not allow subthemes to inherit regions, you must declare these - and they should ideally match your base themes regions.</dd>

<dt>libraries:</dt>
<dd>Load the skin themes library. You don't have to do this here, perhaps you will do this by attaching to a render array in a theme hook, however this is the easiest way to load the skin themes library globally.</dd>
</dl>

Lets see an overview of a typical skin themes info file:


    name: 'Theme Name'
    type: theme
    'base theme': base_theme_name
    'base theme original': git
    'subtheme type': adaptive_skin
    layout: flex-builder
    description: 'Skin type theme.'
    tags: sub-theme
    core: 8.x
    regions:
      leaderboard: Leaderboard
      header_first: 'Header first'
      header_second: 'Header second'
      navbar: Navbar
      highlighted: Highlighted
      features_first: 'Features first'
      features_second: 'Features second'
      features_third: 'Features third'
      content_prefix: 'Content prefix'
      content: 'Main content'
      sidebar_first: 'Sidebar first'
      sidebar_second: 'Sidebar second'
      content_suffix: 'Content suffix'
      subfeatures_first: 'Sub-features first'
      subfeatures_second: 'Sub-features second'
      subfeatures_third: 'Sub-features third'
      subfeatures_fourth: 'Sub-features fourth'
      footer: Footer
      page_top: 'Page top'
      page_bottom: 'Page bottom'
    features:
      - logo
      - favicon
      - node_user_picture
      - comment_user_picture
      - comment_user_verification
    libraries:
      - theme_name/skin
 
 
 
#### 2. theme_name.libraries.yml
 
Skin themes must have at least one library with one CSS file. You can call these whatever you like.

Note we set a very high weight for the CSS file - this ensures the CSS file will be the last to load, therefor make it easier to override previously declared CSS. Increase the weight should you need to (some module might also attempt this same trick).
 
    skin:
      version: 8.x-1.0
      css:
        theme:
          styles/css/theme_name.css: { weight: 1500 }
 
 
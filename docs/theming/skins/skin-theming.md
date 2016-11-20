##  Skin Themes

Skin themes are sub-sub themes. This means their base theme is an existing stylized theme. 

Skin themes are useful when you only want to make CSS style changes. A typical use case could be a particular section of the site needs extensive custom CSS.

### Typical Use Cases

- You create a "base theme" (a standard sub-theme) for a group of sites, then a skin theme for each site - in effect you're extending the base theme for each multi-site site.
- You have a global sub-theme for your site, but then want major CSS alterations for one or more particular sections. It may make sense to place these overrides in a skin theme.
- You don't want to edit the sub-theme, i.e. you're using a commercial sub-theme or perhaps running tests, in this case you can encapsulate changes in the skin without the risks associated with hacking the original theme.

Note that skin themes can be cloned. This allows you to create many versions of the same skin, which may be a useful workflow.

### Limitations and Features

Skin themes have limitations and features not found in standard sub-themes:

- There are no advanced settings for skin themes.
- Skins inherit all Extension and Layout settings from their base theme.
- Skins inherit templates, styles (all libraries), color module settings, preprocess and alters from their base theme(s).

### Theme Switching
If you are looking for a way to switch themes, here is a good article on how to build a simple module that can do this in Drupal 8: [Switch theme based on the page's active menu](http://annakalata.com/blog/drupal-8-how-switch-theme-based-pages-active-menu)


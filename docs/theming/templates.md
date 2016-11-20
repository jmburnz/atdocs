## Templates

### Template Overrides

Adaptivetheme provides many custom template overrides. These include 
modifications to support theme settings and advanced style and features
provided by the core theme.


### Generated Templates

In Adaptivetheme `page.html.twig` is generated - it is overwritten 
every time you save the Layout Theme Settings. The templates stored
here should be considered volatile and never manually edited unless
you switch off the themes Layout System and leave it off.

Customisations should be placed in `row.html.twig` and `row-[row-name]`
suggestions, or others such as html, region or block templates.

See `adaptivetheme/at_core/templates/layout/row.html.twig`

Do not change the directory structure for generated layouts - 
the layout generation system relies on the location of page.html.twig: 
`templates/generated/page.html.twig`


#### Suggestions

Generated page template suggestions are stored in this directory.

Each time you create a new page suggestion the theme automatically 
creates a new library and layout CSS file, which is stored in 
`styles/css/generated/`.

The library is attached via the suggestion template, e.g.:

    {{ attach_library('theme_name/theme_name.layout.page-[suggestion]') }}
    <div{{ attributes }}>
      {{ rows }}
    </div>

In effect the page suggestions are being used to load CSS rather than to 
provide custom markup.


#### Backups

A backup is always stored in your themes /backup/ directory. Backups are 
time stamped and never removed, so if you get a build up you can 
manually clear them out.


#### AT Core Templates
See `at_core/templates/README.md` for more information about AT Cores
templates.


#### Developing with Twig

Please see: https://www.drupal.org/node/1903374


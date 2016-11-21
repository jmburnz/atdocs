## Theming with Breakpoints

Adaptivetheme provides groups of media queries, defined in yml for the core Breakpoints module. AT uses these breakpoints in the Layout settings, Responsive menus, Mobile blocks settings and in the Layout Plugin layouts responsive CSS. 

Additionally these groups and associated breakpoints can be used anywhere in Drupal where Breakpoint module defined queries are supported, e.g. Responsive Image module.

You can find the breakpoint groups in:

`~/adaptivetheme/at_core/at_core.breakpoints.yml`

###  Using Breakpoints in JavaScript

Adaptivetheme will always add one or more breakpoint groups to drupalSettings. The "Simple" group is always included as it is used by the Layout Plugin layouts. 

If a different breakpoint group is used in the Layout settings they're also pushed into drupalSettings.

You can retrieve these from drupalSettings in JS, e.g.:

      var activeTheme = settings['ajaxPageState']['theme'];
      var breakPoints = settings[activeTheme]['at_breakpoints'];


### Breakpoint body classes

Layout settings breakpoints are applied to the body element as a class name. This provides an easy hook for styling or behaviour per layout breakpoint.

For example in narrow screens (e.g. mobile), you may see: `<body class="bp--at-core-simple-mobile">`.


### Enquire.js

Adaptivetheme includes a library that will load [enquire.js](http://wicky.nillia.ms/enquire.js/). Enquire.js is a lightweight, pure JavaScript library for responding to CSS media queries.

If Responsive Menus extension is enabled the Enquire.js plugin will load. The library is called `at.enquire`, so if you need to load it yourself, e.g. in `html.html.twig`:

    {{ attach_library('at_core/at.enquire') }}

Note that this library attaches jQuery and MatchMedia (Drupal core libs) as dependencies.

To use enquire with our drupalSettings you can grab each media query from the breakPoints variable we set above.

For example, at.breakpoints.js is the script adding our breakpoints as body classes, here we use enquire to respond to these queries and add and remove the classes:


      // Get breakpoints from drupalSettings, these are added during preprocess
      // and write the breakpoints used in layout settings, which are themselves
      // set in breakpoints module config, i.e. themeName.breakpoints.yml and are
      // the group selected to be used by the themes layout.
      var activeTheme = settings['ajaxPageState']['theme'];
      var bps = settings[activeTheme]['at_breakpoints'];

      function registerEnquire(breakpoint_label, breakpoint_query) {
        enquire.register(breakpoint_query, {
          match: function() {
            document.body.classList.add('bp--' + breakpoint_label);
          },
          unmatch: function() {
            document.body.classList.remove('bp--' + breakpoint_label);
          }
        });
      }

      for (var item in bps) {
        if (bps.hasOwnProperty(item)) {
          registerEnquire(item.split('_').join('-'), bps[item]['mediaquery']);
        }
      }


### Defining Breakpoints

First create a file `theme_name.breakpoints.yml`.

Declare one or more breakpoints. Here we can view the "Responsive menus" breakpoints from AT Core as an example:
 
    at_core.responsive_menus.mobile:
      label: Mobile
      mediaQuery: 'all and (max-width: 60em)'
      weight: 1
      multipliers:
        - 1x
      group: at_core.responsive_menus
    
    at_core.responsive_menus.max-width:
      label: Max-width
      mediaQuery: 'all and (max-width: 75em)'
      weight: 0
      multipliers:
        - 1x
      group: at_core.responsive_menus
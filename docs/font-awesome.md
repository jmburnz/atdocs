## Whats Included

Adaptivetheme sub-themes (rc2 and onwards) all have a full implimentaiton of Font awesome. This means all the icon class names, animations, flip, rotate, stack, size etc are included for use in content.

Adaptivetheme adds color classes so you can make icons match your themes font, link or border colors, and classes to make icons semi-transparent.

Refer to the [Font awesome cheatsheet](http://fontawesome.io/cheatsheet/) for details about classes names and available icons.


## Using Font Awesome in Content

Using Font awesome in content requires you to apply class names to an element, normally `<i></i>` which is placed somewhere in your content.

Use the zero-width non-joiner character `&zwnj;` as a placeholder in the `<i></i>` - this satisfies Drupals input formats and can be used in the CKEditor without issues.

You need to use at least two classes: `fa` and an icon class, for example:

`<a href="https://www.drupal.org/"><i class="fa fa-drupal">&zwnj;</i> Drupal.org</a>`

Outputs: <a href="https://www.drupal.org/"><i class="fa fa-drupal">&zwnj;</i> Drupal.org</a>

For in depth details on using Font awesome in content please see [Font awesome examples documentation](http://fontawesome.io/examples/).


Note: Adaptivetheme will automatically hide icons if Font awesome fails to load, i.e. this CSS is included in `styles/css/components/webfonts.css`:

````
.fa-loading .fa,
.fa-unavailable .fa {
  display: none;
}
````

## Using Font Awesome in Twig Templates

Use the same methods as used in content.


## Using Font Awesome in CSS/SCSS

For user interface elements you can apply icons using CSS or SCSS. Adaptivetheme does this for all standard icons included with Drupal core, as well some extras such as the breadcrumb separators.

Adaptivetheme uses [Fontfaceobserver](https://github.com/bramstein/fontfaceobserver), whch checks to see if Font awesome has loaded - this prevents displaying missing chars if Font awesome fails to load. 

The class `fa-loaded` is added to the html element when Font awesome has been detected.

`fa-unavailable` is added if Font awesome fails to load.

`fa-loading` is added while the script is waiting to detect success or failure.

We can use the breadcrumb separators as an example.

````
/* Place icon inline before the list item */
.breadcrumb__list-item:before {
  font-family: inherit;
  content: "\00BB"; /* Provide a fallback unicode char */
  display: inline-block;
  padding: 0;
  margin-right: 0.25rem;
  text-align: center;
}

/* FA has loaded, override the fallback char and font family */
.fa-loaded .breadcrumb__list-item:before {
  font-family: FontAwesome, sans-serif;
  content: "\f105"; /* Angle right */
}

/* Flip the icon for RTL languages */
[dir="rtl"] .breadcrumb__list-item:before {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=0, mirror=1)";
  -webkit-transform: scale(-1, 1);
  -ms-transform: scale(-1, 1);
  transform: scale(-1, 1);
}
````

This is expressed in the breadcrumbs SCSS (with non relevant code removed) as:

````
.breadcrumb {
  &__list-item {
    &:before {
      font-family: inherit;
      content: "\00BB";
      display: inline-block;
      padding: 0;
      @include output-rhythm(margin-#{$flow-to}, 4px);
      text-align: center;

      // RTL
      [dir="rtl"] & {
        @include fa-icon-flip(-1, 1, 0);
      }

      // FontAwesome loaded.
      .fa-loaded & {
        font-family: $icon-font;
        content: $breadcrumb-separator-icon;

        // RTL
        [dir="rtl"] & {
          @include fa-icon-flip(-1, 1, 0);
        }
      }
    }
  }
}
````

See: 
````
styles/uikit/partials/component/_breadcrumb.scss
styles/uikit/partials/_variables.scss
````


## Colors and Transparencies

Sub-themes include useful classes that match your themes colors, see `styles/css/components/color.css`.

For SCSS see:
````
styles/uikit/partials/theme/_color.scss
styles/uikit/partials/_variables.scss
````

````
/**
 * Web fonts
 ============================================================================ */
/* Override Font Awesome classes. */
.fa-border {
  border-color: #cccccc;
}

/*  Extra classes for Font Awesome. */
.fa-text-color {
  color: #363636;
}

.fa-text-color-light {
  color: #808080;
}

.fa-text-color-medium {
  color: #5c5c5c;
}

.fa-match-border {
  color: #cccccc;
}

.fa-match-border-light {
  color: #eeeeee;
}

.fa-match-link {
  color: #0066cc;
}

.fa-trans-white-25 {
  color: rgba(255, 255, 255, 0.25);
}

.fa-trans-white-50 {
  color: rgba(255, 255, 255, 0.5);
}

.fa-trans-white-75 {
  color: rgba(255, 255, 255, 0.75);
}

.fa-trans-black-25 {
  color: rgba(0, 0, 0, 0.25);
}

.fa-trans-black-50 {
  color: rgba(0, 0, 0, 0.5);
}

.fa-trans-black-75 {
  color: rgba(0, 0, 0, 0.75);
}
````

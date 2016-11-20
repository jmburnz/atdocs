## Adding CSS Snippets

The Custom CSS extension is for adding small snippets of CSS. Do not use this for building your entire theme - instead modify your themes CSS component stylesheets or use the custom.css file.

CSS selectors cannot use the `>` child selector in the Custom CSS field - it will convert to an entity because the field is sanitised using `Xss::filter()`.



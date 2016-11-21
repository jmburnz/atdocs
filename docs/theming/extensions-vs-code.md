## Extensions vs Manual coding

A common question asked is whether or not to use an Extension or write custom code. All the extensions can be replicated by a competant front end developer, however due consideration should be give to the following main points:

- Theming skills
- Client expectations and requirements
- Budget and schedule
- Does the setting do what you need/mostly what you need?
- Is the extension an acceptable compromise?

Some extensions are relatively easy to replicate in CSS, while others employ PHP, JS, CSS and Twig to achieve the outcome, for example the layout settings or Responsive Menus.

Does your client expect to be able to change things without you? Perhaps this is a feature you want to sell as part of your service, or that you want to be able to easily change things without firing up an editor and manually code something, for example changing a font.

The bottom line is - it really comes down to your use case and your technical skills. If you're able to write the code, or in some cases able to copy/paste code, then it may be that the extension is redundant. However even advanced themers will appreciate wiping hours off their development time simply by being able to use very complex extensions such as Responsive Menus, Layout, Shortcodes, and others.

Here we examine extensions and look at the pros and cons of each approach.



### Responsive menus
Responsive menus allows you to select a menu block and two styles - a default style and a responsive style. You can also set the breakpoint at which the menu changes. Additionally they're accessible (ARIA, not using display: none etc) and use relatively modern JS and CSS practices such as transitions as opposed to JS animation. 

More over they're well tested across device and browser. An example of this is the hover-tap capability of the drop down style for touch devices.

The biggest win of this extension is time. Any way you go about responsive menus in code they take time to implement and get right.

Pros: 

- Quick to implement, very time consuming to replicate every feature
- Neatly syncs with your breakpoints
- Robust accessibility
- Cross browser & device compatibility
- 8 styles to choose from

Cons:

- Limited to one menu only
- CSS is complex
- Has strong opinions about the style, e.g. click handles, colors, hovers etc.


**When to Code it?**

When you need many responsive menus, or when your design demands a style or placement of menu that can't be done with the extension. Alternatively you could use a module such as Superfish, which provides a drop menu with limited responsive styles.

To replicate all the features you need strong front end developer skills (especially responsive design) and a broad understanding of cross browser and device considerations.


### Image alignment and captions

Coding image field layout is easy for a front end developer to achieve with CSS, however the most interesting feature of this extension is the captioning capability. You will need to know Twig and potentially some PHP to properly set titles attribute as a caption in the field template.


### Touch icons
Add touch icon meta tags. A default set of icons are located in themes/juridisch/images/touch-icons/.


### Fonts
Apply fonts to site elements. Supports Google and Typekit fonts, as well as standard websafe fonts.


### Titles
Set case, weight, alignment and letter-spacing for titles (headings).


### Shortcode CSS Classes
Adjust and enhance theme styles with pre-styled CSS classes.


### Slideshows
Enable slideshows and configure settings.


### Mobile Blocks
Show or hide blocks in mobile devices.


### Custom CSS
Enter custom CSS rules for minor adjustment to your theme.


### CKEditor Skin
Select CKEditor skin.


### Developer tools
Settings to help with theme development.


### Legacy browsers
Settings to support crappy old browsers like IE8. Use with caution, do not enable this unless you really, really need it.


### Markup overrides

Responsive tables
Breadcrumbs
Search block
Login block
Comment titles
Feed icons
Skip link
Attribution
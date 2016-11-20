##  Where to place new component styles?

In short - this is up to you, i.e. whatever suites the themer. For teams you might develop a strategy so everyone is on the same page to provide consistency across projects and team members.


I can outline two basic approaches:


- Add to existing partials.
- Create new partials.


Let's examine a new component to see how it can fit into the above strategies: a new entity (node) view mode.


###  Add to existing partials
In this scenario you can just add styles to the existing _node.scss partial. Styles will be automatically compiled into the corresponding CSS file and that's it. Done.


### Create new partials
If you want to create new partials to separate concerns you need a strategy. You could, for example, create a partial called _node.view-modes.scss and place all custom view mode styles there. Otherwise you might create separate per-view-mode partials, e.g. `_node.custom-view-mode.scss`. 


You would then add @import directives to the node.scss file so they’re imported and compiled.
I.e. in `~/styles/uikit/components/node.scss` you would have the following to import the node partials.


    @import "partials/base/base";
    @import "partials/component/node";
    @import "partials/component/node.custom-view-mode";


### Points to Consider


Selector grouping - many different partials is not the DRYest approach, if selector grouping is also part of the strategy you’d probably go with adding to existing partials.

Inheritance and the cascade can be more difficult to debug across many partials,  however with modern browser inspectors and Source maps this is largely mitigated.

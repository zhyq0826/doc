Coding Style
-------------------------

- Use soft-tabs with a two space indent.
- Put spaces after : in property declarations.
- Put spaces before { in rule declarations.
- Use hex color codes #000 unless using rgba.
- Use // for comment blocks (instead of /* */).
- Document styles with `KSS <https://github.com/kneath/kss>`_.

Here is good example syntax:

.. code-block:: bash

    // This is a good example!
    .styleguide-format {
      border: 1px solid #0f0;
      color: #000;
      background: rgba(0,0,0,0.5);
    }


SCSS Style
-------------------------

- Any $variable or @mixin that is used in more than one file should be put in globals/. Others should be put at the top of the file where they're used.

- As a rule of thumb, don't nest further than 3 levels deep. If you find yourself going further, think about reorganizing your rules (either the specificity needed, or the layout of the nesting).


File Organization
-------------------------

.. code-block:: bash

    styles
    ├── components
    │   ├── comments.scss
    │   └── listings.scss
    ├── globals
    │   ├── browser_helpers.scss
    │   ├── responsive_helpers.scss
    │   ├── variables.scss
    ├── plugins
    │   ├── jquery.fancybox-1.3.4.css
    │   └── reset.scss
    ├── sections
    │   ├── issues.scss
    │   ├── profile.scss
    └── shared
        ├── forms.scss
        └── markdown.scss


Use Sprockets to require files. However, you should explicitly import any scss that does not generate styles (globals/) in the particular SCSS file you'll be needing it's helpers in. Here's a good example:

.. code-block:: bash

    //= require_tree ./plugins
    //= require my_awesome_styles

    @import "../globals/basic";

    .rule { ... }

Specificity (classes vs. ids)
-----------------------------------

Elements that occur exactly once inside a page should use IDs, otherwise, use classes. When in doubt, use a class name.

- Good candidates for ids: header, footer, modal popups.
- Bad candidates for ids: navigation, item listings, item view pages (ex: issue view).

When styling a component, start with an element + class namespace (prefer class names over ids), prefer direct descendant selectors by default, and use as little specificity as possible. Here is a good example:

.. code-block:: bash

    <ul class="category-list">
    <li class="item">Category 1</li>
    <li class="item">Category 2</li>
    <li class="item">Category 3</li>
    </ul>

    ul.category-list { // element + class namespace

    &>li { // direct descendant selector > for list items
      list-style-type: disc;
    }

    a { // minimal specificity for all links
        color: #ff0000;
      }
    }


**CSS Specificity guidelines**

- If you must use an id selector (#selector) make sure that you have no more than one in your rule declaration. A rule like #header .search #quicksearch { ... } is considered harmful.
- When modifying an existing element for a specific use, try to use specific class names. Instead of .listings-layout.bigger use rules like .listings-layout.listings-bigger. Think about ack/greping your code in the future.
- The class names disabled, mousedown, danger, hover, selected, and active should always be namespaced by a class (button.selected is a good example).


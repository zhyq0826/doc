Coding Style
------------------

**CoffeeScript**

- Write new JS in CoffeeScript.
- Use soft-tabs with a two space indent.
- Always use camelCase, never underscores.
- Use implicit parentheses when possible.
- Follow @jashkenas's style. See the documentation for good examples.
- Any top level objects should be namespaced under the GitHub namespace.
- Don't ever use $.get or $.post. Instead use $.ajax and provide both a success handler and an error handler.
- Use $.fn.on instead of $.fn.bind, $.fn.delegate and $.fn.live

**Existing JavaScript**

- Avoid adding new .js files.
- Use soft-tabs with a two space indent.
- Do your best to never use a semicolon. This means avoiding them at line breaks and avoiding multi-statement lines. For more info, read Mislav's blog post.

Selectors
-------------------

Try to prefix all javascript-based selectors with js-. This is taken from `slightly obtrusive javascript <http://ozmm.org/posts/slightly_obtrusive_javascript.html>`_. The idea is that you should be able to tell a presentational class from a functional class. Most of the codebase doesn't do this, let's try and move toward it.

Behaviors
-------------------

**MENU**

A simple pop-up menu. You'll need a containing element with js-menu-container, something to click to open the element js-menu-target, then the menu itself js-menu-content.

.. code-block:: bash

    <style>
    .example1.js-menu-container .js-menu-content {
      display: none;
    }
    .example1.js-menu-container.active .js-menu-content {
      display: block;
      position: absolute;
      background: white;
      border: 1px solid grey;
      width: 50px;
      padding: 2px 10px;
    }
    </style>
    <div class="example1 js-menu-container">
      <a href="#" class="js-menu-target">Tags</a>

      <div class="js-menu-content">
        <p>1.0</p>
        <p>1.1</p>
        <p>1.2</p>
      </div>
    </div>

**DETAILS**

With the details behavior you can implement simple div toggling without writing any extra JavaScript. You just need to apply 2 classes classes. js-details-container to the containing element and js-details-target to the clickable element.

.. code-block:: bash

    <style>
    .example2 .content {
      display: none;
    }
    .example2.open .content {
      display: block;
    }
    </style>
    <div class="example2 js-details-container">
      <a href="#" class="minibutton js-details-target">Show More</a>
      <div class="content">Hidden Contents</div>
    </div>

**Select Menu**

Create a select menu in a button without a label.

- Sentence case menu titles, rather than title case.
- The popup menu is 6px below the button.
- Selected items in the list are checked.
- Mouse over on each list item turns them blue with white text.
- The checkmark is top aligned with the text.
- The button changes to an active state while the popup is displayed.

.. code-block:: bash
    
    <div class="select-menu js-menu-container js-select-menu">
      <span class="minibutton select-menu-button js-menu-target">
        <span class="mini-icon mini-icon-advanced-search"></span>
      </span>

      <div class="select-menu-modal-holder js-menu-content js-navigation-container">
        <div class="select-menu-modal">
          <div class="select-menu-header">
            <span class="select-menu-title">select-menu Title</span>
            <span class="mini-icon mini-icon-remove-close js-menu-close"></span>
          </div> <!-- /.select-menu-header -->

          <div class="select-menu-list">

            <div class="select-menu-item js-navigation-item js-navigation-target">
              <span class="select-menu-item-icon mini-icon mini-icon-confirm"></span>
              <div class="select-menu-item-text">List item 1</div>
            </div> <!-- /.select-menu-item -->

            <div class="select-menu-item js-navigation-item js-navigation-target">
              <span class="select-menu-item-icon mini-icon mini-icon-confirm"></span>
              <div class="select-menu-item-text">List item 2</div>
            </div> <!-- /.select-menu-item -->

            <div class="select-menu-item js-navigation-item js-navigation-target">
              <span class="select-menu-item-icon mini-icon mini-icon-confirm"></span>
              <div class="select-menu-item-text">List item 3</div>
            </div> <!-- /.select-menu-item -->

          </div> <!-- /.select-menu-list -->
        </div> <!-- /.select-menu-modal -->
      </div> <!-- /.select-menu-modal-holder -->
    </div> <!-- /.select-menu -->
     <div class="select-menu js-menu-container js-select-menu">
      <span class="minibutton select-menu-button js-menu-target">
        <span class="mini-icon mini-icon-advanced-search"></span>
      </span>

      <div class="select-menu-modal-holder js-menu-content js-navigation-container">
        <div class="select-menu-modal">
          <div class="select-menu-header">
            <span class="select-menu-title">select-menu Title</span>
            <span class="mini-icon mini-icon-remove-close js-menu-close"></span>
          </div> <!-- /.select-menu-header -->

          <div class="select-menu-list">

            <div class="select-menu-item js-navigation-item js-navigation-target">
              <span class="select-menu-item-icon mini-icon mini-icon-confirm"></span>
              <div class="select-menu-item-text">List item 1</div>
            </div> <!-- /.select-menu-item -->

            <div class="select-menu-item js-navigation-item js-navigation-target">
              <span class="select-menu-item-icon mini-icon mini-icon-confirm"></span>
              <div class="select-menu-item-text">List item 2</div>
            </div> <!-- /.select-menu-item -->

            <div class="select-menu-item js-navigation-item js-navigation-target">
              <span class="select-menu-item-icon mini-icon mini-icon-confirm"></span>
              <div class="select-menu-item-text">List item 3</div>
            </div> <!-- /.select-menu-item -->

          </div> <!-- /.select-menu-list -->
        </div> <!-- /.select-menu-modal -->
      </div> <!-- /.select-menu-modal-holder -->
    </div> <!-- /.select-menu -->
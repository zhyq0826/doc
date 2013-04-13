sublime setting
===========================

sublime 可以根据个人喜好以及编程语言来定制自己的设置，分别包含有

-   **默认设置**
    
    Preference-->Settings Default

-   **用户设置**

    Preference-->Settings User

-   **语言设置**
    Preference-->Settings More-->Synta Specific User

默认设置优先级最高，其次是语言设置和用户设置,例如当前打开文件时html，选择语言设置时，可看到打开的设置包是

.. code-block:: bash
    
    Packages\User\HTML.sublime-setting

可以针对html语言进行自己的偏好设置

**注意**
    
    sublime 在打开文件时会检测文件的设置比如缩进等，这是检测的结果会覆盖其他的设置，可以在配置中设置取消检测

    .. code-block:: bash
        {
            "detect_indentation":false
        }


user
---------------------

.. code-block:: bash

    {
        "color_scheme": "Packages/Color Scheme - Default/Cobalt.tmTheme",
        "font_size": 12.0,
        "ignored_packages":
        [
            "Vintage"
        ],
        "translate_tabs_to_spaces": true
    }

python
---------------------

.. code-block:: bash

    {
        "color_scheme": "Packages/Color Scheme - Default/Cobalt.tmTheme",
        "font_size": 12.0,
        "ignored_packages":
        [
            "Vintage"
        ],
        "tab_size": 4,s
        "translate_tabs_to_spaces": true
    }

css html javascript
----------------------

.. code-block:: bash
    {
        "color_scheme": "Packages/Color Scheme - Default/Cobalt.tmTheme",
        "font_size": 12.0,
        "ignored_packages":
        [
            "Vintage"
        ],
        "tab_size": 2,
        "translate_tabs_to_spaces": true
    }

useful plugin
----------------------

- JsFormat
- SublimeCodeIntel
- ZenCoding
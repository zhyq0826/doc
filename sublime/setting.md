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

```
    
    Packages\User\HTML.sublime-setting

```

可以针对html语言进行自己的偏好设置

**注意**
    
sublime 在打开文件时会检测文件的设置比如缩进等，这是检测的结果会覆盖其他的设置，可以在配置中设置取消检测

```

    {
        "detect_indentation":false
    }

```

user
---------------------

```

    {
        "color_scheme": "Packages/Color Scheme - Default/Cobalt.tmTheme",
        "font_size": 12.0,
        "ignored_packages":
        [
            "Vintage"
        ],
        "translate_tabs_to_spaces": true,
        "font_face": "Ubuntu Mono",               //only in Ubuntu 
    }

```

python
---------------------

```

    {
        "color_scheme": "Packages/Color Scheme - Default/Cobalt.tmTheme",
        "font_size": 12.0,
        "ignored_packages":
        [
            "Vintage"
        ],
        "tab_size": 4,
        "translate_tabs_to_spaces": true
    }

```

html javascript
----------------------

```

    {
        "color_scheme": "Packages/Color Scheme - Default/Cobalt.tmTheme",
        "font_size": 12.0,
        "ignored_packages":
        [
            "Vintage"
        ],
        "tab_size": 4,
        "translate_tabs_to_spaces": true
    }

```

css 
------------------------

```

    {
        "color_scheme": "Packages/Color Scheme - Default/Cobalt.tmTheme",
        "font_size": 12.0,
        "ignored_packages":
        [
            "Vintage"
        ],
        "tab_size": 4,
        "translate_tabs_to_spaces": true,
        // Calculates indentation automatically when pressing enter
        "auto_indent": true,
        // Adds whitespace up to the first open bracket when indenting. Requires
        // auto_indent to be enabled.
        "indent_to_bracket": true
    }

```

auto pep8
-------------------------

```

    {
        "max-line-length": 120,
        "ignore":"E24, E226, W191"
    }
```

sublimeLinter
--------------------------

- W191: 80 long
- E231: after : is whitespace

```

    {
        "pep8_ignore":
        [
            "E501",
            "W191",
            "E231"
        ]
    }

```


useful plugin
----------------------

- JsFormat
- [SublimeCodeIntel](https://github.com/SublimeCodeIntel/SublimeCodeIntel)
- [ZenCoding or emmet](<http://emmet.io>)
- GitGutter
- VSCGutter
- [sublime_alignment](https://github.com/wbond/sublime_alignment)
- [Bracket Hightlighter](https://github.com/facelessuser/BracketHighlighter)
- [AutoPEP8](https://github.com/hhatto/autopep8)
- MarkDown Build
- MarkDown preview
- SublimeLinter
- [flatland](https://github.com/thinkpixellab/flatland)
- [Jedi - Python autocompletion](https://github.com/davidhalter/jedi)
- [SublimeRope](https://github.com/JulianEberius/SublimeRope)

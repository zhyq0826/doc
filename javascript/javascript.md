# JavaScript

## Identifiers

- **RULE**: Identifiers bound to constructors **must** start with a capital.

- **RULE**: 绑定到构造函数的标识符必须以 **大写** 开头.

```javascript
  // GOOD

  var User = function (name, age) {
      this.name = name;
      this.age = age;
  };
  var user = new User('bob', 32);

```


```javascript
  // BAD

  var user = function (name, age) {
      this.name = name;
      this.age = age;
  };
  var u = new user('bob', 32);

```

- **RULE**: Identifiers bound to a variable or function **must** start with a *minuscule*.
- **RULE**: Identifiers bound to a variable or function **must** be CamelCased or lowercase,
  depending on their length.

- **RULE**: 绑定到函数和字面量的标识符必须以 **小写** 开头且必须是 **驼峰风格** 或全部小写

```javascript
  // GOOD

  var someKindOfProcess = function () {};
  var tmpvar = 42;

```


```javascript
  // BAD

  var some_kind_of_process = function () {};
  var somekindofprocess = function () {};

```

## Variable declarations

- **RULE**: Variables **must** always be declared, prior to use.
- **RULE**: Variable declarations **should** appear at the top of functions,
  and not inside other blocks. The exception is *for* loops.

- **RULE**: 变量必须在使用之前声明,而且声明位置不应该是除函数的顶部或者 **loop** 循环内的内部其他位置

> Variable declarations are moved up to the top of the function scope anyway,
> so that's where they belong.


```javascript
  // GOOD

  function (a, b) {
      var k;

      if (a == b) {
          k = true;
      }
      ...
  }

  for (var i = 0; i < l; i ++) { ... }

```


```javascript
  // BAD

  function (a, b) {
      if (a == b) {
          var k = true;
      }
      ...
  }

```

## Control-flow

- **RULE**: Control-flow statements, such as `if`, `while` and `for` **must** have a space between the keyword and the left parenthesis.

- **RULE**: 流程控制语句，像`if`,`while`,`for`，在这些关键字和左括号之间必须有空格

> They aren't functions, and thus better distinguished like this.

```javascript
  // GOOD

  if (a) {
      return true;
  }

```

```javascript
  // BAD

  if(a) {
      return true;
  }

```

## Functions

- **RULE**: Anonymous functions **must** have a space between the `function` keyword and the left parenthesis.

- **RULE**: 匿名函数必须在`function`关键字和左括号之间有空格

> To emphasise the lack of identifier and differentiate them with named functions.


```javascript
  // GOOD

  function (a, b) {}

```


```javascript
  // BAD

  function(a, b) {}

```

- **RULE**: Named functions **must not** have a space between the function name and the left parenthesis.
- **RULE**: Function calls **should not** have a space between the function name and the left parenthesis.

- **RULE**: 命名函数不能在函数名和左括号之间有空格,函数调用也一样

```javascript
  // GOOD

  function add(a, b) {}

  add(2,3)

```


```javascript
  // BAD

  function add (a, b) {}

  add (2,3)

```

## Semicolons

- **RULE**: Semicolons `;` **must** be added at the end of every statement, **except** when the next character is a closing bracket `}`.
  In that case, they may be omitted.

- **RULE**: 分号必须添加在每一个语句的结束后，如果下一个字符是一个闭合的`}`，则分号舍弃(分号的使用一直存在争议，github建议根本不用分号)

```javascript
  // GOOD

  var f = function add(a, b) {
      if (a == b) { return a * 2 }   // No `;` here.
      return a + b;
  };

```


```javascript
  // BAD

  var f = function add (a, b) {
      return a + b
  }

```

## Braces

- **RULE**: Braces **should** be used in all circumstances. They **may** be omitted
  around simple statements.

- **RULE**: 括号应该在所有地方使用，只在语句特别简单时考虑不使用它们


```javascript
  // GOOD

  if (x) { return true }

```

```javascript
  // BAD

  if (x)
    while (1)
      i ++;
  else
    ...
```


```javascript
  // OK

  if (x) return true;

```

```javascript
  // OK

  if (x)
      return true;

```
- **RULE**: Opening Braces **must never** be on a line of their own.

- **RULE**: 起始的括号永远不要自成一行

> Vertical screen space is precious.

```javascript
  // GOOD

  if (x) {
      return true;
  }

```


```javascript
  // BAD

  if (x)
  {
      return true;
  }

```

```javascript
  // BAD

  if (x) {
      return true; }

```



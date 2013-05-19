# css 组织结构

## 组织结构

css 按照不同的用途可以划分出不同的组织

- **base**
- **layout**
- **module**
- **state**
- **theme**

### base

基础样式，包括reset等 ,多以标签选择器为主



### layout

布局样式按布局的不同可以分为列式布局，固定布局，流式布局

#### 命名规则
以layout 开头或者缩写,如果名字意义明显不加也可

```css

    //块状
    .grid {

    }

    //行式
    .row {

    }
    
    //列式
    .collum {

    }
    
    //行式自适应
    .row-fluid {

    }

    //列式自适应
    .collum-fluid {

    }

```

### module

按项目需要组织不同的模块nav, tooltip, button, menu


#### 命名规则

按照模块具体的名称,如果有子模块需要特别定制,以父模块开头或者结尾,尽量把子模块和父模块组织到一个文件中.
例如所有nav 都在nav的文件中

```css

    .nav {

    }

    .tooltip {

    }

    .button {

    }

    .nav-search {

    }


    .submit-button {

    }

```

### state 和 theme 

模块的状态

### 命名规则

以is开头,状态和模块同在一个文件

```css

    .is-active {

    }

    .is-collapse {

    }

```

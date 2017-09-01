# MiniRefresh库暴露的全局变量

## MiniRefreshTools

`minirefresh`核心类暴露的全局变量，该变量的层级大概如下

```
MiniRefreshTools
    |- -                 // 直接.xxx就能调用的一些工具方法
    |   |- extend        // 对象的拓展
    |   |- Clazz         // 模拟Class
    |   |- ...           // 更多工具方法
    |- - core            // minirefresh的核心，定义了需要暴露的API，所有的主题都继承自核心
    |- - theme           // minirefresh的主题，每定义一个主题都会挂载到这个命名空间下
    |   |- defaults      // 默认的主题
    |   |- applet        // 仿微信小程序主题
    |   |- taobao        // 仿淘宝刷新主题
    |   |- drawer3d      // 3D抽屉效果主题
    |   |- drawerslider  // 滑动抽屉效果主题
```

例如，访问`applet`主题的方法为`MiniRefreshTools.theme.applet`

注意:

```html
<script type="text/javascript" src="xxx/minirefresh.js"></script>
```

如果是上述这样脚本方式引入，默认会在`window`对象上绑定`MiniRefreshTools`

```js
var MiniRefreshTools = require('xxx/minirefresh.js');
```

```js
import { MiniRefreshTools } from 'xxx/minirefresh.js';
```

上述是通过`require`或`import`引入方式获取全局变量的方法

## MiniRefresh

当前使用的主题的变量，每一个主题都会覆盖这个变量，因此

__一般情况这个变量指向最后一个引用的主题__

例如

```html
<script type="text/javascript" src="xxx/minirefresh.js"></script>
<script type="text/javascript" src="xxx/minirefresh.theme.applet.js"></script>
```

```js
var MiniRefreshTools = require('xxx/minirefresh.js');

require('xxx/minirefresh.theme.applet.js');
```

```js
import { MiniRefreshTools } from 'xxx/minirefresh.js';

import 'xxx/minirefresh.theme.applet.js';
```

按照上述方法引入后，`MiniRefresh`指向的是`applet`主题（即`MiniRefreshTools.theme.applet`）
# applet主题

仿微信小程序主题

__继承自default__

![](https://minirefresh.github.io/minirefresh/staticresource/screenshoot/theme_applet.gif)

## 引入

```html
<link rel="stylesheet" href="xxx/minirefresh.css" />
<link rel="stylesheet" href="xxx/minirefresh.theme.applet.css" />
...

<script type="text/javascript" src="xxx/minirefresh.js"></script>
<script type="text/javascript" src="xxx/minirefresh.theme.applet.js"></script>
```

```js
// 同时支持NPM与文件形式引入
var MiniRefreshTools = require('xxx/minirefresh.js');
require('xxx/minirefresh.css');

require('xxx/minirefresh.theme.applet.js');
require('xxx/minirefresh.theme.applet.css');
```

```js
// debug下是.js dist下是.min.js
import MiniRefreshTools from 'xxx/minirefresh.js';
import 'minirefresh/dist/debug/minirefresh.css'

import 'minirefresh/dist/debug/themes/applet/minirefresh.theme.applet.js';
import 'minirefresh/dist/debug/themes/applet/minirefresh.theme.applet.css';
```

## 说明

这个主题继承自`default`主题

享有`default`主题的所有配置以及API方法

## `options`配置

无（除default提供的外，无新的配置）

## API方法

无（除default提供的外，无新的API）


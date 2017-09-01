# default主题

默认打包的主题

__继承自Core__

![](https://minirefresh.github.io/minirefresh/staticresource/screenshoot/base_default.gif)

## 引入

```html
<link rel="stylesheet" href="xxx/minirefresh.css" />

...

<script type="text/javascript" src="xxx/minirefresh.js"></script>
```

```js
var MiniRefreshTools = require('xxx/minirefresh.js');
```

```js
import { MiniRefreshTools } from 'xxx/minirefresh.js';
```

## 说明

这个主题定义了默认的UI实现，很多其它官方主题都是继承于它的，另外在`core`的基础上新增了一些功能

- `toTop`（实现了一个滚动到顶部效果）

所有继承自`default`主题的主题都享有它的配置以及API方法

## `options`配置

在`core`的配置的基础上，新增以下配置：

__down的配置__

| 参数 | 参数类型 | 默认值 |说明 |
| :------------- |:-------------:|:-------------:|:-------------|
| isWrapCssTranslate | Boolean | false | 是否下拉时wrap（下拉区域不是内容区域，与scroll区分开）会跟随css translate |
| contentdown | String | '下拉刷新' | 下拉刷新默认提示 |
| contentover | String | '释放刷新' | 在超过阈值后的提示 |
| contentrefresh | String | '加载中...' | 正在刷新中的提示 |
| contentsuccess | String | '刷新成功' | 刷新成功后，结束前，成功状态的提示 |
| contenterror | String | '刷新失败' | 刷新成功后，结束前，失败状态的提示 |

__up的配置__

| 参数 | 参数类型 | 默认值 |说明 |
| :------------- |:-------------:|:-------------:|:-------------|
| contentdown | String | '上拉显示更多' | 上拉加载默认提示，一般默认情况会隐藏用不到它 |
| contentrefresh | String | '加载中...' | 上拉加载时的提示 |
| contentnomore | String | '没有更多数据了' | 没有更多数据时的提示 |
| toTop | Object | 默认配置 | 滚动到顶部的相关配置，图片的话请在css中修改 |
| toTop.isEnable | Boolean | true | 是否开启自动滚动到顶部  |
| toTop.duration | Number | 300 | 滚动到顶部的过渡时间  |
| toTop.offset | Number | 800 | 阈值，滚动超过多少距离后才会显示滚动到顶部按钮  |

## API方法

无（除Core提供的外，无新的API）
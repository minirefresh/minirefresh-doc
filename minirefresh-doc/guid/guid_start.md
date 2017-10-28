# 快速开始

## 安装

### NPM

```js
npm install minirefresh
```

[https://www.npmjs.com/package/minirefresh](https://www.npmjs.com/package/minirefresh)

### GIT

```js
git clone git://github.com/minirefresh/minirefresh.git
```

[https://github.com/minirefresh/minirefresh](https://github.com/minirefresh/minirefresh)

## 引入

```html
<link rel="stylesheet" href="xxx/minirefresh.css" />
<script type="text/javascript" src="xxx/minirefresh.js"></script>
```

### `require`引入

```js
// 同时支持NPM与文件形式引入
var MiniRefreshTools = require('xxx/minirefresh.js');
require('xxx/minirefresh.css');
```

### `import`引入

```js
// debug下是.js dist下是.min.js
import MiniRefreshTools from 'minirefresh';
import 'minirefresh/dist/debug/minirefresh.css'
```

## 页面布局

```html
<!-- minirefresh开头的class请勿修改 -->
<div id="minirefresh" class="minirefresh-wrap">
    <div class="minirefresh-scroll">        
    </div>
</div>
```

## 初始化

```js
// 引入任何一个主题后，都会有一个 MiniRefresh 全局变量
var miniRefresh = new MiniRefresh({
    container: '#minirefresh',
    down: {
        callback: function() {
            // 下拉事件
        }
    },
    up: {

        callback: function() {
            // 上拉事件
        }
    }
});
```

### 结束刷新

```js
// 结束下拉刷新
miniRefresh.endDownLoading();
```

```js
// 结束上拉加载
// 参数为true代表没有更多数据，否则接下来可以继续加载
miniRefresh.endUpLoading(true);
```
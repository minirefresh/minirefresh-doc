# 快速开始

## 安装

### NPM

```js
npm install minirefresh
```

### GIT

```js
git clone git://github.com/minirefresh/minirefresh.git
```

## 引入

```html
<link rel="stylesheet" href="xxx/minirefresh.css" />
<script type="text/javascript" src="xxx/minirefresh.js"></script>
```

### `require`引入

```js
// npm安装情况
var MiniRefresh = require('minirefresh');
```

```js
// 直接通过路径引入
var MiniRefresh = require('xxx/minirefresh.js');
```

## 页面布局

```html
<div id="minirefresh" class="minirefresh-wrap">
    <div class="minirefresh-scroll">        
    </div>
</div>
```

## 初始化

```js
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
# taobao主题

仿淘宝，包括淘宝二楼

__继承自default__

![](https://minirefresh.github.io/minirefresh/staticresource/screenshoot/theme_taobao.gif)

## 引入

参考`applet主题`中的引入，文件其中主题的样式和脚本换为如下名称

```js
taobao/minirefresh.theme.taobao.css
taobao/minirefresh.theme.taobao.js
```

## 说明

这个主题继承自`default`主题

享有`default`主题的所有配置以及API方法

## `options`配置

除了默认配置外，新增了一个秘密花园配置（仿淘宝二楼）

__down的配置__

| 参数 | 参数类型 | 默认值 |说明 |
| :------------- |:-------------:|:-------------:|:-------------|
| secretGarden | Object | 默认配置 | 秘密花园的配置 |
| secretGarden.isEnable | Boolean | true | 是否开启  |
| secretGarden.offset | Number | 200 | 阈值，超过多少阈值后才会触发秘密花园，这个阈值大于下拉阈值，是先下拉，再拉才会触发秘密花园  |
| secretGarden.tips | String | '欢迎光临秘密花园' | 可以进入秘密花园时的提示文字 |
| secretGarden.inSecretGarden | Function | 空函数 | 进入秘密花园后的回调，可以在回调中处理自定义事件，然后特定时候关闭秘密花园 |

## API方法

### resetSecretGarden()

关闭秘密花园

当触发秘密花园后，可以在特定的情况下关闭它

```js
minirefresh.resetSecretGarden();
```







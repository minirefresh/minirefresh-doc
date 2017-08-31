# MiniRefresh核心API

所有的主题都拥有的核心API（即`core`类的API）

## `options`配置说明

核心API有一些通用的`options`配置（生效与所有主题）

```js
new MiniRefresh(options);
```

| 参数 | 参数类型 | 默认值 |说明 |
| :------------- |:-------------:|:-------------:|:-------------|
| down | Object | 默认配置 | 下拉的默认配置 |
| up | Object | 默认配置 | 上拉的默认配置 |
| container | String | '#minirefresh' | minirefresh容器的selector |

__down的配置__

```js
{
    down: {
        xxx: xxx
    }
}
```

| 参数 | 参数类型 | 默认值 |说明 |
| :------------- |:-------------:|:-------------:|:-------------|
| isLock | Boolean | false | 是否锁定下拉刷新，如果锁定了，则无法下拉 |
| isAuto | Boolean | false | 是否初始化时自动执行一次下拉刷新，优先级要高于上拉加载的auto，并且两个auto只会执行一次 |
| isAways | Boolean | false | 是否运行在上拉时也可以下拉，如果为false，上拉时无法触发下拉刷新 |
| isAllowAutoLoading | Boolean | true | 设置isAuto=true时生效，是否在初始化的下拉刷新触发事件中显示动画，如果是false，初始化的加载只会触发回调，不会触发动画 |
| isScrollCssTranslate | Boolean | true | 请只在定制主题时使用，是否在下拉时scroll（内容区域）跟随css translate动画，如果为false，下拉时只会回调下拉距离，scroll不会跟随动画，常用来定制自定义下拉刷新 |
| offset | Number | 75 | 触发下拉的阈值，当下拉距离大于这个阈值后，在松开时会触发下拉刷新 |
| dampRate | Number | 0.3 | 下拉超过阈值后的阻尼系数，越接近0，下拉高度变化越小，例如0.1时表现是超过阈值后基本就拉不动了 |
| bounceTime | Number | 300 | 回弹动画时间，下拉取消后或结束后到关闭时，会有一个回弹时间过渡  |
| successAnim | Object | 默认配置 | 成功动画配置相关，请只在实现了成功动画的主题中使用，比如default主题,目前成功动画只是保留功能，因为以后可能有主题需要它 |
| successAnim.isEnable | Boolean | false | 是否开启成功动画，开启后，下拉结束之前会先出现成功动画  |
| successAnim.duration | Number | 300 | 成功动画的过度时间  |
| onPull | Function | 空函数 | 下拉过程中的持续回调，回调参数（downHight, downOffset）  |
| onCalcel | Function | 空函数 | 取消下拉后的回调,当下拉超过阈值，并松开就会触发  |
| callback | Function | 空函数 | 触发下拉刷新后的回调  |

__up的配置__

```js
{
    up: {
        xxx: xxx
    }
}
```

| 参数 | 参数类型 | 默认值 |说明 |
| :------------- |:-------------:|:-------------:|:-------------|
| isLock | Boolean | false | 是否锁定上，如果锁定了，则无法上拉 |
| isAuto | Boolean | false | 是否初始化时自动执行一次上拉加载（会同时有动画和回调），当下拉的down的isAuto生效时，这个不会生效 |
| isShowUpLoading | Boolean | true | 上拉加载的过程中是否显示动画，如果为false，代表静默加载，没有动画 |
| offset | Number | 75 | 触发上拉的阈值，当滑动到距离底部距离小于这个阈值时，会触发上拉加载 |
| loadFull | Object | 默认配置 | 自动加载满屏相关配置 |
| loadFull.isEnable | Boolean | true | 是否开启自动加载满屏，开启后，如果当前页面数据没有满屏，并且可以加载更多，就会自动触发上拉加载  |
| loadFull.delay | Number | 300 | 延迟加载的时间，自动加载满屏时，会延迟一定时间才加载  |
| onScroll | Function | 空函数 | 滚动时的持续回调，回调参数（scrollTop）  |
| callback | Function | 空函数 | 触发上拉加载后的回调  |

## API方法

`minirefresh`对象可以调用

```js
var minirefresh = new MiniRefresh({...});

minirefresh.method();
```

### triggerDownLoading(isShowLoading)

触发下拉刷新

```js
minirefresh.triggerDownLoading();
```

__参数说明__

| 参数 | 参数类型  | 说明  |
| :------------- |:-------------:|:-------------|
| isShowLoading | Boolean | 是否显示loading动画，默认为`true`，如果关闭动画，每次触发时只会触发回调而不会触发动画 |

### triggerUpLoading(isShowLoading)

触发上拉加载

```js
minirefresh.triggerUpLoading();
```

__参数说明__

| 参数 | 参数类型  | 说明  |
| :------------- |:-------------:|:-------------|
| isShowLoading | Boolean | 是否显示loading动画，默认为`true`，如果关闭动画，每次触发时只会触发回调而不会触发动画 |

### endDownLoading(isSuccess)

结束下拉刷新

```js
minirefresh.endDownLoading(true);
```

__参数说明__

| 参数 | 参数类型  | 说明  |
| :------------- |:-------------:|:-------------|
| isSuccess | Boolean | 只有主题实现了success动画并开始时才有效，是否下拉并处理成功，默认为`true`，为`true`时会走入成功动画，否则走入失败动画 |

### endUpLoading(isFinishUp)

结束上拉加载

```js
minirefresh.endUpLoading(false);
```

__参数说明__

| 参数 | 参数类型  | 说明  |
| :------------- |:-------------:|:-------------|
| isFinishUp | Boolean | 默认为`false`，是否没有更多数据，如果为`true`，会变为没有更多数据，不能继续加载更多，直到下拉刷新后更新状态或者主动resetUp状态才能继续加载 |

### resetUpLoading()

重置上拉加载状态,如果是没有更多数据后重置，会变为可以继续上拉加载

```js
minirefresh.resetUpLoading();
```

### scrollTo(y, duration)

在特定的时间内，滚动到指定的y位置

```js
minirefresh.scrollTo(100， 300);
```

__参数说明__

| 参数 | 参数类型  | 说明  |
| :------------- |:-------------:|:-------------|
| y | Number | 需要滚动到位置的top高度 |
| duration | Number | 过渡时间，默认为`0` |

### refreshOptions(options)

刷新minirefresh的配置，刷新后会马上生效

```js
// 更多调用参考showcase中的示例
minirefresh.refreshOptions({...});
```

__参数说明__

| 参数 | 参数类型  | 说明  |
| :------------- |:-------------:|:-------------|
| options | Object | 新的配置参数，有一些属性无法更改 |

__注意:以下配置无法被刷新__

```js
container
down.callback
down.onPull
down.onCalcel
up.callback
up.onScroll
```

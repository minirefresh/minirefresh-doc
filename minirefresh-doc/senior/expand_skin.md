# 拓展自定义皮肤

拓展自定义主题主要需要注意以下几大要点：

- 源码编写注意

- 提交贡献的流程

## 源码编写注意

### 代码编写

关于如何组织代码，可以参考`examples`中的`theme_expand.html`与`theme_modify.html`

[theme_expand.html](https://github.com/minirefresh/minirefresh/blob/master/examples/senior/theme_expand.html)
[theme_modify.html](https://github.com/minirefresh/minirefresh/blob/master/examples/senior/theme_modify.html)

### 代码规范

- 所有的主题源码统一放入`src`中，例如

```js
src
    |- - themes               
    |   |- applet
    |           |- xxx.js
    |           |- xxx.css
    |           |- xxx
```

- 所有的源码必须通过`ESlint`检测

```js
npm run eslint

// 下述是报告导出成html格式_report目录下
npm run eslint:report
```

执行上述命令可以检测代码

- 源码编写完后用`gulp`自动构建出发布包

```js
npm run build
```

构建完后，通过`dist/`下的对应发布文件可以引入主题

### 示例

- 主题都必须有相应的示例

可以放入`examples/themes/`中（示例中的代码也请尽可能规范）

另外`examples/index.html`中可以加入示例链接

- 主题必须有相应的动态图（`xxx.gif`）

截取后放入`staticresource/screenshoot`中（命名请尽量统一）

### 文档

可以参考其它主题以`Markdown`形式写好文档

目前不做强制要求...

### 单元测试

目前不做要求...

## 提交贡献的流程

主题完成，并代码符合规范，自测通过，示例完成后，就可以提交合并流程

- 如果是`Manager`，直接自己`Commit`即可

- 如果是其它贡献者，请提交新的`PR`，可以通知相应的`Manager`来合并

如果符合要求，一般`PR`会被合并，并且可以成为贡献者中的一员


_PS:如果不太善于编码，但是有新的Idea，也可直接通过Issue提出，一起来参与贡献!_
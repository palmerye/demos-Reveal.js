# reveal.js 中文文档

> [文章博客地址](http://palmer.arkstack.cn/RevealJs-slides%E6%BC%94%E7%A4%BA%E5%B7%A5%E5%85%B7-%E4%B8%AD%E6%96%87%E6%96%87%E6%A1%A3/) 👈

> This repository is forked from the official repository of revealjs.It translated by [palmerye](https://github.com/palmerye) in 2017/5/13. welcome **star**! **star**! **star**!

![image](http://ohce3yxd6.bkt.clouddn.com/revealjs/revealjs-zh.jpg)

> 示例： 左图为移动端，右图为PC端，右下为整个slides概览（ESC键）。完整示例：[Demo 预览](http://palmer.arkstack.cn/demos-Reveal.js/)

- [Demo 预览](http://palmer.arkstack.cn/demos-Reveal.js/)
    - 工程位于[gh-pages](https://github.com/palmerye/demos-Reveal.js/tree/gh-pages)分支
- [工程运行指南](#工程安装)
- [中文文档](#revealjs-中文文档)
- [官方英文文档](#revealjs-en)

## 工具框架介绍

- 一个使用 `HTML` 轻松创建精美的演示文稿框架，你只要有一个支持 `CSS 3D` 切换的浏览器(拥抱Chrome, 拒绝IE)。点击查看 [Demo](http://lab.hakim.se/reveal-js/)
- reveal.js 配备了广泛的功能，包括嵌套幻灯片，`Markdown` 内容，`PDF` 导出，演讲笔记和 `JavaScript` API。还有一个全功能的可视化编辑器和平台,可生成在线的slide地址,有免费版和收费版：[slides.com](https://slides.com/)。

## 目录

- [在线编辑](#在线编辑)
- [说明](#说明)
  - [结构](#结构)
  - [_Markdown](#_markdown)
  - [元素属性](#元素属性)
  - [幻灯片属性](#幻灯片属性)
  - [配置 marked](#配置-marked)
- [配置](#配置)
- [尺寸](#演示文稿尺寸)
- [依赖](#依赖)
- [Ready事件](#ready事件)
- [自动播放](#自动播放)
- [自定义快捷键](#自定义快捷键)
- [触屏操作](#触屏操作)
- [延迟加载](#延迟加载)
- [API](#API-CH)
  - [幻灯片更改事件](#幻灯片更改事件)
  - [演示状态](#演示状态)
  - [幻灯片状态](#幻灯片状态)
  - [幻灯片背景](#幻灯片背景)
    - [颜色背景](#颜色背景)
    - [图像背景](#图像背景)
    - [视频背景](#视频背景)
    - [Iframe 背景](#iframe-背景)
    - [背景切换过渡效果](#背景切换过渡效果)
    - [视差背景](#视差背景)
  - [切换过渡效果](#切换过渡效果)
  - [内部跳转](#内部跳转)
  - [片段](#片段)
  - [片段事件](#片段事件)
  - [代码语法高亮](#代码语法高亮)
  - [幻灯片页码](#幻灯片页码)
  - [概览模式](#概览模式)
  - [全屏模式](#全屏模式)
  - [嵌入媒体](#嵌入媒体)
  - [拉伸元素](#拉伸元素)
  - [通信 API](#通信-api)
- [导出 PDF](#导出-pdf)
  - [页面尺寸](#页面尺寸)
  - [打印样式](#打印样式)
  - [步骤](#步骤)
- [主题](#主题)
- [演讲备注](#演讲备注)
  - [共享和打印演讲者备注](#共享和打印演讲者备注)
  - [演讲者备注服务器端](#演讲者备注服务器端)
- [复用插件](#复用插件)
  - [分享和打印演讲备注](#分享和打印演讲备注)
  - [服务器端演讲备注](#服务器端演讲备注)
  - [多路复用](#多路复用)
  - [主演示文稿](#主演示文稿)
  - [客户端演示文稿](#客户端演示文稿)
- [MathJax](#_mathjax)
- [工程安装](#工程安装)
  - [基础安装](#基础安装)
  - [完整安装](#完整安装)
  - [目录结构](#目录结构)

## 更多功能

- [更新日志](https://github.com/hakimel/reveal.js/releases): 获取最新版本.
- [例子](https://github.com/hakimel/reveal.js/wiki/Example-Presentations): 这里有一些基于`reveal.js`的演示例子,也欢迎PR,提供属于你自己的个性例子!
- [浏览器支持](https://github.com/hakimel/reveal.js/wiki/Browser-Support): 浏览器兼容情况.
- [插件](https://github.com/hakimel/reveal.js/wiki/Plugins,-Tools-and-Hardware): 扩展`reveal.js`功能的插件列表.

## 在线编辑

演示文档是使用 `HTML` 或者 `Markdown` 编写的，如果你们更喜欢图形界面的在线编辑器，点击 [https://slides.com](https://slides.com?ref=github) 尝试一下。

## 说明

### 结构
这里有一个简单的例子,充分展示了reveal.js的演示文档结构.
```html
<html>
   <head>
      <link rel="stylesheet" href="css/reveal.css">
      <link rel="stylesheet" href="css/theme/white.css">
   </head>
   <body>
      <div class="reveal">
         <div class="slides">
            <section>Slide 1</section>
            <section>Slide 2</section>
         </div>
      </div>
      <script src="js/reveal.js"></script>
      <script>
         Reveal.initialize();
      </script>
   </body>
</html>
```

演示文档的标签结构需要 `.reveal > .slides > section` 包含，一个 `section` 表示一个 `slide` 而且可以无限重复。如果你在一个 `section` 标签里包含了多个 `section`，那么这几个 `section` 就会垂直分布（意思就是你需要上下切换 `slide`），第一个垂直的 `slide` 位于其它 `slide` 的顶部，同时也是包含在水平 `slide` 序列中。举个例子:
```html
<div class="reveal">
   <div class="slides">
      <section>Single Horizontal Slide</section>
      <section>
         <section>Vertical Slide 1</section>
         <section>Vertical Slide 2</section>
      </section>
   </div>
</div>
```

## _Markdown

`reveal.js` 支持 `Markdown` 来实现内容。使用 `Markdown` 实现内容时，需要在 `section` 标签中添加 `data-markdown` 属性，然后将 `Markdown` 内容写到一个 `text/template` 脚本中，如下例。

> 这是基于 [Paul Irish](https://gist.github.com/1343518) 为了支持 [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown) 而修改的 [data-markdown](https://gist.github.com/1343518)，所以对缩进和换行符都是敏感的，应该避免tabs和空格混用，也要注意换行的使用。 

```html
<section data-markdown>
   <script type="text/template">
      ## Page title

      A paragraph with some text and a [link](http://hakim.se).
   </script>
</section>
```
### 外部 Markdown 文件

可以把 Markdown 内容写在外部文件里，在 reveal.js 运行时进行加载。 引用外部文件时可设置的参数：

- `data-separator` 定义划分横向幻灯片的规则（默认值为 `^\r?\n---\r?\n$`)
- `data-separator-vertical` 定义划分纵向幻灯片的规则（默认禁用）
- `data-separator-notes` 定义当前幻灯片的演讲备注 (默认值为 `note:`)
- `data-charset` 定义外部文件加载时使用的字符集

如果要在本地使用该特性，演示文稿需要运行在[本地服务器上](#full-setup)

```html
<section data-markdown="example.md"  
         data-separator="^\n\n\n"  
         data-separator-vertical="^\n\n"  
         data-separator-notes="^Note:"  
         data-charset="iso-8859-15">
</section>
```

### 元素属性

在 Markdown 内容中，可以通过 html 注释来添加元素属性，如分段：

```html
<section data-markdown>
   <script type="text/template">
      - 列表项 1 <!-- .element: class="fragment" data-fragment-index="2" -->
      - 列表项 2 <!-- .element: class="fragment" data-fragment-index="1" -->
   </script>
</section>
```

### 幻灯片属性

html 注释也可以用来添加幻灯片 `<section>` 元素的属性。

```html
<section data-markdown>
   <script type="text/template">
   <!-- .slide: data-background="#ff0000" -->
      Markdown 内容
   </script>
</section>
```

### 配置 marked

reveal.js 使用 [marked](https://github.com/chjj/marked) 来解析 Markdown，可在设置[reveal 配置](#configuration) 时传入 marked 的配置：

```javascript
Reveal.initialize({
   // 传入 marked 的配置
   // 参考 https://github.com/chjj/marked#options-1
   markdown: {
      smartypants: true
   }
});
```

## 配置

需在页面底部初始化 reveal，所有配置项均为可选，默认值如下：

```javascript
Reveal.initialize({

    // 在右下角显示控制面板
    controls: true,

    // 显示演示进度条
    progress: true,

    // 显示幻灯片页码
    // 可使用代码 slideNumber: 'c/t'，表示 '当前页/总页数'
    slideNumber: false,

    // 幻灯片切换时写入浏览器历史记录
    history: false,

    // 启用键盘快捷键
    keyboard: true,

    // 启用幻灯片概览
    overview: true,

    // 幻灯片垂直居中
    center: true,

    // 在触屏设备上启用触摸滑动切换
    touch: true,

    // 循环演示
    loop: false,

    // 演示方向为右往左，即向左切换为下一张，向右切换为上一张
    rtl: false,

    // 打乱幻灯片顺序
    shuffle: false,

    // 启用幻灯片分段
    fragments: true,

    // 演示文稿是否运行于嵌入模式（如只占页面的一部分）
    // 译者注：与触屏相关
    // false：所有在演示文稿上触发的 "touchmove" 的默认行为都会被阻止
    // true：只有在 "touchmove" 触发了演示文稿事件时才会阻止默认行为
    embedded: false,

    // 是否在按下 ? 键时显示快捷键帮助面板
    help: true,

    // 演讲备注是否对所有人可见
    showNotes: false,

    // 两个幻灯片之间自动播放的时间间隔（毫秒），当设置为 0 时，则禁止自动播放。
    // 该值可以被幻灯片上的 `data-autoslide` 属性覆盖
    autoSlide: 0,

    // 允许停止自动播放
    // 在手动切换分段或幻灯片后暂停自动播放
    // 按 a 键暂停或恢复自动播放
    autoSlideStoppable: true,

    // 使用该函数执行自动播放操作
    autoSlideMethod: Reveal.navigateNext,

    // 启用鼠标滚轮切换幻灯片，作用与 SPACE 相同
    mouseWheel: false,

    // 在移动设备上隐藏地址栏
    hideAddressBar: true,

    // 在 iframe 预览弹框中打开链接
    previewLinks: false,

    // 切换过渡效果
    // none-无/fade-渐变/slide-飞入/convex-凸面/concave-凹面/zoom-缩放
    transition: 'slide', // none/fade/slide/convex/concave/zoom

    // 切换过渡速度
    // default-中速/fast-快速/slow-慢速
    transitionSpeed: 'default', // default/fast/slow

    // 背景切换过渡效果
    backgroundTransition: 'fade', // none/fade/slide/convex/concave/zoom

    // 预加载幻灯片数
    viewDistance: 3,

    // 视差背景图
    parallaxBackgroundImage: '', // 示例："'https://s3.amazonaws.com/hakim-static/reveal-js/reveal-parallax-1.jpg'"

    // 视察背景图尺寸
    parallaxBackgroundSize: '', // CSS 写法，示例："2100px 900px"（目前只支持像素值，不支持 % 和 auto）

    // 相邻两张幻灯片间，视差背景移动的像素值
    // - 如果不设置则自动计算
    // - 当设置为 0 时，则禁止视差动画
    parallaxBackgroundHorizontal: null,
    parallaxBackgroundVertical: null

});
```
在执行初始化后，可通过 configure 方法来更新配置：

```javascript
// 关闭自动播放
Reveal.configure({ autoSlide: 0 });

// 开启自动播放（时间间隔为 5 秒）
Reveal.configure({ autoSlide: 5000 });
```

## 演示文稿尺寸

演示文稿有一个标准尺寸，框架会在其基础上自动缩放以适应各种分辨率。

尺寸相关的配置项及其默认值如下：
```javascript
Reveal.initialize({

  ...

  // 演示文稿缩放时，会保持标准尺寸的宽高比。
  // 可使用百分比，如：'200%'
  width: 960,
  height: 700,

  // 内容外边距
  margin: 0.1,

  // 内容缩放比例的最小值/最大值
  minScale: 0.2,
  maxScale: 1.5

});
```
如果想要使用自定义的缩放方式（如使用媒体查询），可通过下面的设置来禁用自动缩放：
```javascript
Reveal.initialize({

  ...

  width: "100%",
  height: "100%",
  margin: 0,
  minScale: 1,
  maxScale: 1
});
```
## 依赖

Reveal.js 的部分功能需要引入自带的第三方库，可在初始化时传入依赖项，运行时会自动加载。

```javascript
Reveal.initialize({
  dependencies: [
    // classList 跨浏览器支持 - https://github.com/eligrey/classList.js/
    { src: 'lib/js/classList.js', condition: function() { return !document.body.classList; } },

    // 解析 <section> 元素里的 Markdown 内容
    { src: 'plugin/markdown/marked.js', condition: function() { return !!document.querySelector( '[data-markdown]' ); } },
    { src: 'plugin/markdown/markdown.js', condition: function() { return !!document.querySelector( '[data-markdown]' ); } },

    // <code> 元素语法高亮
    { src: 'plugin/highlight/highlight.js', async: true, callback: function() { hljs.initHighlightingOnLoad(); } },

    // Alt+click 缩放点击元素
    { src: 'plugin/zoom-js/zoom.js', async: true },

    // 演讲备注
    { src: 'plugin/notes/notes.js', async: true },

    // 数学公式
    { src: 'plugin/math/math.js', async: true }
  ]
});
```
自定义库也可以使用该方式加载。
依赖项属性：
- **src**: 脚本路径
- **async**: [可选] 异步，是否允许 reveal.js 执行后再加载脚本，默认值为 false
- **callback**: [可选] 回调函数，脚本加载完成后执行
- **condition**: [可选] 条件函数，返回 true 时才会加载脚本

要使用该方式来加载依赖项，需在引入 reveal.js 之前引入 [head.js](http://headjs.com/) *(提供加载脚本功能的库)*。

## Ready事件

reveal.js 在所有非异步依赖加载完成，准备播放时，会广播 'ready' 事件。
可调用 `Reveal.isReady()` 函数来检查 reveal.js 是否已准备完成。

```javascript
Reveal.addEventListener( 'ready', function( event ) {
  // event.currentSlide, event.indexh, event.indexv
} );
```

reveal.js 准备完成时会给 `.reveal` 元素增加 `.ready` 类，也可以此来判断是否已准备完成。

## 自动播放

演示文稿可以设置为自动播放，只需告诉框架自动切换的时间间隔（毫秒）：

```javascript
// 每 5 秒自动切换下一张幻灯片
Reveal.configure({
  autoSlide: 5000
});
```

在手动切换分段或幻灯片后会暂停自动播放，也可以按 a 键来暂停或恢复自动播放。
设置 ```autoSlideStoppable: false``` 后，用户操作则不会打断自动播放。

也可以通过 ```data-autoslide``` 属性来给个别幻灯片或分段重新设置时间间隔:

```html
<section data-autoslide="2000">
  <p class="fragment"> 2 秒后第一个分段会自动显示 </p>
  <p class="fragment" data-autoslide="10000"> 10 秒后下一个分段会自动显示 </p>
  <p class="fragment"> 2 秒后会自动切换到下一张幻灯片 </p>
</section>
```

通过设置 ```autoSlideMethod``` 指定自动播放的方式，如设置为 ```Reveal.navigateRight```，则自动播放时纵向幻灯片只会播放主幻灯片，其它纵向幻灯片会被忽略。

自动播放被暂停和恢复时，会广播 ```autoslidepaused``` 和 ```autoslideresumed``` 事件。

## 自定义快捷键

如果不喜欢默认的快捷键，可通过 ```keyboard``` 配置项来自定义：

```javascript
Reveal.configure({
  keyboard: {
    13: 'next', // 按 ENTER 键切换到下一个分段或幻灯片
    27: function() {}, // 按 ESC 键时触发自定义行为
    32: null // 按 SPACE 时不做任何处理（可用于禁用 reveal.js 的默认快捷键）
  }
});
```

## 触屏操作

在触屏设备上可以通过滑动来操作幻灯片，水平滑动切换横向幻灯片，垂直滑动切换纵向幻灯片。
设置 ```touch: false`` 可禁用触屏操作。

如果幻灯片内容本身带有滑动操作（比如滚动内容），需要给元素添加 `data-prevent-swipe` 属性来阻止默认的滑动行为。


## 延迟加载

当演示文稿中带有大量的多媒体或 iframe 内容时，延迟加载就显得尤为重要，即只提前加载当前幻灯片最近的几张幻灯片中的内容。
预加载的幻灯片数量由 `viewDistance` 配置项决定。

延迟加载支持 image、video、audio 和 iframe 元素，只需把 "src" 属性改为 "data-src" 即可。
幻灯片中延迟加载的 iframe，会在切换到其它幻灯片时自动卸载。

```html
<section>
  <img data-src="图片.png">
  <iframe data-src="http://hakim.se"></iframe>
  <video>
    <source data-src="视频.webm" type="video/webm" />
    <source data-src="视频.mp4" type="video/mp4" />
  </video>
</section>
```
## API中文

``Reveal`` 对象提供了一套控制演示进度和管理演示状态的 JavaScript API：

```javascript
// 演示进度控制
Reveal.slide( indexh, indexv, indexf );
Reveal.left();
Reveal.right();
Reveal.up();
Reveal.down();
Reveal.prev();
Reveal.next();
Reveal.prevFragment();
Reveal.nextFragment();

// 打乱幻灯片顺序
Reveal.shuffle();

// 显示快捷键帮助面板
Reveal.showHelp();

// 管理演示文稿状态，传入 true/false 对应 on/off 状态
Reveal.toggleOverview();
Reveal.togglePause();
Reveal.toggleAutoSlide();

// 改变配置项设置
Reveal.configure({ controls: true });

// 获取当前的配置项设置
Reveal.getConfig();

// 获取当前演示文稿的缩放比例
Reveal.getScale();

// 获取上一个/当前幻灯片节点
Reveal.getPreviousSlide();
Reveal.getCurrentSlide();

// 获取当前演示状态
// h-横向幻灯片索引，v-纵向幻灯片索引，f-分段索引
Reveal.getIndices(); // { h: 0, v: 0, f: 0 }
// 获取当前演示进度
Reveal.getProgress(); // 0-1
// 获取幻灯片总数（包括横向幻灯片和纵向幻灯片）
Reveal.getTotalSlides();

// 获取当前幻灯片的演讲备注
Reveal.getSlideNotes();

// 状态检查
Reveal.isFirstSlide();
Reveal.isLastSlide();
Reveal.isOverview();
Reveal.isPaused();
Reveal.isAutoSliding();
```
### 幻灯片切换事件

幻灯片切换时会广播 'slidechanged' 事件。event 对象保存了当前幻灯片的横向索引和纵向索引、上一张幻灯片和当前幻灯片的节点引用。

部分第三方库，如 MathJax（见 [#226](https://github.com/hellobugme/reveal.js/issues/226#issuecomment-10261609)），会受到幻灯片变形和显示状态的影响，此时可以尝试在该事件的回调函数中重新计算和渲染来进行修复。

```javascript
Reveal.addEventListener( 'slidechanged', function( event ) {
  // event.previousSlide, event.currentSlide, event.indexh, event.indexv
} );
```

### 演示状态

`getState` 方法可以获取演示文稿的当前状态，使用这个快照，可以非常方便地返回到记录的演示进度。

```javascript
// 切换到幻灯片 1
Reveal.slide( 1 );

// 获取当前状态
var state = Reveal.getState();

// 切换到幻灯片 3
Reveal.slide( 3 );

// 切回幻灯片 1
Reveal.setState( state );
```
### 幻灯片状态

如果给幻灯片 ``<section>`` 设置了 ``data-state="somestate"`` 属性，则当播放到该幻灯片时，"somestate" 将会出现在文档元素 ``<html>`` 的类里，可以很方便地给各个幻灯片设置不同的页面样式。

此外，还可以在 JavaScript 中侦听这个状态：

```javascript
Reveal.addEventListener( 'somestate', function() {
  // TODO: somestate 出现了，做些啥吧
}, false );
```

### 幻灯片背景

```<section>``` 元素的 ```data-background``` 属性可以设置一个覆盖整个幻灯片的背景。
支持 4 种类型的背景：颜色，图像，视频和 iframe。

#### 颜色背景
支持所有 CSS 颜色格式，如 rgba() 或 hsl()。
```html
<section data-background-color="#ff0000">
  <h2> 颜色背景 </h2>
</section>
```
#### 图像背景
背景图像默认会自动调整大小以覆盖整个幻灯片，可设置的选项：

| 属性                         | 默认值     | 说明 |
| :--------------------------- | :--------- | :---------- |
| data-background-image        |            | 图片 URL（GIF 动图会在幻灯片显示时重新播放） |
| data-background-size         | cover      | 见 MDN [background-size](https://developer.mozilla.org/docs/Web/CSS/background-size) |
| data-background-position     | center     | 见 MDN [background-position](https://developer.mozilla.org/docs/Web/CSS/background-position) |
| data-background-repeat       | no-repeat  | 见 MDN [background-repeat](https://developer.mozilla.org/docs/Web/CSS/background-repeat) |

```html
<section data-background-image="http://example.com/image.png">
  <h2> 图像背景 </h2>
</section>
<section data-background-image="http://example.com/image.png" data-background-size="100px" data-background-repeat="repeat">
  <h2> 背景图像尺寸为 100 像素，且平铺模式为重复 </h2>
</section>
```

#### 视频背景

在幻灯片后面自动播放一个撑满页面的视频。

| 属性                         | 默认值  | 说明 |
| :--------------------------- | :------ | :---------- |
| data-background-video        |         | 单个视频地址，或由半角逗号 ',' 分隔的视频地址列表。 |
| data-background-video-loop   | false   | 是否循环播放 |
| data-background-video-muted  | false   | 是否静音 |

```html
<section data-background-video="https://s3.amazonaws.com/static.slid.es/site/homepage/v1/homepage-video-editor.mp4,https://s3.amazonaws.com/static.slid.es/site/homepage/v1/homepage-video-editor.webm" data-background-video-loop data-background-video-muted>
  <h2> 视频背景 </h2>
</section>
```

#### Iframe 背景

嵌入一个网页作为背景，该网页位于幻灯片后面的背景层，无法进行交互。
```html
<section data-background-iframe="https://slides.com">
  <h2> Iframe </h2>
</section>
```

#### 背景切换过渡效果

背景切换的默认过渡效果为 fade（渐变），可在初始化 ```Reveal.initialize()``` 时传入 ```backgroundTransition``` 配置项来修改，也可给 `<section>` 添加 ```data-background-transition``` 属性来给个别幻灯片单独设置。

#### 视差背景

要使用视差滚动背景，需要在初始化 reveal.js 时设置下面的前两个配置项（后两个为可选项）。

```javascript
Reveal.initialize({

    // 视差背景图
    parallaxBackgroundImage: '', // 示例："'https://s3.amazonaws.com/hakim-static/reveal-js/reveal-parallax-1.jpg'"

    // 视察背景图尺寸
    parallaxBackgroundSize: '', // CSS 写法，示例："2100px 900px"（目前只支持像素值，不支持 % 和 auto）

    // 相邻两张幻灯片间，视差背景移动的像素值
    // - 如果不设置则自动计算
    // - 当设置为 0 时，则禁止视差动画
    parallaxBackgroundHorizontal: 200,
    parallaxBackgroundVertical: 50

});
```

视差背景图尺寸必须大于幻灯片尺寸，否则切换幻灯片时无法滚动。[查看示例](http://lab.hakim.se/reveal-js/?parallaxBackgroundImage=https%3A%2F%2Fs3.amazonaws.com%2Fhakim-static%2Freveal-js%2Freveal-parallax-1.jpg&parallaxBackgroundSize=2100px%20900px)

### 切换过渡效果
幻灯片的切换过渡效果，默认使用配置项 ```transition``` 设置的值，可通过 ```data-transition``` 属性来给个别幻灯片单独指定过渡效果：

```html
<section data-transition="zoom">
  <h2> 该幻灯片不使用全局的切换过渡效果，而是单独指定的缩放！ </h2>
</section>

<section data-transition-speed="fast">
  <h2> 可供选择的切换过渡速度有：default-中速、fast-快速、slow-慢速！ </h2>
</section>
```

甚至可以给同一张幻灯片指定不同的切入和切出过渡效果：

```html
<section data-transition="slide">
    没时间解释了快上车……
</section>
<section data-transition="slide">
    继续前进……
</section>
<section data-transition="slide-in fade-out">
    到站停车。
</section>
<section data-transition="fade-in slide-out">
    （乘客上车和下车）
</section>
<section data-transition="slide">
    重新上路。
</section>
```

### 内部跳转

幻灯片间的跳转十分简单，下面第一个例子指定的是目标幻灯片的索引，第二个例子指定的是目标幻灯片的 ID 属性（```<section id="some-slide">```）：

```html
<a href="#/2/1"> 跳转到第 3 个横向幻灯片的第 2 个纵向幻灯片 </a>
<a href="#/some-slide"> 跳转到 ID 为 some-slide 的幻灯片 </a>
```

也可以给元素添加下面这些类，来指定一个相对地址，类似于 reveal.js 的控制面板。
如果指定的是一个有效的跳转地址，元素会自动附加 ```enabled``` 类。

```html
<a href="#" class="navigate-left">
<a href="#" class="navigate-right">
<a href="#" class="navigate-up">
<a href="#" class="navigate-down">
<a href="#" class="navigate-prev"> <!-- 上一张纵向幻灯片或横向幻灯片 -->
<a href="#" class="navigate-next"> <!-- 下一张纵向幻灯片或横向幻灯片 -->
```

### 片段

分段可用于强调幻灯片中的个别元素。演示文稿向前播放时，所有带有 ```fragment``` 类的元素，会在切换下个幻灯片之前逐个触发。[查看示例](http://lab.hakim.se/reveal-js/#/fragments)

分段默认是初始隐藏，播放时渐显出现，可通过给分段追加类来修改这个效果：

```html
<section>
  <p class="fragment grow"> 放大：初始可见，播放时放大 </p>
  <p class="fragment shrink"> 缩小：初始可见，播放时缩小 </p>
  <p class="fragment fade-out"> 渐隐消失：初始可见，播放时渐隐消失 </p>
  <p class="fragment fade-up"> 渐显上升：初始隐藏，播放时渐显上升出现（down、left、right 类似） </p>
  <p class="fragment current-visible"> 显示一次：初始隐藏，播放时出现，继续播放则消失 </p>
  <p class="fragment highlight-current-blue"> 高亮蓝一次：初始可见，播放时变蓝，继续播放则恢复颜色 </p>
  <p class="fragment highlight-red"> 高亮红：初始可见，播放时变红 </p>
  <p class="fragment highlight-green"> 高亮绿：初始可见，播放时变绿 </p>
  <p class="fragment highlight-blue"> 高亮蓝：初始可见，播放时变蓝 </p>
</section>
```

嵌套分段会对包裹的内容逐个触发，在下面的例子中，播放时文本会先渐显出现，继续播放则文本渐隐消失。

```html
<section>
  <span class="fragment fade-in">
    <span class="fragment fade-out"> 我将渐显出现，然后渐隐消失 </span>
  </span>
</section>
```

分段的播放顺序，可以通过 ```data-fragment-index``` 属性来控制。

```html
<section>
  <p class="fragment" data-fragment-index="3"> 最后播放 </p>
  <p class="fragment" data-fragment-index="1"> 最先播放 </p>
  <p class="fragment" data-fragment-index="2"> 第二个播放 </p>
</section>
```

### 片段事件

任意分段在出现和隐藏时，reveal.js 都会广播事件。

部分第三方库，如 MathJax（见 #505），会受到初始隐藏的分段元素的影响，此时可以尝试在这些事件的回调函数中重新计算和渲染来进行修复。

```javascript
Reveal.addEventListener( 'fragmentshown', function( event ) {
  // event.fragment = 分段元素节点
} );
Reveal.addEventListener( 'fragmenthidden', function( event ) {
  // event.fragment = 分段元素节点
} );
```

### 代码语法高亮

Reveal 自带代码语法高亮插件 [highlight.js](https://highlightjs.org/)（需引入该依赖项）。
在下面的例子中， clojure 代码会自动语法高亮，指定 `data-trim` 属性可以自动删除多余空格。
HTML 默认会自动转义，要避免转义（如例子中的 `<mark>` 标签要显示出来），可以给 `<code>` 元素追加 `data-noescape` 属性。

```html
<section>
  <pre><code data-trim data-noescape>
(def lazy-fib
  (concat
   [0 1]
   <mark>((fn rfib [a b]</mark>
        (lazy-cons (+ a b) (rfib b (+ a b)))) 0 1)))
  </code></pre>
</section>
```

### 幻灯片页码
如果想显示幻灯片页码，可以设置 ```slideNumber``` 配置项。

```javascript
// 使用默认格式显示幻灯片页码
Reveal.configure({ slideNumber: true });

// 可供选择的幻灯片页码格式：
//  "h.v":  当前横向幻灯片页码 . 当前纵向幻灯片页码 (默认)
//  "h/v":  当前横向幻灯片页码 / 当前纵向幻灯片页码
//    "c":  当前幻灯片页码（包括横向幻灯片和纵向幻灯片）
//  "c/t":  当前幻灯片页码 / 幻灯片总数
Reveal.configure({ slideNumber: 'c/t' });

```

### 概览模式

按 "Esc" 或 "o" 键可以打开或关闭概览模式。在概览模式中，你仍然可以在幻灯片间切换，就好像位于演示文稿的上空，操作平铺开来的幻灯片。
与概览模式相关的 API：

```javascript
Reveal.addEventListener( 'overviewshown', function( event ) { /* ... */ } );
Reveal.addEventListener( 'overviewhidden', function( event ) { /* ... */ } );

// 通过代码打开或关闭概览模式
Reveal.toggleOverview();
```

### 全屏模式
按 »F« 键可以让演示文稿进入全屏模式，按 »ESC« 键退出全屏模式。


### 嵌入媒体
嵌入的 HTML5 `<video>`/`<audio>` 和 YouTube iframe，会在幻灯片切出时自动暂停播放，通过给元素添加 `data-ignore` 属性可以禁止该行为。

给媒体元素添加 `data-autoplay` 属性，则在幻灯片显示时媒体将自动播放：

```html
<video data-autoplay src="http://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4"></video>
```

此外，框架会自动发送两条消息（见 [发送消息](https://developer.mozilla.org/en-US/docs/Web/API/Window.postMessage)）给所有的 iframe。包含 iframe 的幻灯片，显示时会给其内部所有的 iframe 发送 ```slide:start```消息，隐藏时会发送 ```slide:stop``` 消息。


### 拉伸元素

有时我们希望元素（如图像或者视频）可以自动拉伸，尽可能多的占用幻灯片的空间，这时可以给元素添加 ```.stretch``` 类：

```html
<section>
  <h2> 这个视频将占用幻灯片的所有剩余空间 </h2>
    <video class="stretch" src="http://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4"></video>
</section>
```

限制：

- 只能用于幻灯片的直接子元素
- 每个幻灯片最多只能设置 1 个子元素


### 通信 API
框架自带一个发送消息 API ```postMessage```，可用于内嵌的演示文稿和父窗口之间的通信。
下面的例子展示了如何让指定窗口中的 reveal.js 实例切换到幻灯片 2：

```javascript
<window>.postMessage( JSON.stringify({ method: 'slide', args: [ 2 ] }), '*' );
```

---
**译者注**
示例可参考 [icewind1991](https://github.com/icewind1991/reveal) 的 [plugin/postmessage](https://github.com/icewind1991/reveal/blob/master/js/public/plugin/postmessage/example.html)。
reveal.js 已自带该特性，无需额外引入 postmessage.js 插件。
```html
<html>
    <body>
        <iframe id="reveal" src="../../index.html" style="border: 0;" width="500" height="500"></iframe>
        <div>
            <input id="back" type="button" value="后退"/>
            <input id="ahead" type="button" value="前进"/>
            <input id="slideto" type="button" value="切换到 2-2"/>
        </div>
        <script>
            (function (){
                var back = document.getElementById( 'back' ),
                    ahead = document.getElementById( 'ahead' ),
                    slideto = document.getElementById( 'slideto' ),
                    reveal =  window.frames[0];
                back.addEventListener( 'click', function () {
                    reveal.postMessage( JSON.stringify({method: 'prev', args: []}), '*' );
                }, false );
                ahead.addEventListener( 'click', function (){
                    reveal.postMessage( JSON.stringify({method: 'next', args: []}), '*' );
                }, false );
                slideto.addEventListener( 'click', function (){
                    reveal.postMessage( JSON.stringify({method: 'slide', args: [2,2]}), '*' );
                }, false );
            }());
        </script>
    </body>
</html>
```
---

reveal.js 在 iframe 中运行时，可选择是否将其所有事件冒泡给父窗口。冒泡的事件对象为一个 JSON 字符串，保存了 3 个字段：namespace-命名空间、eventName-事件名、state-状态。
下面的例子展示了父窗口如何向 reveal 订阅事件：

```javascript
window.addEventListener( 'message', function( event ) {
  var data = JSON.parse( event.data );
  if( data.namespace === 'reveal' && data.eventName ==='slidechanged' ) {
    // 幻灯片切换，可访问 data.state 来查看幻灯片页码
  }
} );
```

跨窗口消息传递可通过配置项来打开或关闭。

```javascript
Reveal.initialize({
  ...,

    // 暴露 postMessage API
  postMessage: true,

    // 将演示文稿的所有事件冒泡给父窗口
  postMessageEvents: false
});
```

## 导出 PDF

演示文稿可以通过一个特殊的打印样式来导出 PDF。该特性需要使用 [Google Chrome](http://google.com/chrome) 或 [Chromium](https://www.chromium.org/Home)、且运行于 web 服务器上时，可以导出为 PDF。
这是一个演示文稿导出 PDF 并上传到 SlideShare 的例子：http://www.slideshare.net/hakimel/revealjs-300。

### 页面尺寸
导出的 PDF 尺寸由 [演示文稿尺寸](#演示文稿尺寸) 决定，如果幻灯片太高无法一页展示完，则会切分为多页，可通过 `pdfMaxPagesPerSlide` 配置项设置每张幻灯片最多可被切分为几数，如 `Reveal.configure({ pdfMaxPagesPerSlide: 1 })` 可确保幻灯片不会被切分。

### 打印样式
想要启用演示文稿的打印功能，需要加载一个用于打印的特殊样式 [/css/print/pdf.css](https://github.com/hakimel/reveal.js/blob/master/css/print/pdf.css)，默认的 index.html 文件已包含该逻辑，只要演示文稿的链接中带有 `print-pdf` 参数，就会自动加载。如果使用的是其它的 HTML 模板，可以在 HEAD 中插入以下代码：

```html
<script>
  var link = document.createElement( 'link' );
  link.rel = 'stylesheet';
  link.type = 'text/css';
  link.href = window.location.search.match( /print-pdf/gi ) ? 'css/print/pdf.css' : 'css/print/paper.css';
  document.getElementsByTagName( 'head' )[0].appendChild( link );
</script>
```
### 步骤

1. 给演示文稿的 URL 加上 `print-pdf` 参数，如：http://localhost:8000/?print-pdf#/ ，可以尝试这个例子 [lab.hakim.se/reveal-js?print-pdf](http://lab.hakim.se/reveal-js?print-pdf)。
2. 打开浏览器的打印面板 (CTRL/CMD+P)。
3. **Destination（目标打印机）** 修改为 **Save as PDF（另存为 PDF）**。
4. **Layout（布局）** 修改为 **Landscape（横向）**。
5. **Margins（边距）** 修改为 **None（无）**。
6. 启用选项 **Background graphics（背景图形）**。
7. 点击 **Save（保存）**

![谷歌浏览器打印设置](https://s3.amazonaws.com/hakim-static/reveal-js/pdf-print-settings-2.png)

也可使用 [decktape](https://github.com/astefanutti/decktape)（一个将 HTML5 演示文稿导出为高质量 PDF 的框架）项目代替。

## 主题

框架带有几个不同的主题：

- black：黑色背景，白色文本，蓝色链接（默认主题）
- white：白色背景，黑色文本，蓝色链接
- league：灰色背景，白色文本，蓝色链接（reveal.js 3.0.0 之前版本的默认主题）
- beige：米黄色背景，暗色（#333）文本，棕色链接
- sky：蓝色背景，暗色文本，蓝色链接
- night：黑色背景，亮色（#eee）文本，橙色链接
- serif：咖啡色背景，灰色文本，褐色链接
- simple：白色背景，黑色文本，蓝色链接
- solarized：奶油色背景，深绿色文本，蓝色链接

每个主题都是一个单独的样式文件，修改主题只需把 index.html 的主题样式中的 **black** 替换为想要的主题名即可：

```html
<link rel="stylesheet" href="css/theme/black.css" id="theme">
```

如果要增加自定义主题，请参考：[/css/theme/README.md](https://github.com/hellobugme/reveal.js/blob/master/css/theme/README.md)。

## 演讲备注

reveal.js 自带演讲备注插件，可以在一个单独的浏览器窗口中为每张幻灯片提供备注，同时预览下一张幻灯片。
按 's' 键来打开备注窗口。

演讲计时器会在备注窗口打开时启动，点击时间可以重置为 00:00:00。

给幻灯片追加一个 ```<aside>``` 元素来添加备注，如果想用 Markdown 编写备注内容，可以给 aside 元素添加 ```data-markdown``` 属性。

也可以通过幻灯片的 `data-notes` 属性来添加简单的备注，如 `<section data-notes="一些简单的备注"></section>`。

如果是在本地打开演示文稿，想要使用演讲备注，需要 reveal.js [运行于一个本地 web 服务器](#完整安装).

```html
<section>
  <h2> 我是幻灯片 </h2>

  <aside class="notes">
        大家好，我是这张幻灯片的备注，在演示文稿上是看不到，不过可以按 's' 键打开备注窗口来找我哦，么么哒~
  </aside>
</section>
```

对于幻灯片引入的外部 Markdown 文件，可以在指定的分隔符后面添加备注：

```html
<section data-markdown="example.md" data-separator="^\n\n\n" data-separator-vertical="^\n\n" data-separator-notes="^Note:"></section>

# 标题
## 子标题

幻灯片内容……

Note:
只会在备注窗口显示的内容……
```
### 分享和打印演讲备注

备注只对演讲者可见，如果想让其他人也能看到，可以在初始化 reveal.js 时，把 `showNotes` 配置项设为 `true`，则备注会显示在演示文稿的底部。

如果启用了 `showNotes`，在 [导出 PDF](#导出-pdf) 时也会包含备注。
备注默认打印在一个半透明的浮窗中，覆盖于幻灯片底部，如果想在该幻灯片后面单独新建一页打印备注，可以把 `showNotes` 设置为 `"separate-page"`。

### 服务器端演讲备注

基于 Node.js 的演讲备注插件，让你可以在其它设备上运行你正在控制的演讲备注，就像客户端演讲备注的副本，会相互同步操作。
需要引入以下依赖项：

```javascript
Reveal.initialize({
  ...

  dependencies: [
    { src: 'socket.io/socket.io.js', async: true },
    { src: 'plugin/notes-server/client.js', async: true }
  ]
});
```

然后：

1. 安装 [Node.js](http://nodejs.org/)（4.0.0 或更新版本）
2. 执行 ```npm install```
3. 执行 ```node plugin/notes-server```

### 多路复用

多路复用插件让你的听众可以在自己的手机、平板电脑或笔记本电脑上观看你正在控制的演示文稿，当你操作主演示文稿时，所有的客户端演示文稿将实时同步更新。查看示例：[https://reveal-js-multiplex-ccjbegmaii.now.sh/](https://reveal-js-multiplex-ccjbegmaii.now.sh/)。

多路复用插件需要以下 3 个部分：

1. 可以控制的主演示文稿
2. 同步更新的客户端演示文稿
3. 用于广播主演示文稿事件给客户端演示文稿的 Socket.io 服务器

更多说明：

### 主演示文稿

存放于只有演讲者可以访问（最好）的静态文件服务器（存放在演讲者的电脑上即可，在演讲者的电脑上运行主演示文稿会更加保险，即使会场断网，也不会打断演示。）。
在主演示文稿目录中执行以下命令：

1. ```npm install node-static```
2. ```static```

如果想在主演示文稿上使用演讲备注，需要先配置演讲备注插件，然后在主演示文稿目录中执行 ```node plugin/notes-server``` 命令。

运行演讲备注/静态文件服务器，作为主控端连接 socket.io 服务器。

通过 ```http://localhost:1947``` 访问主演示文稿。

配置示例：
```javascript
Reveal.initialize({
  // 其它配置项……

  multiplex: {
    // 示例值，使用时请自己生成，具体参考 socket.io 说明。
    secret: '13652805320794272084', // 从 socket.io 服务器获得，允许演示文稿可以被控制
    id: '1ea875674b17ca76', // 从 socket.io 服务器获得
    url: 'https://reveal-js-multiplex-ccjbegmaii.now.sh' // socket.io 服务器地址
  },

  // 依赖项
  dependencies: [
    { src: '//cdn.socket.io/socket.io-1.3.5.js', async: true },
    { src: 'plugin/multiplex/master.js', async: true },

    // 演讲备注
    { src: 'plugin/notes-server/client.js', async: true }

    // 其它依赖项……
  ]
});
```

### 客户端演示文稿

存放于可以公开访问的静态文件服务器，如 GitHub Pages、Amazon S3、Dreamhost、Akamai 等。

使用下面的配置，当听众通过 ```http://example.com/path/to/presentation/client/index.html``` 访问演示文稿时，将作为被控端连接 socket.io 服务器。

配置示例：
```javascript
Reveal.initialize({
  // 其它配置项……

  multiplex: {
    // 示例值，使用时请自己生成，具体参考 socket.io 说明。
    secret: null, // 设置为 null，演示文稿将不能被控制，而是同步 socket.io 服务器上相同 id 的主演示文稿的操作
    id: '1ea875674b17ca76', // 从 socket.io 服务器获得
    url: 'https://reveal-js-multiplex-ccjbegmaii.now.sh' // socket.io 服务器地址
  },

  // 依赖项
  dependencies: [
    { src: '//cdn.socket.io/socket.io-1.3.5.js', async: true },
    { src: 'plugin/multiplex/client.js', async: true }

    // 其它依赖项……
  ]
});
```

## _MathJax

如果想在演示文稿中更好的显示数学公式，可以使用基于 [MathJax](http://www.mathjax.org/) 库封装的这个小插件。

插件默认使用 [LaTeX](http://en.wikipedia.org/wiki/LaTeX) 格式（一种基于ΤΕΧ的排版系统），可通过 ```math``` 配置项来修改。

MathJax 是从远程服务器加载的，如果想离线使用，需自行下载该库，并修改 ```mathjax``` 配置项。

下面是 MathJax 的配置示例（使用默认配置时，```math``` 配置项可省略）：

```js
Reveal.initialize({
  // 其它配置项……

  math: {
    mathjax: 'https://cdn.mathjax.org/mathjax/latest/MathJax.js',
    config: 'TeX-AMS_HTML-full'  // 参考 http://docs.mathjax.org/en/latest/config-files.html
  },

  dependencies: [
    { src: 'plugin/math/math.js', async: true }
  ]

});
```

如果想了解 MathJax 的 [HTTPS 传输](http://docs.mathjax.org/en/latest/start.html#secure-access-to-the-cdn)方式，或为了稳定性需要使用[特定版本](http://docs.mathjax.org/en/latest/configuration.html#loading-mathjax-from-the-cdn)，请参考 MathJax 的说明文档。


## 工程安装

**基础安装** 适用于创建简单的演讲文稿，**完整安装** 可以使用 reveal.js 的所有特性和插件（如演讲备注）。

### 基础安装

reveal.js 基础功能的安装十分简单，只需下载框架包，然后直接在浏览器中打开 index.html 文件即可。

1. 在 <https://github.com/hakimel/reveal.js/releases> 上下载 reveal.js 的最新版本

2. 解压缩，然后将 index.html 里的示例内容修改为自己的内容

3. 在浏览器中打开 index.html


### 完整安装

部分 reveal.js 特性（如 Markdown 和演讲备注）需要演示文稿运行于一个本地 web 服务器。
按照下面的步骤，可以创建一个完整的 reveal.js 开发和运行环境：

1. 安装 [Node.js](http://nodejs.org/) （4.0.0 或更新版本）

1. 克隆 reveal.js 仓库
   ```sh
   $ git clone https://github.com/palmerye/demos-Reveal.js.git
   ```

1. 进入 reveal.js 目录
   ```sh
   $ cd reveal.js
   ```

1. 安装依赖
   ```sh
   $ npm install
   ```

1. 启动演示文稿并监控文件变更
   ```sh
   $ npm start
   ```

1. 打开 <http://localhost:8000> 查看演示文稿

通过 `npm start -- --port=8001` 指令可修改端口号


### 目录结构
- **css/** 框架样式
- **js/** 框架 JavaScript 
- **plugin/** 用于扩展 reveal.js 的组件
- **lib/** 第三方库（JavaScript、样式、字体）


## 许可

遵循 MIT 开源协议

Copyright (C) 2016 Hakim El Hattab, http://hakim.se

---

# reveal.js EN

> Official Document in English

[![Build Status](https://travis-ci.org/hakimel/reveal.js.svg?branch=master)](https://travis-ci.org/hakimel/reveal.js) <a href="https://slides.com?ref=github"><img src="https://s3.amazonaws.com/static.slid.es/images/slides-github-banner-320x40.png?1" alt="Slides" width="160" height="20"></a>

A framework for easily creating beautiful presentations using HTML. [Check out the live demo](http://lab.hakim.se/reveal-js/).

reveal.js comes with a broad range of features including [nested slides](https://github.com/hakimel/reveal.js#markup), [Markdown contents](https://github.com/hakimel/reveal.js#markdown), [PDF export](https://github.com/hakimel/reveal.js#pdf-export), [speaker notes](https://github.com/hakimel/reveal.js#speaker-notes) and a [JavaScript API](https://github.com/hakimel/reveal.js#api). There's also a fully featured visual editor and platform for sharing reveal.js presentations at [slides.com](https://slides.com?ref=github).

## Table of contents
- [Online Editor](#online-editor)
- [Instructions](#instructions)
  - [Markup](#markup)
  - [Markdown](#markdown)
  - [Element Attributes](#element-attributes)
  - [Slide Attributes](#slide-attributes)
- [Configuration](#configuration)
- [Presentation Size](#presentation-size)
- [Dependencies](#dependencies)
- [Ready Event](#ready-event)
- [Auto-sliding](#auto-sliding)
- [Keyboard Bindings](#keyboard-bindings)
- [Touch Navigation](#touch-navigation)
- [Lazy Loading](#lazy-loading)
- [API](#api)
  - [Slide Changed Event](#slide-changed-event)
  - [Presentation State](#presentation-state)
  - [Slide States](#slide-states)
  - [Slide Backgrounds](#slide-backgrounds)
  - [Parallax Background](#parallax-background)
  - [Slide Transitions](#slide-transitions)
  - [Internal links](#internal-links)
  - [Fragments](#fragments)
  - [Fragment events](#fragment-events)
  - [Code syntax highlighting](#code-syntax-highlighting)
  - [Slide number](#slide-number)
  - [Overview mode](#overview-mode)
  - [Fullscreen mode](#fullscreen-mode)
  - [Embedded media](#embedded-media)
  - [Stretching elements](#stretching-elements)
  - [postMessage API](#postmessage-api)
- [PDF Export](#pdf-export)
- [Theming](#theming)
- [Speaker Notes](#speaker-notes)
  - [Share and Print Speaker Notes](#share-and-print-speaker-notes)
  - [Server Side Speaker Notes](#server-side-speaker-notes)
- [Multiplexing](#multiplexing)
  - [Master presentation](#master-presentation)
  - [Client presentation](#client-presentation)
  - [Socket.io server](#socketio-server)
- [MathJax](#mathjax)
- [Installation](#installation)
  - [Basic setup](#basic-setup)
  - [Full setup](#full-setup)
  - [Folder Structure](#folder-structure)
- [License](#license)

#### More reading
- [Changelog](https://github.com/hakimel/reveal.js/releases): Up-to-date version history.
- [Examples](https://github.com/hakimel/reveal.js/wiki/Example-Presentations): Presentations created with reveal.js, add your own!
- [Browser Support](https://github.com/hakimel/reveal.js/wiki/Browser-Support): Explanation of browser support and fallbacks.
- [Plugins](https://github.com/hakimel/reveal.js/wiki/Plugins,-Tools-and-Hardware): A list of plugins that can be used to extend reveal.js.

## Online Editor

Presentations are written using HTML or Markdown but there's also an online editor for those of you who prefer a graphical interface. Give it a try at [https://slides.com](https://slides.com?ref=github).


## Instructions

### Markup

Here's a barebones example of a fully working reveal.js presentation:
```html
<html>
   <head>
      <link rel="stylesheet" href="css/reveal.css">
      <link rel="stylesheet" href="css/theme/white.css">
   </head>
   <body>
      <div class="reveal">
         <div class="slides">
            <section>Slide 1</section>
            <section>Slide 2</section>
         </div>
      </div>
      <script src="js/reveal.js"></script>
      <script>
         Reveal.initialize();
      </script>
   </body>
</html>
```

The presentation markup hierarchy needs to be `.reveal > .slides > section` where the `section` represents one slide and can be repeated indefinitely. If you place multiple `section` elements inside of another `section` they will be shown as vertical slides. The first of the vertical slides is the "root" of the others (at the top), and will be included in the horizontal sequence. For example:

```html
<div class="reveal">
   <div class="slides">
      <section>Single Horizontal Slide</section>
      <section>
         <section>Vertical Slide 1</section>
         <section>Vertical Slide 2</section>
      </section>
   </div>
</div>
```

### Markdown

It's possible to write your slides using Markdown. To enable Markdown, add the `data-markdown` attribute to your `<section>` elements and wrap the contents in a `<script type="text/template">` like the example below.

This is based on [data-markdown](https://gist.github.com/1343518) from [Paul Irish](https://github.com/paulirish) modified to use [marked](https://github.com/chjj/marked) to support [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown). Sensitive to indentation (avoid mixing tabs and spaces) and line breaks (avoid consecutive breaks).

```html
<section data-markdown>
   <script type="text/template">
      ## Page title

      A paragraph with some text and a [link](http://hakim.se).
   </script>
</section>
```

#### External Markdown

You can write your content as a separate file and have reveal.js load it at runtime. Note the separator arguments which determine how slides are delimited in the external file: the `data-separator` attribute defines a regular expression for horizontal slides (defaults to `^\r?\n---\r?\n$`, a newline-bounded horizontal rule)  and `data-separator-vertical` defines vertical slides (disabled by default). The `data-separator-notes` attribute is a regular expression for specifying the beginning of the current slide's speaker notes (defaults to `note:`). The `data-charset` attribute is optional and specifies which charset to use when loading the external file.

When used locally, this feature requires that reveal.js [runs from a local web server](#full-setup).  The following example customises all available options:

```html
<section data-markdown="example.md"  
         data-separator="^\n\n\n"  
         data-separator-vertical="^\n\n"  
         data-separator-notes="^Note:"  
         data-charset="iso-8859-15">
</section>
```

#### Element Attributes

Special syntax (in html comment) is available for adding attributes to Markdown elements. This is useful for fragments, amongst other things.

```html
<section data-markdown>
   <script type="text/template">
      - Item 1 <!-- .element: class="fragment" data-fragment-index="2" -->
      - Item 2 <!-- .element: class="fragment" data-fragment-index="1" -->
   </script>
</section>
```

#### Slide Attributes

Special syntax (in html comment) is available for adding attributes to the slide `<section>` elements generated by your Markdown.

```html
<section data-markdown>
   <script type="text/template">
   <!-- .slide: data-background="#ff0000" -->
      Markdown content
   </script>
</section>
```

#### Configuring *marked*

We use [marked](https://github.com/chjj/marked) to parse Markdown. To customise marked's rendering, you can pass in options when [configuring Reveal](#configuration):

```javascript
Reveal.initialize({
   // Options which are passed into marked
   // See https://github.com/chjj/marked#options-1
   markdown: {
      smartypants: true
   }
});
```

### Configuration

At the end of your page you need to initialize reveal by running the following code. Note that all config values are optional and will default as specified below.

```javascript
Reveal.initialize({

   // Display controls in the bottom right corner
   controls: true,

   // Display a presentation progress bar
   progress: true,

   // Display the page number of the current slide
   slideNumber: false,

   // Push each slide change to the browser history
   history: false,

   // Enable keyboard shortcuts for navigation
   keyboard: true,

   // Enable the slide overview mode
   overview: true,

   // Vertical centering of slides
   center: true,

   // Enables touch navigation on devices with touch input
   touch: true,

   // Loop the presentation
   loop: false,

   // Change the presentation direction to be RTL
   rtl: false,

   // Randomizes the order of slides each time the presentation loads
   shuffle: false,

   // Turns fragments on and off globally
   fragments: true,

   // Flags if the presentation is running in an embedded mode,
   // i.e. contained within a limited portion of the screen
   embedded: false,

   // Flags if we should show a help overlay when the questionmark
   // key is pressed
   help: true,

   // Flags if speaker notes should be visible to all viewers
   showNotes: false,

   // Number of milliseconds between automatically proceeding to the
   // next slide, disabled when set to 0, this value can be overwritten
   // by using a data-autoslide attribute on your slides
   autoSlide: 0,

   // Stop auto-sliding after user input
   autoSlideStoppable: true,

   // Use this method for navigation when auto-sliding
   autoSlideMethod: Reveal.navigateNext,

   // Enable slide navigation via mouse wheel
   mouseWheel: false,

   // Hides the address bar on mobile devices
   hideAddressBar: true,

   // Opens links in an iframe preview overlay
   previewLinks: false,

   // Transition style
   transition: 'slide', // none/fade/slide/convex/concave/zoom

   // Transition speed
   transitionSpeed: 'default', // default/fast/slow

   // Transition style for full page slide backgrounds
   backgroundTransition: 'fade', // none/fade/slide/convex/concave/zoom

   // Number of slides away from the current that are visible
   viewDistance: 3,

   // Parallax background image
   parallaxBackgroundImage: '', // e.g. "'https://s3.amazonaws.com/hakim-static/reveal-js/reveal-parallax-1.jpg'"

   // Parallax background size
   parallaxBackgroundSize: '', // CSS syntax, e.g. "2100px 900px"

   // Number of pixels to move the parallax background per slide
   // - Calculated automatically unless specified
   // - Set to 0 to disable movement along an axis
   parallaxBackgroundHorizontal: null,
   parallaxBackgroundVertical: null

});
```


The configuration can be updated after initialization using the ```configure``` method:

```javascript
// Turn autoSlide off
Reveal.configure({ autoSlide: 0 });

// Start auto-sliding every 5s
Reveal.configure({ autoSlide: 5000 });
```


### Presentation Size

All presentations have a normal size, that is the resolution at which they are authored. The framework will automatically scale presentations uniformly based on this size to ensure that everything fits on any given display or viewport.

See below for a list of configuration options related to sizing, including default values:

```javascript
Reveal.initialize({

   ...

   // The "normal" size of the presentation, aspect ratio will be preserved
   // when the presentation is scaled to fit different resolutions. Can be
   // specified using percentage units.
   width: 960,
   height: 700,

   // Factor of the display size that should remain empty around the content
   margin: 0.1,

   // Bounds for smallest/largest possible scale to apply to content
   minScale: 0.2,
   maxScale: 1.5

});
```

If you wish to disable this behavior and do your own scaling (e.g. using media queries), try these settings:

```javascript
Reveal.initialize({

   ...

   width: "100%",
   height: "100%",
   margin: 0,
   minScale: 1,
   maxScale: 1
});
```

### Dependencies

Reveal.js doesn't _rely_ on any third party scripts to work but a few optional libraries are included by default. These libraries are loaded as dependencies in the order they appear, for example:

```javascript
Reveal.initialize({
   dependencies: [
      // Cross-browser shim that fully implements classList - https://github.com/eligrey/classList.js/
      { src: 'lib/js/classList.js', condition: function() { return !document.body.classList; } },

      // Interpret Markdown in <section> elements
      { src: 'plugin/markdown/marked.js', condition: function() { return !!document.querySelector( '[data-markdown]' ); } },
      { src: 'plugin/markdown/markdown.js', condition: function() { return !!document.querySelector( '[data-markdown]' ); } },

      // Syntax highlight for <code> elements
      { src: 'plugin/highlight/highlight.js', async: true, callback: function() { hljs.initHighlightingOnLoad(); } },

      // Zoom in and out with Alt+click
      { src: 'plugin/zoom-js/zoom.js', async: true },

      // Speaker notes
      { src: 'plugin/notes/notes.js', async: true },

      // MathJax
      { src: 'plugin/math/math.js', async: true }
   ]
});
```

You can add your own extensions using the same syntax. The following properties are available for each dependency object:
- **src**: Path to the script to load
- **async**: [optional] Flags if the script should load after reveal.js has started, defaults to false
- **callback**: [optional] Function to execute when the script has loaded
- **condition**: [optional] Function which must return true for the script to be loaded

To load these dependencies, reveal.js requires [head.js](http://headjs.com/) *(a script loading library)* to be loaded before reveal.js.

### Ready Event

A 'ready' event is fired when reveal.js has loaded all non-async dependencies and is ready to start navigating. To check if reveal.js is already 'ready' you can call `Reveal.isReady()`.

```javascript
Reveal.addEventListener( 'ready', function( event ) {
   // event.currentSlide, event.indexh, event.indexv
} );
```

Note that we also add a `.ready` class to the `.reveal` element so that you can hook into this with CSS.

### Auto-sliding

Presentations can be configured to progress through slides automatically, without any user input. To enable this you will need to tell the framework how many milliseconds it should wait between slides:

```javascript
// Slide every five seconds
Reveal.configure({
  autoSlide: 5000
});
```
When this is turned on a control element will appear that enables users to pause and resume auto-sliding. Alternatively, sliding can be paused or resumed by pressing »a« on the keyboard. Sliding is paused automatically as soon as the user starts navigating. You can disable these controls by specifying ```autoSlideStoppable: false``` in your reveal.js config.

You can also override the slide duration for individual slides and fragments by using the ```data-autoslide``` attribute:

```html
<section data-autoslide="2000">
   <p>After 2 seconds the first fragment will be shown.</p>
   <p class="fragment" data-autoslide="10000">After 10 seconds the next fragment will be shown.</p>
   <p class="fragment">Now, the fragment is displayed for 2 seconds before the next slide is shown.</p>
</section>
```

To override the method used for navigation when auto-sliding, you can specify the ```autoSlideMethod``` setting. To only navigate along the top layer and ignore vertical slides, set this to ```Reveal.navigateRight```.

Whenever the auto-slide mode is resumed or paused the ```autoslideresumed``` and ```autoslidepaused``` events are fired.


### Keyboard Bindings

If you're unhappy with any of the default keyboard bindings you can override them using the ```keyboard``` config option:

```javascript
Reveal.configure({
  keyboard: {
    13: 'next', // go to the next slide when the ENTER key is pressed
    27: function() {}, // do something custom when ESC is pressed
    32: null // don't do anything when SPACE is pressed (i.e. disable a reveal.js default binding)
  }
});
```

### Touch Navigation

You can swipe to navigate through a presentation on any touch-enabled device. Horizontal swipes change between horizontal slides, vertical swipes change between vertical slides. If you wish to disable this you can set the `touch` config option to false when initializing reveal.js.

If there's some part of your content that needs to remain accessible to touch events you'll need to highlight this by adding a `data-prevent-swipe` attribute to the element. One common example where this is useful is elements that need to be scrolled.


### Lazy Loading

When working on presentation with a lot of media or iframe content it's important to load lazily. Lazy loading means that reveal.js will only load content for the few slides nearest to the current slide. The number of slides that are preloaded is determined by the `viewDistance` configuration option.

To enable lazy loading all you need to do is change your "src" attributes to "data-src" as shown below. This is supported for image, video, audio and iframe elements. Lazy loaded iframes will also unload when the containing slide is no longer visible.

```html
<section>
  <img data-src="image.png">
  <iframe data-src="http://hakim.se"></iframe>
  <video>
    <source data-src="video.webm" type="video/webm" />
    <source data-src="video.mp4" type="video/mp4" />
  </video>
</section>
```


### API

The ``Reveal`` object exposes a JavaScript API for controlling navigation and reading state:

```javascript
// Navigation
Reveal.slide( indexh, indexv, indexf );
Reveal.left();
Reveal.right();
Reveal.up();
Reveal.down();
Reveal.prev();
Reveal.next();
Reveal.prevFragment();
Reveal.nextFragment();

// Randomize the order of slides
Reveal.shuffle();

// Shows a help overlay with keyboard shortcuts
Reveal.showHelp();

// Toggle presentation states, optionally pass true/false to force on/off
Reveal.toggleOverview();
Reveal.togglePause();
Reveal.toggleAutoSlide();

// Change a config value at runtime
Reveal.configure({ controls: true });

// Returns the present configuration options
Reveal.getConfig();

// Fetch the current scale of the presentation
Reveal.getScale();

// Retrieves the previous and current slide elements
Reveal.getPreviousSlide();
Reveal.getCurrentSlide();

Reveal.getIndices(); // { h: 0, v: 0 } }
Reveal.getProgress(); // 0-1
Reveal.getTotalSlides();

// Returns the speaker notes for the current slide
Reveal.getSlideNotes();

// State checks
Reveal.isFirstSlide();
Reveal.isLastSlide();
Reveal.isOverview();
Reveal.isPaused();
Reveal.isAutoSliding();
```

### Slide Changed Event

A 'slidechanged' event is fired each time the slide is changed (regardless of state). The event object holds the index values of the current slide as well as a reference to the previous and current slide HTML nodes.

Some libraries, like MathJax (see [#226](https://github.com/hakimel/reveal.js/issues/226#issuecomment-10261609)), get confused by the transforms and display states of slides. Often times, this can be fixed by calling their update or render function from this callback.

```javascript
Reveal.addEventListener( 'slidechanged', function( event ) {
   // event.previousSlide, event.currentSlide, event.indexh, event.indexv
} );
```

### Presentation State

The presentation's current state can be fetched by using the `getState` method. A state object contains all of the information required to put the presentation back as it was when `getState` was first called. Sort of like a snapshot. It's a simple object that can easily be stringified and persisted or sent over the wire.

```javascript
Reveal.slide( 1 );
// we're on slide 1

var state = Reveal.getState();

Reveal.slide( 3 );
// we're on slide 3

Reveal.setState( state );
// we're back on slide 1
```

### Slide States

If you set ``data-state="somestate"`` on a slide ``<section>``, "somestate" will be applied as a class on the document element when that slide is opened. This allows you to apply broad style changes to the page based on the active slide.

Furthermore you can also listen to these changes in state via JavaScript:

```javascript
Reveal.addEventListener( 'somestate', function() {
   // TODO: Sprinkle magic
}, false );
```

### Slide Backgrounds

Slides are contained within a limited portion of the screen by default to allow them to fit any display and scale uniformly. You can apply full page backgrounds outside of the slide area by adding a ```data-background``` attribute to your ```<section>``` elements. Four different types of backgrounds are supported: color, image, video and iframe.

##### Color Backgrounds
All CSS color formats are supported, like rgba() or hsl().
```html
<section data-background-color="#ff0000">
   <h2>Color</h2>
</section>
```

##### Image Backgrounds
By default, background images are resized to cover the full page. Available options:

| Attribute                    | Default    | Description |
| :--------------------------- | :--------- | :---------- |
| data-background-image        |            | URL of the image to show. GIFs restart when the slide opens. |
| data-background-size         | cover      | See [background-size](https://developer.mozilla.org/docs/Web/CSS/background-size) on MDN.  |
| data-background-position     | center     | See [background-position](https://developer.mozilla.org/docs/Web/CSS/background-position) on MDN. |
| data-background-repeat       | no-repeat  | See [background-repeat](https://developer.mozilla.org/docs/Web/CSS/background-repeat) on MDN. |
```html
<section data-background-image="http://example.com/image.png">
   <h2>Image</h2>
</section>
<section data-background-image="http://example.com/image.png" data-background-size="100px" data-background-repeat="repeat">
   <h2>This background image will be sized to 100px and repeated</h2>
</section>
```

##### Video Backgrounds
Automatically plays a full size video behind the slide.

| Attribute                    | Default | Description |
| :--------------------------- | :------ | :---------- |
| data-background-video        |         | A single video source, or a comma separated list of video sources. |
| data-background-video-loop   | false   | Flags if the video should play repeatedly. |
| data-background-video-muted  | false   | Flags if the audio should be muted. |

```html
<section data-background-video="https://s3.amazonaws.com/static.slid.es/site/homepage/v1/homepage-video-editor.mp4,https://s3.amazonaws.com/static.slid.es/site/homepage/v1/homepage-video-editor.webm" data-background-video-loop data-background-video-muted>
   <h2>Video</h2>
</section>
```

##### Iframe Backgrounds
Embeds a web page as a background. Note that since the iframe is in the background layer, behind your slides, it is not possible to interact with the embedded page.
```html
<section data-background-iframe="https://slides.com">
   <h2>Iframe</h2>
</section>
```

##### Background Transitions
Backgrounds transition using a fade animation by default. This can be changed to a linear sliding transition by passing ```backgroundTransition: 'slide'``` to the ```Reveal.initialize()``` call. Alternatively you can set ```data-background-transition``` on any section with a background to override that specific transition.


### Parallax Background

If you want to use a parallax scrolling background, set the first two config properties below when initializing reveal.js (the other two are optional).

```javascript
Reveal.initialize({

   // Parallax background image
   parallaxBackgroundImage: '', // e.g. "https://s3.amazonaws.com/hakim-static/reveal-js/reveal-parallax-1.jpg"

   // Parallax background size
   parallaxBackgroundSize: '', // CSS syntax, e.g. "2100px 900px" - currently only pixels are supported (don't use % or auto)

   // Number of pixels to move the parallax background per slide
   // - Calculated automatically unless specified
   // - Set to 0 to disable movement along an axis
   parallaxBackgroundHorizontal: 200,
   parallaxBackgroundVertical: 50

});
```

Make sure that the background size is much bigger than screen size to allow for some scrolling. [View example](http://lab.hakim.se/reveal-js/?parallaxBackgroundImage=https%3A%2F%2Fs3.amazonaws.com%2Fhakim-static%2Freveal-js%2Freveal-parallax-1.jpg&parallaxBackgroundSize=2100px%20900px).



### Slide Transitions
The global presentation transition is set using the ```transition``` config value. You can override the global transition for a specific slide by using the ```data-transition``` attribute:

```html
<section data-transition="zoom">
   <h2>This slide will override the presentation transition and zoom!</h2>
</section>

<section data-transition-speed="fast">
   <h2>Choose from three transition speeds: default, fast or slow!</h2>
</section>
```

You can also use different in and out transitions for the same slide:

```html
<section data-transition="slide">
    The train goes on …
</section>
<section data-transition="slide">
    and on …
</section>
<section data-transition="slide-in fade-out">
    and stops.
</section>
<section data-transition="fade-in slide-out">
    (Passengers entering and leaving)
</section>
<section data-transition="slide">
    And it starts again.
</section>
```


### Internal links

It's easy to link between slides. The first example below targets the index of another slide whereas the second targets a slide with an ID attribute (```<section id="some-slide">```):

```html
<a href="#/2/2">Link</a>
<a href="#/some-slide">Link</a>
```

You can also add relative navigation links, similar to the built in reveal.js controls, by appending one of the following classes on any element. Note that each element is automatically given an ```enabled``` class when it's a valid navigation route based on the current slide.

```html
<a href="#" class="navigate-left">
<a href="#" class="navigate-right">
<a href="#" class="navigate-up">
<a href="#" class="navigate-down">
<a href="#" class="navigate-prev"> <!-- Previous vertical or horizontal slide -->
<a href="#" class="navigate-next"> <!-- Next vertical or horizontal slide -->
```


### Fragments
Fragments are used to highlight individual elements on a slide. Every element with the class ```fragment``` will be stepped through before moving on to the next slide. Here's an example: http://lab.hakim.se/reveal-js/#/fragments

The default fragment style is to start out invisible and fade in. This style can be changed by appending a different class to the fragment:

```html
<section>
   <p class="fragment grow">grow</p>
   <p class="fragment shrink">shrink</p>
   <p class="fragment fade-out">fade-out</p>
   <p class="fragment fade-up">fade-up (also down, left and right!)</p>
   <p class="fragment current-visible">visible only once</p>
   <p class="fragment highlight-current-blue">blue only once</p>
   <p class="fragment highlight-red">highlight-red</p>
   <p class="fragment highlight-green">highlight-green</p>
   <p class="fragment highlight-blue">highlight-blue</p>
</section>
```

Multiple fragments can be applied to the same element sequentially by wrapping it, this will fade in the text on the first step and fade it back out on the second.

```html
<section>
   <span class="fragment fade-in">
      <span class="fragment fade-out">I'll fade in, then out</span>
   </span>
</section>
```

The display order of fragments can be controlled using the ```data-fragment-index``` attribute.

```html
<section>
   <p class="fragment" data-fragment-index="3">Appears last</p>
   <p class="fragment" data-fragment-index="1">Appears first</p>
   <p class="fragment" data-fragment-index="2">Appears second</p>
</section>
```

### Fragment events

When a slide fragment is either shown or hidden reveal.js will dispatch an event.

Some libraries, like MathJax (see #505), get confused by the initially hidden fragment elements. Often times this can be fixed by calling their update or render function from this callback.

```javascript
Reveal.addEventListener( 'fragmentshown', function( event ) {
   // event.fragment = the fragment DOM element
} );
Reveal.addEventListener( 'fragmenthidden', function( event ) {
   // event.fragment = the fragment DOM element
} );
```

### Code syntax highlighting

By default, Reveal is configured with [highlight.js](https://highlightjs.org/) for code syntax highlighting. Below is an example with clojure code that will be syntax highlighted. When the `data-trim` attribute is present, surrounding whitespace is automatically removed.  HTML will be escaped by default. To avoid this, for example if you are using `<mark>` to call out a line of code, add the `data-noescape` attribute to the `<code>` element.

```html
<section>
   <pre><code data-trim data-noescape>
(def lazy-fib
  (concat
   [0 1]
   <mark>((fn rfib [a b]</mark>
        (lazy-cons (+ a b) (rfib b (+ a b)))) 0 1)))
   </code></pre>
</section>
```

### Slide number
If you would like to display the page number of the current slide you can do so using the ```slideNumber``` configuration value.

```javascript
// Shows the slide number using default formatting
Reveal.configure({ slideNumber: true });

// Slide number formatting can be configured using these variables:
//  "h.v":  horizontal . vertical slide number (default)
//  "h/v":  horizontal / vertical slide number
//    "c":  flattened slide number
//  "c/t":  flattened slide number / total slides
Reveal.configure({ slideNumber: 'c/t' });

```


### Overview mode

Press "Esc" or "o" keys to toggle the overview mode on and off. While you're in this mode, you can still navigate between slides,
as if you were at 1,000 feet above your presentation. The overview mode comes with a few API hooks:

```javascript
Reveal.addEventListener( 'overviewshown', function( event ) { /* ... */ } );
Reveal.addEventListener( 'overviewhidden', function( event ) { /* ... */ } );

// Toggle the overview mode programmatically
Reveal.toggleOverview();
```

### Fullscreen mode
Just press »F« on your keyboard to show your presentation in fullscreen mode. Press the »ESC« key to exit fullscreen mode.


### Embedded media
Embedded HTML5 `<video>`/`<audio>` and YouTube iframes are automatically paused when you navigate away from a slide. This can be disabled by decorating your element with a `data-ignore` attribute.

Add `data-autoplay` to your media element if you want it to automatically start playing when the slide is shown:

```html
<video data-autoplay src="http://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4"></video>
```

Additionally the framework automatically pushes two [post messages](https://developer.mozilla.org/en-US/docs/Web/API/Window.postMessage) to all iframes, ```slide:start``` when the slide containing the iframe is made visible and ```slide:stop``` when it is hidden.


### Stretching elements
Sometimes it's desirable to have an element, like an image or video, stretch to consume as much space as possible within a given slide. This can be done by adding the ```.stretch``` class to an element as seen below:

```html
<section>
   <h2>This video will use up the remaining space on the slide</h2>
    <video class="stretch" src="http://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4"></video>
</section>
```

Limitations:
- Only direct descendants of a slide section can be stretched
- Only one descendant per slide section can be stretched


### postMessage API
The framework has a built-in postMessage API that can be used when communicating with a presentation inside of another window. Here's an example showing how you'd make a reveal.js instance in the given window proceed to slide 2:

```javascript
<window>.postMessage( JSON.stringify({ method: 'slide', args: [ 2 ] }), '*' );
```

When reveal.js runs inside of an iframe it can optionally bubble all of its events to the parent. Bubbled events are stringified JSON with three fields: namespace, eventName and state. Here's how you subscribe to them from the parent window:

```javascript
window.addEventListener( 'message', function( event ) {
   var data = JSON.parse( event.data );
   if( data.namespace === 'reveal' && data.eventName ==='slidechanged' ) {
      // Slide changed, see data.state for slide number
   }
} );
```

This cross-window messaging can be toggled on or off using configuration flags.

```javascript
Reveal.initialize({
   ...,

   // Exposes the reveal.js API through window.postMessage
   postMessage: true,

   // Dispatches all reveal.js events to the parent window through postMessage
   postMessageEvents: false
});
```


## PDF Export

Presentations can be exported to PDF via a special print stylesheet. This feature requires that you use [Google Chrome](http://google.com/chrome) or [Chromium](https://www.chromium.org/Home) and to be serving the presention from a webserver.
Here's an example of an exported presentation that's been uploaded to SlideShare: http://www.slideshare.net/hakimel/revealjs-300.

### Page size
Export dimensions are inferred from the configured [presentation size](#presentation-size). Slides that are too tall to fit within a single page will expand onto multiple pages. You can limit how many pages a slide may expand onto using the `pdfMaxPagesPerSlide` config option, for example `Reveal.configure({ pdfMaxPagesPerSlide: 1 })` ensures that no slide ever grows to more than one printed page.

### Print stylesheet
To enable the PDF print capability in your presentation, the special print stylesheet at [/css/print/pdf.css](https://github.com/hakimel/reveal.js/blob/master/css/print/pdf.css) must be loaded. The default index.html file handles this for you when `print-pdf` is included in the query string. If you're using a different HTML template, you can add this to your HEAD:

```html
<script>
   var link = document.createElement( 'link' );
   link.rel = 'stylesheet';
   link.type = 'text/css';
   link.href = window.location.search.match( /print-pdf/gi ) ? 'css/print/pdf.css' : 'css/print/paper.css';
   document.getElementsByTagName( 'head' )[0].appendChild( link );
</script>
```

### Instructions
1. Open your presentation with `print-pdf` included in the query string i.e. http://localhost:8000/?print-pdf. You can test this with [lab.hakim.se/reveal-js?print-pdf](http://lab.hakim.se/reveal-js?print-pdf).
2. Open the in-browser print dialog (CTRL/CMD+P).
3. Change the **Destination** setting to **Save as PDF**.
4. Change the **Layout** to **Landscape**.
5. Change the **Margins** to **None**.
6. Enable the **Background graphics** option.
7. Click **Save**.

![Chrome Print Settings](https://s3.amazonaws.com/hakim-static/reveal-js/pdf-print-settings-2.png)

Alternatively you can use the [decktape](https://github.com/astefanutti/decktape) project.

## Theming

The framework comes with a few different themes included:

- black: Black background, white text, blue links (default theme)
- white: White background, black text, blue links
- league: Gray background, white text, blue links (default theme for reveal.js < 3.0.0)
- beige: Beige background, dark text, brown links
- sky: Blue background, thin dark text, blue links
- night: Black background, thick white text, orange links
- serif: Cappuccino background, gray text, brown links
- simple: White background, black text, blue links
- solarized: Cream-colored background, dark green text, blue links

Each theme is available as a separate stylesheet. To change theme you will need to replace **black** below with your desired theme name in index.html:

```html
<link rel="stylesheet" href="css/theme/black.css" id="theme">
```

If you want to add a theme of your own see the instructions here: [/css/theme/README.md](https://github.com/hakimel/reveal.js/blob/master/css/theme/README.md).


## Speaker Notes

reveal.js comes with a speaker notes plugin which can be used to present per-slide notes in a separate browser window. The notes window also gives you a preview of the next upcoming slide so it may be helpful even if you haven't written any notes. Press the 's' key on your keyboard to open the notes window.

A speaker timer starts as soon as the speaker view is opened. You can reset it to 00:00:00 at any time by simply clicking/tapping on it.

Notes are defined by appending an ```<aside>``` element to a slide as seen below. You can add the ```data-markdown``` attribute to the aside element if you prefer writing notes using Markdown.

Alternatively you can add your notes in a `data-notes` attribute on the slide. Like `<section data-notes="Something important"></section>`.

When used locally, this feature requires that reveal.js [runs from a local web server](#full-setup).

```html
<section>
   <h2>Some Slide</h2>

   <aside class="notes">
      Oh hey, these are some notes. They'll be hidden in your presentation, but you can see them if you open the speaker notes window (hit 's' on your keyboard).
   </aside>
</section>
```

If you're using the external Markdown plugin, you can add notes with the help of a special delimiter:

```html
<section data-markdown="example.md" data-separator="^\n\n\n" data-separator-vertical="^\n\n" data-separator-notes="^Note:"></section>

# Title
## Sub-title

Here is some content...

Note:
This will only display in the notes window.
```

#### Share and Print Speaker Notes

Notes are only visible to the speaker inside of the speaker view. If you wish to share your notes with others you can initialize reveal.js with the `showNotes` config value set to `true`. Notes will appear along the bottom of the presentations.

When `showNotes` is enabled notes are also included when you [export to PDF](https://github.com/hakimel/reveal.js#pdf-export). By default, notes are printed in a semi-transparent box on top of slide. If you'd rather print them on a separate page after the slide, set `showNotes: "separate-page"`.

## Server Side Speaker Notes

In some cases it can be desirable to run notes on a separate device from the one you're presenting on. The Node.js-based notes plugin lets you do this using the same note definitions as its client side counterpart. Include the required scripts by adding the following dependencies:

```javascript
Reveal.initialize({
   ...

   dependencies: [
      { src: 'socket.io/socket.io.js', async: true },
      { src: 'plugin/notes-server/client.js', async: true }
   ]
});
```

Then:

1. Install [Node.js](http://nodejs.org/) (4.0.0 or later)
2. Run ```npm install```
3. Run ```node plugin/notes-server```


## Multiplexing

The multiplex plugin allows your audience to view the slides of the presentation you are controlling on their own phone, tablet or laptop. As the master presentation navigates the slides, all client presentations will update in real time. See a demo at [https://reveal-js-multiplex-ccjbegmaii.now.sh/](https://reveal-js-multiplex-ccjbegmaii.now.sh/).

The multiplex plugin needs the following 3 things to operate:

1. Master presentation that has control
2. Client presentations that follow the master
3. Socket.io server to broadcast events from the master to the clients

More details:

#### Master presentation
Served from a static file server accessible (preferably) only to the presenter. This need only be on your (the presenter's) computer. (It's safer to run the master presentation from your own computer, so if the venue's Internet goes down it doesn't stop the show.) An example would be to execute the following commands in the directory of your master presentation:

1. ```npm install node-static```
2. ```static```

If you want to use the speaker notes plugin with your master presentation then make sure you have the speaker notes plugin configured correctly along with the configuration shown below, then execute ```node plugin/notes-server``` in the directory of your master presentation. The configuration below will cause it to connect to the socket.io server as a master, as well as launch your speaker-notes/static-file server.

You can then access your master presentation at ```http://localhost:1947```

Example configuration:
```javascript
Reveal.initialize({
   // other options...

   multiplex: {
      // Example values. To generate your own, see the socket.io server instructions.
      secret: '13652805320794272084', // Obtained from the socket.io server. Gives this (the master) control of the presentation
      id: '1ea875674b17ca76', // Obtained from socket.io server
      url: 'https://reveal-js-multiplex-ccjbegmaii.now.sh' // Location of socket.io server
   },

   // Don't forget to add the dependencies
   dependencies: [
      { src: '//cdn.socket.io/socket.io-1.3.5.js', async: true },
      { src: 'plugin/multiplex/master.js', async: true },

      // and if you want speaker notes
      { src: 'plugin/notes-server/client.js', async: true }

      // other dependencies...
   ]
});
```

#### Client presentation
Served from a publicly accessible static file server. Examples include: GitHub Pages, Amazon S3, Dreamhost, Akamai, etc. The more reliable, the better. Your audience can then access the client presentation via ```http://example.com/path/to/presentation/client/index.html```, with the configuration below causing them to connect to the socket.io server as clients.

Example configuration:
```javascript
Reveal.initialize({
   // other options...

   multiplex: {
      // Example values. To generate your own, see the socket.io server instructions.
      secret: null, // null so the clients do not have control of the master presentation
      id: '1ea875674b17ca76', // id, obtained from socket.io server
      url: 'https://reveal-js-multiplex-ccjbegmaii.now.sh' // Location of socket.io server
   },

   // Don't forget to add the dependencies
   dependencies: [
      { src: '//cdn.socket.io/socket.io-1.3.5.js', async: true },
      { src: 'plugin/multiplex/client.js', async: true }

      // other dependencies...
   ]
});
```

#### Socket.io server
Server that receives the slideChanged events from the master presentation and broadcasts them out to the connected client presentations. This needs to be publicly accessible. You can run your own socket.io server with the commands:

1. ```npm install```
2. ```node plugin/multiplex```

Or you use the socket.io server at [https://reveal-js-multiplex-ccjbegmaii.now.sh/](https://reveal-js-multiplex-ccjbegmaii.now.sh/).

You'll need to generate a unique secret and token pair for your master and client presentations. To do so, visit ```http://example.com/token```, where ```http://example.com``` is the location of your socket.io server. Or if you're going to use the socket.io server at [https://reveal-js-multiplex-ccjbegmaii.now.sh/](https://reveal-js-multiplex-ccjbegmaii.now.sh/), visit [https://reveal-js-multiplex-ccjbegmaii.now.sh/token](https://reveal-js-multiplex-ccjbegmaii.now.sh/token).

You are very welcome to point your presentations at the Socket.io server running at [https://reveal-js-multiplex-ccjbegmaii.now.sh/](https://reveal-js-multiplex-ccjbegmaii.now.sh/), but availability and stability are not guaranteed. For anything mission critical I recommend you run your own server. It is simple to deploy to nodejitsu, heroku, your own environment, etc.

##### socket.io server as file static server

The socket.io server can play the role of static file server for your client presentation, as in the example at [https://reveal-js-multiplex-ccjbegmaii.now.sh/](https://reveal-js-multiplex-ccjbegmaii.now.sh/). (Open [https://reveal-js-multiplex-ccjbegmaii.now.sh/](https://reveal-js-multiplex-ccjbegmaii.now.sh/) in two browsers. Navigate through the slides on one, and the other will update to match.)

Example configuration:
```javascript
Reveal.initialize({
   // other options...

   multiplex: {
      // Example values. To generate your own, see the socket.io server instructions.
      secret: null, // null so the clients do not have control of the master presentation
      id: '1ea875674b17ca76', // id, obtained from socket.io server
      url: 'example.com:80' // Location of your socket.io server
   },

   // Don't forget to add the dependencies
   dependencies: [
      { src: '//cdn.socket.io/socket.io-1.3.5.js', async: true },
      { src: 'plugin/multiplex/client.js', async: true }

      // other dependencies...
   ]
```

It can also play the role of static file server for your master presentation and client presentations at the same time (as long as you don't want to use speaker notes). (Open [https://reveal-js-multiplex-ccjbegmaii.now.sh/](https://reveal-js-multiplex-ccjbegmaii.now.sh/) in two browsers. Navigate through the slides on one, and the other will update to match. Navigate through the slides on the second, and the first will update to match.) This is probably not desirable, because you don't want your audience to mess with your slides while you're presenting. ;)

Example configuration:
```javascript
Reveal.initialize({
   // other options...

   multiplex: {
      // Example values. To generate your own, see the socket.io server instructions.
      secret: '13652805320794272084', // Obtained from the socket.io server. Gives this (the master) control of the presentation
      id: '1ea875674b17ca76', // Obtained from socket.io server
      url: 'example.com:80' // Location of your socket.io server
   },

   // Don't forget to add the dependencies
   dependencies: [
      { src: '//cdn.socket.io/socket.io-1.3.5.js', async: true },
      { src: 'plugin/multiplex/master.js', async: true },
      { src: 'plugin/multiplex/client.js', async: true }

      // other dependencies...
   ]
});
```

## MathJax

If you want to display math equations in your presentation you can easily do so by including this plugin. The plugin is a very thin wrapper around the [MathJax](http://www.mathjax.org/) library. To use it you'll need to include it as a reveal.js dependency, [find our more about dependencies here](#dependencies).

The plugin defaults to using [LaTeX](http://en.wikipedia.org/wiki/LaTeX) but that can be adjusted through the ```math``` configuration object. Note that MathJax is loaded from a remote server. If you want to use it offline you'll need to download a copy of the library and adjust the ```mathjax``` configuration value.

Below is an example of how the plugin can be configured. If you don't intend to change these values you do not need to include the ```math``` config object at all.

```js
Reveal.initialize({

   // other options ...

   math: {
      mathjax: 'https://cdn.mathjax.org/mathjax/latest/MathJax.js',
      config: 'TeX-AMS_HTML-full'  // See http://docs.mathjax.org/en/latest/config-files.html
   },

   dependencies: [
      { src: 'plugin/math/math.js', async: true }
   ]

});
```

Read MathJax's documentation if you need [HTTPS delivery](http://docs.mathjax.org/en/latest/start.html#secure-access-to-the-cdn) or serving of [specific versions](http://docs.mathjax.org/en/latest/configuration.html#loading-mathjax-from-the-cdn) for stability.


## Installation

The **basic setup** is for authoring presentations only. The **full setup** gives you access to all reveal.js features and plugins such as speaker notes as well as the development tasks needed to make changes to the source.

### Basic setup

The core of reveal.js is very easy to install. You'll simply need to download a copy of this repository and open the index.html file directly in your browser.

1. Download the latest version of reveal.js from <https://github.com/hakimel/reveal.js/releases>

2. Unzip and replace the example contents in index.html with your own

3. Open index.html in a browser to view it


### Full setup

Some reveal.js features, like external Markdown and speaker notes, require that presentations run from a local web server. The following instructions will set up such a server as well as all of the development tasks needed to make edits to the reveal.js source code.

1. Install [Node.js](http://nodejs.org/) (4.0.0 or later)

1. Clone the reveal.js repository
   ```sh
   $ git clone https://github.com/hakimel/reveal.js.git
   ```

1. Navigate to the reveal.js folder
   ```sh
   $ cd reveal.js
   ```

1. Install dependencies
   ```sh
   $ npm install
   ```

1. Serve the presentation and monitor source files for changes
   ```sh
   $ npm start
   ```

1. Open <http://localhost:8000> to view your presentation

   You can change the port by using `npm start -- --port=8001`.


### Folder Structure
- **css/** Core styles without which the project does not function
- **js/** Like above but for JavaScript
- **plugin/** Components that have been developed as extensions to reveal.js
- **lib/** All other third party assets (JavaScript, CSS, fonts)


## License

MIT licensed

Copyright (C) 2016 Hakim El Hattab, http://hakim.se

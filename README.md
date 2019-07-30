# windowing-technique-echart
给 echart 加上窗口化技术

[预览地址](https://qccs.github.io/windowing-technique-echart/)

## 问题
做项目的时候，渲染柱形图，后端返回大约 5000 数据，

每一个柱子高度 30 px

那么 echart 的高度：5000 * 30 = 150000 px；

![](https://github.com/QCCS/windowing-technique-echart/blob/master/1.png)

## 关于 echart
echart 有两种渲染模式，分别是svg 与 canvas

canvas 渲染性能要高于svg，但是 canvas 在不同的浏览器都有限制，对最大渲染的像素不能超过一个数。

svg 渲染虽然没有这个限制，但是渲染的速度很难接受

如果数据量再大一点，svg等待时间可能是几小时

## 窗口化技术

把 echart 设置一个固定的高度与宽度，比如 width 600 * height 400

每次只渲染 10 条数据，监听滚轮事件，根据滚动距离，实时截取应该被渲染的数据

## 本 demo 主要实现以下功能点

- 毫秒级别渲染 10W 条数据以内，如果涉及百万条数据，需要做数据分块
- 鼠标滚轮与虚拟滚动条双向绑定
- 兼容 chrome 与 Firefox

![](https://github.com/QCCS/windowing-technique-echart/blob/master/2.png)

用的是原生 js ，看看原理，可以很方便移植到 react 或者 vue 项目。

wechat: qianchaochushui
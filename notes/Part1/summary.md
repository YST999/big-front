# 布局总结
前言
布局就像是 加强版的 俄罗斯方块游戏:
1.DOM 元素就是一个个方块
2.CSS 属性就是画笔与胶水，修饰这些方块、并且将这些方块连接起来

全部的 CSS 属性很多，但是我们只要牢记其中几个重要的属性，就可以完成复杂的布局任务

## 那些重要的 CSS 规则：
1. 一切皆盒子，盒模型分为：[^1]
    标准盒模型(box-sizing: content-box): width = 内容的宽度
    怪异盒模型(box-sizing: border-box) : width = border + padding + 内容的宽度

2. DOM 元素分类、及其对应的默认 display 属性[^2]
    块级元素:    display: bolck;
    行内元素:    display: inline;
    行内块级元素: display: inline-block;

3. 普通流(normal-flow) 与 脱离普通流[^3]
    除浮动或者定位布局的DOM 元素，都在普通流中
    浮动 与 清除浮动[^4]
    定位 与 定位偏移量[^5] [^6]

## 那些次重要的 CSS 规则：
1. 样式表、选择器的优先级
    内联样式style= > (内部样式`<style>` = 外部样式link)

2. 布局单位，重点关注相对长度单位[^7]

3. flex 布局

## 其他的 CSS 属性我们可以在这里查阅：
1. [MDN 官网(右上角搜索框框)](https://developer.mozilla.org/zh-CN/)

2. [CSS 参考手册](https://css.doyoe.com/)

[^1]:[盒模型 MDN](https://developer.mozilla.org/zh-cn/docs/Web/CSS/box-sizing)
[^2]:[HTML元素分类](https://www.jianshu.com/p/c663e4729cd7)
[^3]:[CSS 流](https://leohxj.gitbooks.io/front-end-database/content/html-and-css-basic/css-normal-flow.html)
[^4]:[浮动 MDN(值得仔细看的教科书级文档)](https://developer.mozilla.org/zh-CN/docs/Web/CSS/clear)
[^5]:[定位](https://developer.mozilla.org/zh-cn/docs/Web/CSS/position)
[^6]:[定位偏移量](https://developer.mozilla.org/en-US/docs/Web/CSS/position_value)
[^7]:[布局单位](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Values_and_units)

## 移动WEB开发基础

移动端开发现状：

移动端浏览器我们主要对webkit内核进行兼容；我们现在开发的移动端主要针对手机端开发
现在移动端碎片化比较严重，分辨率和屏幕尺寸大小不一；学会用谷歌浏览器模拟手机界面以及调试

### 视口：

浏览器显示页面内容的屏幕区域。

* 布局视口(layout viewport)

  

* 视觉视口(visual viewport)

  用户正在看到的网站的区域。

  可以通过缩放去操作视觉视口，但不会改变布局视口

* 理想视口(ideal viewport)

  为了使网站在移动端有最理想的浏览和阅读宽度而设定

  需要添加<meta>视口标签通知浏览器操作

  作用：让布局视口和理想视口的宽度一致。

标准的viewport参数设置

* 视口宽度和设备保持一致
* 视口的默认缩放比例1.0
* 不允许用户自行缩放
* 最大允许的缩放比例1.0
* 最小允许的缩放比例1.0

### 二倍图：

#### 物理像素&物理像素比

1. 物理像素点指的是屏幕显示的最小颗粒，是物理真实存在的，厂商在出厂时已设置好，后期不会改变。iPhone6/7/8  750x1334
2. 开发时的1px不是一定等于1个物理像素的
3. PC端页面，1px等于1个物理像素，移动端不尽相同。
4. 一个1px能显示的物理像素点的个数，称为物理像素比或屏幕像素比。
5. PC端和早起的手机屏幕/普通手机屏幕：1CSS像素=1物理像素
6. Retina(视网膜屏幕)是一种显示技术，可以把更多的物理像素点压缩在一块屏幕内，从而达到更高的分辨率，并提高屏幕显示的细腻程度。

多倍图：

背景：如果一个50 * 50px的图片放在手机屏幕中，占有的物理像素点是100 *100个，会造成图片模糊。

解决：使用一个本身就是100 *100px的图片去进行制作，替换原来的图片。然后设置图片尺寸为50 *50px。

背景图也需要使用多倍图来进行加载。使用background-size来更改图片大小。

切图要用原始尺寸，开发时使用开发尺寸。

#### 移动端开发选择

主流：单独制作移动端页面 eg.淘宝 京东 苏宁

* 两套代码，一般在网址域名前加m

其次：响应式页面兼容移动端  eg.三星手机官网

* 共用一套网站，在不同宽度的屏幕下自动适配。
* 制作麻烦，需要调兼容性问题

#### 常见问题解决：

###### 浏览器：

移动端浏览器基本以webkit内核为主，因此主要考虑webkit兼容性问题。

支持H5C3

浏览器的私有前缀我们只需考虑添加-webkit-即可。

CSS normalize.css

替代reset.css,可定制，让不同的浏览器在渲染网页元素的时候形式更统一，是一种现代的、为HTML5准备的优质替代方案。

优点：

1. 保护了有价值的默认值
2. 修复了浏览器的bug，解决了浏览器的不一致的默认样式
3. Normalize.css是模块化的，提高了易用性
4. 文档详细

CSS3盒子模型 box-sizing

此盒子的宽度里包含了border和padding。

移动端技术选型

单独制作移动端页面：

* 流式布局(百分比布局)
* flex弹性布局(推荐)
* less+rem+媒体查询
* 混合布局

响应式：

* 媒体查询
* bootstrap



### 流式布局(百分比布局)

1. 也称非固定像素布局
2. 通过将盒子的宽度设置成百分比，从而根据屏幕的宽度来进行伸缩，不受固定像素的限制，内容向两侧填充。
3. 流式布局方式是移动web开发使用的比较常见的布局方式。

##### 注意事项

制作过程中需要定义最大最小支持宽度

* max-width/max-height
* min-width/min-height



### 京东flex布局

二倍精灵图做法：

1. 等比缩放精灵图
2. 根据新的大小量取坐标
3. background-sizing也需要设置为缩放后的数值(精灵图原来宽度的一半)

制作渐变背景：

1. background-image （详情见MDN）

   1. 取值：

      * none：表示无背景图的关键字
      * image：用来标记将要显示的图片，支持多背景设置，‘，’分隔

   2. 语法：

      ```css
        background-image:
            url("https://mdn.mozillademos.org/files/6457/mdn_logo_only_color.png");
      ```

2. 相关函数：[`linear-gradient`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/linear-gradient), [`radial-gradient`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/radial-gradient), [`repeating-linear-gradient`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/repeating-linear-gradient), [`repeating-radial-gradient`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/repeating-radial-gradient)

3. linear-gradient：

   ```css
   /* 渐变轴为45度，从蓝色渐变到红色 */
   linear-gradient(45deg, blue, red);
   
   /* 从右下到左上、从蓝色渐变到红色 */
   linear-gradient(to left top, blue, red);
   
   /* 从下到上，从蓝色开始渐变、到高度40%位置是绿色渐变开始、最后以红色结束 */
   linear-gradient(0deg, blue, green 40%, red);
   ```

图片格式：

1. DPG图片压缩技术

   京东自主研发，可节省用户近50%的浏览流量，极大提升用户打开网页的速度。能够兼容JPEG，实现全平台、全部浏览器的兼容支持。压缩后的图片和webp的清晰度对比没有差距。

2. webp图片格式

   谷歌开发的一种旨在加快图片加载速度的图片格式。图片压缩后的体积大约只有JPEG的2/3，并能节省大量的服务器宽带资源和数据空间。8

图片转为块级元素？为什么 什么情况
# CSS世界 学习笔记 例子

## 第1章 概述

### 1.1 CSS世界的“世界观”

### 1.2 世界都是创造出来的

CSS世界的诞生就是为图文信息展示服务的

### 1.3 CSS完胜SVG的武器——流

#### 1.3.1 何为“流”

“流”实际上是CSS世界中一种基本的定位和布局机制

#### 1.3.2 流是如何影响整个CSS世界的

#### 1.3.3 什么是流体布局

### 1.4 CSS世界的开启从IE8开始

### 1.5 table自己的世界

### 1.6 CSS新世界——CSS3

## 第2章 需提前了解的术语和概念

### 2.1 务必了解的CSS世界的专业术语

1. 属性
2. 值
3. 关键字
4. 变量
5. 长度单位
6. 功能符
7. 属性值
8. 声明
9. 声明块
10. 规则或规则集
11. 选择器
    - 类选择器
    - ID选择器
    - 属性选择器
    - 伪类选择器
    - 伪元素选择器
12. 关系选择器
    - 后代选择器
    - 相邻后代选择器
    - 兄弟选择器
    - 相邻兄弟选择器
13. @规则

### 2.2 了解CSS世界中的未定义行为

## 第3章 流、元素与基本尺寸

### 3.1 块级元素

#### 3.1.1 为什么list-item元素会出现项目符号

每个元素都有两个盒子：外在盒子和容器盒子。外在盒子觉得元素时候换行显示；容器盒子觉得宽高、内容呈现。

#### 3.1.2 display:inline-block 的盒子是怎样组成的

#### 3.1.3 width/height 作用在哪个盒子上

### 3.2 width/height 作用的具体细节

#### 3.2.1 深藏不露的 width:auto

1. 充分利用可用空间
2. 收缩与包裹
3. 收缩到最小
4. 超出容器限制

子元素既保持了inline-block元素的收缩特性，又同时让内容宽度最大，直接无视父级容器的宽度限制。

##### 1. 外部尺寸与流体特性

1. 正常流宽度
2. 格式化宽度

格式化宽度仅出现在决定定位模型中，也就是出现在position属性值为absolute或fixed的元素中。
默认情况下，绝对定位元素的宽度表现是“包裹性”的，即宽度是由内部尺寸决定的。
对于非替换性元素，当left/right或top/bottom对立方位的属性值同时存在的时候，元素的宽度表现为“格式化宽度”，即其宽度大小相对于最近的具有定位特性的祖先元素计算。

##### 2.内部尺寸与流体特性

1. 包裹性
2. 首选最小宽度

    - 东亚文字最小宽度为每个汉字的宽度。
    - 西方文字最小宽度由特定的连续的英文字符单元决定，以空格、短横线、问号以及其他非英文字符分割。
    - 图片的最小宽度就是该元素内容本身的宽度。

3. 最大宽度

最大宽度实际等同于“包裹性”元素设置wihte-space：norwap 声明后的宽度。
如果内部没有块级元素或者块级元素没有设定宽度值，则最大宽度实际上是最大的连续内联盒子的宽度。

#### 3.2.2 width值作用的细节

内在盒子又分为4个盒子，分别是content box、padding box、border box、margin box。

margin的背景永远是透明的。

margin一旦设定具体宽度和高度值，其本身的尺寸是不会因margin值变化而变化的。

设置padding、border后会：
    - 流动性丢失
    - 与现实世界表现不一致的困扰
    width会直接作用于content box上

#### 3.2.3 CSS流体布局下的宽度分离原则

“宽度分离原则”是指CSS中的width属性不与影响宽度的padding/border（有时候包括margin）属性共存。

#### 3.2.4 改变width/height作用细节的box-sizing

#### 3.2.5 相对简单而单纯的height:auto

#### 3.2.6 关于height：100%

对于width属性，父元素的width为auto，百分比值是支持的；但是，对于height属性，如果父元素的height为auto，只要子元素在文档流中，其百分比值就被忽略了。

原因：如果包含块的高度没有显示指定（即高度由内容决定），并且该元素不是绝对定位，则计算值为auto。auto和100%无法一起计算，所以百分比就被忽略了。

##### 如何让元素支持height：100%效果

1. 设定显式的高度值
2. 使用绝对定位

### 3.3 CSS min-width/max-width和min-height/max-height二三事

#### 3.3.1 为流体而生的min-width/max-width

#### 3.3.2 与众不同的初始值

- width/height的默认值为auto。
- min-width/min-height的初始值也是auto。
- max-width/max-height的初始值为none。

#### 3.3.3 超越！important，超越最大

1. 超越！important是指max-width会覆盖添加!important的width属性
2. 超越最大是指在min-width和max-width冲突的时候min-width会覆盖max-width

#### 3.3.4 任意高度元素的展开收起动画技术

- 从0px到auto是无法计算的，因此无法形成过渡或动画效果。
- max-height的值比height计算值大的时候，元素的高度就是height属性的计算值

### 3.4 内联元素

#### 3.4.1 哪些元素是内联元素

#### 3.4.2 内联世界深入的基础——内联盒模型

#### 3.4.3 幽灵空白节点

文档声明为HTML5时，内联元素的所有解析和渲染表现就如同每个行框盒子的前面有一个“空白节点”一样。

## 第4章 盒尺寸四大家族

### 4.1 深入理解content

#### 4.1.1 content与替换元素

1. 什么是替换元素——通过修改某个属性值呈现的内容就可以被替换的元素就称为“替换元素”

    1. 内容的外观不收页面上CSS的影响
    2. 有自己的尺寸
    3. 在很多CSS属性上有自己的一套表现规则

2. 替换元素的默认display值
3. 替换元素的尺寸计算规则
    1. 固有尺寸指的是替换内容原本的尺寸
    2. HTML尺寸
    3. CSS尺寸特指可以通过CSS的width和height或者max-width/min-width和max-height/min-height设置的尺寸
    4. 计算规则如下：
        - 如果没有CSS尺寸和HTML尺寸，则使用固有尺寸作为最终的宽高
        - 如果没CSS尺寸，就使用HTML尺寸作为最终的宽高
        - 如果有CSS尺寸，则最终尺寸由CSS属性决定
        - 如果“固有尺寸”含有固有的宽高比例，同时仅设置了宽度或仅设置了高度，则元素依然按照固有的宽高比例显示
        - 如果上面的条件都不符合，则最终宽度表现为300px，高度为150px，宽高比2：1（img标签除外）
        - 内联替换原宿和块级替换元素使用上面同一套尺寸计算规则

    - 当图片的src属性缺省的时候，图片不会有任何请求，是最高效的占位实现方式
    - CSS世界中的替换元素的固有尺寸有一个很重要的特性，就是“我们是无法改变这个替换元素内容的固有尺寸的”

4. 替换元素和非替换元素的距离有多远
    1. 替换元素和非替换元素之间只隔了一个src属性
    2. 替换元素和非替换元素之间只隔了一个CSS content属性
5. content与替换元素关系剖析
    1. 使用content生成的文本无法选中、无法复制
    2. 不能左右:emtey伪类
    3. content动态生成值无法获取

#### 4.1.2 content内容生成技术——::before/::after伪元素技术

1. content辅助元素生成
2. content字符内容生成
3. content图片生成
4. 了解content开启闭合符号生成
5. content attr属性值内容生成
6. 深入理解content计数器
    1. 属性counter-rest，作用是给计数器起个名字
    2. 属性counter-increment，就是计数器递增
        - 普照源唯一，每普照一次，普照源就增加一次计数值
        - 计数器的数值变化遵循HTML渲染顺序，遇到一个increment计数器就变化，什么时候counter输出就输出此时的计数值
        - counter-rest可以一次命名两个计数器，increment也可以，用空格隔开
        - 变化的值不一定是1，可以灵活设置
        - 值还可以为none或inherit
    3. 方法counter()/counters()
7. content内容生成的混合特性

### 4.2 温和的 padding 属性

#### 4.2.1 padding 与元素的尺寸

在设置box-sizing:border-box时，如果padding足够大，那么width也无能为力

内联元素的padding在垂直方向同样会影响布局，影响视觉表现。只是因为内联元素没有可视宽度和可视高度的说法，垂直方向的行为表现完全受line-height和vertical-align的影响，视觉上病没有改变和上一行下一行内容的间距，所以我们就感觉垂直padding没有起作用。

这样我们就可以在不影响当前布局的情况下，优雅地增加链接或按钮的点击区域的大小。

对于非替换元素的内联元素，不仅padding不会加入行盒高度的计算，margin和border也都是如此，都是不计算高度，但实际上在内联盒周围发生了渲染。

#### 4.2.2 padding 的百分比值

1. 和margin属性不同，padding属性不支持负值
2. padding支持百分比值，但是无论是水平方向还是垂直方向都是相对于宽度计算的
    - 对于内联元素
        1. 同样是基于宽度计算
        2. 默认的高度和宽度细节有差异
        3. padding会断行

#### 4.2.3 标签元素内置的 padding

1. ol/ul 列表内置 padding-left，但是单位是px不是em
2. 很多表单元素都内置padding
    - 所有浏览器input标签和textarea标签输入框内置 padding
    - 所有浏览器button标签按钮内置 padding
    - 部门浏览器select下拉内置 padding，如Firefox、IE8
    - 所有浏览器radio标签/checkbox标签按钮内置 padding
    - button按钮元素的 padding最难控制
        - 推荐一个既语义良好行为保留，同时UI效果棒兼容性好的实现小技巧，就是用label元素，label元素的for属性和button元素的id值对应即可

#### 4.2.4 padding 与图形绘制

### 4.3 激进的 margin 属性

#### 4.3.1 margin与元素尺寸以及相关布局

1. 元素尺寸的相关概念
    - 元素尺寸包括padding和border，也就是元素的border box尺寸，原生DOM API中是offsetWidth和offsetHeight
    - 元素内部尺寸包括padding，但不包括border，也就是元素的padding box尺寸，原生DOM API中是clientWidth和clientHeight
    - 元素外部尺寸包括padding、border和margin，也就是元素的margin box尺寸，没有对应的原生API
2. margin与元素的内部尺寸
    - 只有元素是“充分利用可用空间”的状态时，margin才可以改变元素的可视尺寸
    - 只要宽度设定，margin就无法改变元素尺寸
    - 只要元素的尺寸表现符合“充分利用可用空间”，无论是垂直方向还是水平方向，都可以通过margin改变尺寸
    - 对于普通流体元素，margin智能改变元素水平方向尺寸
    - 对于具有拉伸特性的绝对定位元素，则水平或垂直方向都可以
3. margin与元素的外部尺寸
    - 垂直方向margin无法改变元素的内部尺寸，但可以改变外部尺寸
    - margin对尺寸的影响都是针对具有块状特性的元素而言，对于纯内联元素不适用
    - 内联元素垂直方向的margin是没有任何影响的，既不会影响外部尺寸，也不会影响内部尺寸

#### 4.3.2 margin 的百分比值

margin的百分比值无论是水平方向还是垂直方向都是相对于宽度计算的

#### 4.3.3 正确看待CSS世界里的margin合并

1. 什么是margin合并
    - 块级元素的margin-top和margin-bottom有时会合并为单个外边距
    - 不包括浮动和定位元素
    - 只发生在垂直方向
2. margin合并的3种场景
    1. 相邻兄弟元素margin合并
    2. 父级和第一个/最后一个元素
        - 阻止margin-top合并
            1. 父元素设置为块状格式化上下文元素
            2. 父元素设置border-top值
            3. 父元素设置padding-top值
            4. 父元素和第一个子元素之间添加内联元素进行分隔
        - 阻止margin-bottom合并
            1. 父元素设置为块状格式化上下文元素
            2. 父元素设置border-bottom值
            3. 父元素设置padding-bottom值
            4. 父元素和最后一个子元素之间添加内联元素进行分隔
            5. 父元素设置height、min-height或max-height
    3. 空块级元素的margin合并
        - 阻止空元素的margin合并
            1. 设置垂直方向的border
            2. 设置垂直方向的padding
            3. 里面添加内联元素，直接键入空格是无用的
            4. 设置height或min-height
3. margin合并的计算规则
    1. 正正取大值
    2. 正负值相加
    3. 负负取负值
4. margin合并的意义
    1. 兄弟元素的margin合并是为了让图文信息的排版更加舒服自然
    2. 父子margin合并是为了在页面中任何地方嵌套或直接放入任何裸div元素，都不会影响原来的块状布局
    3. 自身margin合并是为了可以避免不小心遗落或者生成的空标签影响排版和布局

#### 4.3.4 深入理解CSS中的margin:auto

- margin:auto的填充规则如下：
    1. 如果一侧定值，一侧auto，则auto是剩余空间大小
    2. 如果两侧都为auto，则平分剩余空间
- 出发margin:auto有一个前提条件，就是width或height为auto时。元素是具有对应方向的自动填充特性的
- 由于绝对定位元素的格式化高度即使父元素height:auto也是支持的，因此，可以在绝对定位下使用margin:auto使块级元素垂直居中对齐
- 如果里面的元素尺寸比外面的大，auto该如何计算？
    1. 默认的水平流中，如果里面的元素大，水平方向auto计算后的负值会被当做0来处理，所以不会水平居中
    2. 垂直方向计算后的负值会保留，所以会垂直居中

#### 4.3.5 margin无效情形解析

1. display计算值inline的非替换元素的垂直margin是无效的
2. 表格中tr和td元素或者设置display计算值是table-cell或table-row的元素的margin都是无效的
    - 计算值是table-caption、table或inline-table则没有问题
    - ::first-letter伪元素也可以解析margin
3. margin合并的时候，更改margin值可能是没有效果的
4. 绝对定位元素非定位方位的margin值“无效”
    - 绝对定位元素的渲染是独立的，所以margin无法影响兄弟元素，所以看起来就像是无效的
5. 定高容器的子元素的margin-bottom或者宽度定死的子元素的margin-right的定位“失效”
6. 鞭长莫及导致的margin无效
7. 内联特性导致的margin无效

### 4.4 功勋卓著的 border 属性

#### 4.4.1 为什么border-width不支持百分比

border-width支持若干关键字：

- thin：等同于1px
- medium：默认，等同于3px
- thick：等同于4px

#### 4.4.2 了解各种border-style类型

1. border-style:none
    - 默认值
    - 重置边框样式时，可以一起写border: 0 none;这样写渲染性能最高
2. border-style:solid
3. border-style:dashed
4. border-style:double
    - double类型的最小边框宽度为3px，这时double才有效果
5. 其他border-style类型
    - inset、outset、groove、ridge风格老土过时，兼容性惨不忍睹

#### 4.4.3 border-color 和 color

1. border-color的默认颜色就是color
2. 其他类似特性的CSS属性还有outline、box-shadow和text-shadow等

#### 4.4.4 border 与透明边框效果

1. 右下方background定位的技巧
    - 默认background背景图片是相对于padding box定位的，所以，计算background-position:100%的位置时不会吧border-width计算在内
2. 优雅增加点击区域大小
3. 三角等图形绘制

#### 4.4.5 border 与图形构建

#### 4.4.6 border 等高布局技术

## 第5章 内联元素和流

### 5.1 字母 x —— CSS 世界中隐匿的举足轻重的角色

#### 5.1.1 字母 x 与 CSS 世界的基线

字母x的下边缘就是我们的基线

#### 5.1.2 字母 x 与 CSS 中的 x-height

x-height指的是小写字母x的高度，就是基线和等分线之间的距离。

middle指的是基线往上1/2 x-height的高度，可以近似理解为字母x交叉点的位置

#### 5.1.3 字母 x 与 CSS 中的 ex

ex 是 CSS 中的一个相对单位，指的是小写字母 x 的高度，就是x-height

ex的价值就是不受字体和字号影响的内联元素的垂直居中对齐效果

### 5.2 内联元素的基石 —— line-height

#### 5.2.1 内联元素的高度之本 —— line-height

div的高度是由行高决定的，而非文字。

对于非替换元素的纯内联元素，其可视高度完全由line-height决定。

行距 = line-height - font-size

理解了行间距后，就能设置line-height的大小根据设计稿获取准确的文字标注值。

半行距，文字上边距，向下取证，下边距，向上取证，例如line-height是1.5，font-size的大小为14px，半行距就是（14px * 2 -14px） / 2 = 3.5px。如果标注值为20px，那么margin-top就该设为17px，margin-bottom为16px

- line-height为2时，半行距是一半的文字大小，两行文字中的间隙为一个文字尺寸大小
- line-height为1时，半行距为0，两行文字紧密贴合在一起
- line-height为0.5时，半行距为负数，两行文字就重叠在一起

line-height 不会影响替换元素

对于块级元素，line-height对其本身是没有任何作用的

#### 5.2.2 为什么 line-height 可以让内联元素居中

1. 要让单行文字垂直居中，只设置line-height一个属性就可以了
2. line-height可以让多行或单行元素近似垂直居中
3. 多行文本或者替换元素的垂直居中实现原理和单行文本不一样，需要vertical-align属性才可以

#### 5.2.3 深入 line-height 的各类属性值

line-height 的默认值是 normal，还支持数值、百分比值和长度值

- 数值：最终的计算值是和当前font-size相乘后的值
- 百分比值：最终的计算值是和当前font-size相乘后的值
- 长度值：带单位的值，如果是em，还是和当前font-size相乘后的值
- 如果属性值为数值，则所有子元素继承的都是数值
- 如果是百分比值或长度值，那么子元素继承的是最终计算后的值

1. 如果是重图文内容显示的网站，一定要用数值作为单位，line-height值可以设为1.6~1.8
2. 如果是片中布局结构的网站，用长度或数值均可，长度值建议可设为20px

#### 5.2.4 内联元素 line-height 的“大值特性”

无论内联元素 line-height 如何设置，最终父级元素的高度都是由数值大的那个 line-height 决定的

### 5.3 line-height 的好朋友 vertical-align

#### 5.3.1 vertical-align 家族基本认识

vertical-align 属性值分为以下4类：

1. 线类：如baseline（默认值）、top、middle、bottom
2. 文本类，如text-top、text-bottom
3. 上标下标类：如sub、super
4. 数值百分比类：如20px、2em、20%等
    - 应该分为数值类和百分比类

根据计算值的不同，相对于基线往上还是往下偏移，取决于vertical-align的计算值是正值还是负值，如果是负值，往下偏移，如果是正值，往上偏移

vertical-align的数值属性值在实际开发时实用性很强

- 兼容性很好
- 可以精确控制内联元素的垂直对齐位置

vertical-align 属性的百分比值是相对于line-height 的计算值计算的

#### 5.3.2 vertical-align 作用的前提

vertical-align 属性智能作用在display计算值为 inline、inline-block、inline-table或inline-cell的元素上。

浮动和绝对定位会让元素块状化，从而使vertical-align属性无效

table-cell元素设置vertical-align垂直对齐的是子元素，但是作用的并不是子元素，而是table-cell元素自身。

#### 5.3.3 vertical-align 和 line-height 之间的关系

font-size 越大字符的基线位置越靠下，因为文字默认全部都是基线对齐，所以当字号大小不一致的两个文字在一起的时候，彼此就会发生上下位移，如果位移距离足够大，就会超过行高的限制，而导致出现意料之外的高度

如何解决常见的图片底部留有间隙的问题

- 图片块状化
- 容器line-height足够小
- 容器font-size足够小，此方法要生效，需要容器的line-heigt和font-size相关
- 图片设置其他vertical-align属性

#### 5.3.4 深入理解vertical-align 线性类属性值

1. inline-block 与 baseline
    - 一个inline-block元素，如果里面没有内联元素，或者overflow不是visible，则该元素的基线就是其margin底边缘，否则其基线就是元素里面最后一行内联元素的基线
    - 改变“幽灵空白节点”的基线位置可以使用font-size，当字体足够小时，基线和中线会重合在一起
    - 20px图标对齐的处理办法
        1. 图标高度和当前行高都是20px
        2. 图标标签里面永远有字符
        3. 图标CSS不适用overflow:hidden 保证基线为链字符的基线，但是要让里面潜在的字符不可见
        4. 如果项目字号都是16px，那么图标规格和默认行号设为24px可能会更适合一些
2. 了解vertical-align:top/bottom
    1. vertical-align:top就是垂直上边缘对齐，具体定义如下
        - 内联元素：元素顶部和当前行框盒子的顶部对齐
        - table-cell元素：元素顶padding边缘和表格行的顶部对齐
    2. vertical-align:bottom的规则与top类似，就是把顶部换成底部，上边缘换成下边缘
3. vertical-align:middle 与近似垂直居中
    - 内联元素：元素的垂直中心点和行框盒子基线往上1/2 x-height 处对齐
    - table-cell元素：单元格填充盒子相对于外面的表格行居中对齐
    - 通常做法是设置font-size为0，整个字符X缩小为看不见的点，根据line-height的半行间距上下等分原则，这个点正好是整个容器的垂直中心位置，这样就可以实现真正意义上的垂直居中对齐了

#### 5.3.5 深入理解vertical-align文本类属性值

文本类属性值得就是text-top和text-bottom

- vertical-align:text-top —— 盒子的顶部和父级内容区域的顶部对齐
- vertical-align:text-bottom —— 盒子的地步和父级内容区域的底部对齐

#### 5.3.6 简单了解vertical-align上标下标类属性值

上标下标类属性值得就是sub和super

- vertical-align:super —— 提高盒子的基线到父级核实的上标基线位置
- vertical-align:sub —— 降低盒子的基线到父级核实的下标基线位置

#### 5.3.7 无处不在的 vertical-align 

top/bottom和baseline/middle，切着对齐看边缘看行框盒子，后者和字符x打交道。

#### 5.3.8 基于 vertical-align 属性的水平垂直居中弹框

1. 节省了很多JavaScript定位代码，也不需要浏览器resize事件处理，当弹框内容动态变化的时候，也无需重新定位
2. 性能更改、渲染更快
3. 可以很灵活的控制垂直居中的比例
4. 容易设置overflow:auto可以实现弹框高度超过一屏时依然能看见屏幕外的内容

## 第6章 流的破坏与保护

### 6.1 魔鬼属性 float

#### 6.1.1 float 的本质与特性

float的特性：

1. 包裹性
    - 包裹
    - 自适应
2. 块状化并格式化上下文
3. 破坏文档流
4. 没有任何margin合并

#### 6.1.2 float 的作用机制

float 属性让父元素高度坍塌的原因就是为了实现文字的环绕效果

行框盒子如何和浮动元素的垂直高度有重叠，则行框盒子在正常定位状态下只会跟随浮动元素，而不会发生重叠

#### 6.1.3 float 更深入的作用机制

- 浮动锚点是 float 元素所在的”流“中的一个点，这个点本身并不浮动，而是更像一个没有margin、padding、border的空的内联元素
- 浮动参考值得是浮动元素对齐参考的实体

#### 6.1.4 float 与流体布局

### 6.2 float 的天然克星 clear

#### 6.2.1 什么是 clear 属性

clear属性：元素盒子的边不能和前面的浮动元素相邻

- none：默认值，左右浮动来就来
- left：左侧抗浮动
- right：右侧抗浮动
- both：两侧抗浮动

#### 6.2.2 成事不足败事有余的 clear

clear 属性只有块级元素才有效果，而 ::after 等伪元素默认都是内联水哦宁，这就是借助伪元素清除浮动影响时需要设置 display 属性的原因

由于clear:both 的作用本质是让自己不和 float 元素在一行显示，并不是真正意义上的清除浮动，因此float元素的一些不好的特性依然存在，所以会有以下现象

1. 如果clear:both 元素前面的元素就是 float 元素，则 margin-top 负值即使设为-9999px，也没有任何效果
2. clear:both 后面的元素依旧会发生文字环绕的现象

### 6.3 CSS 世界的结界——BFC

#### 6.3.1 BFC 的定义

BFC是块级格式化上下文

如果一个元素具有BFC，则内部子元素无论如何都不会影响到外部元素。所以，BFC元素不可能发生margin重叠；BFC元素也可以用来清除浮动的影响。

什么时候会出发BFC？

1. html根元素
2. float的值不为none
3. overflow的值为auto、scroll、hidden
4. display的值为table-cell、table-caption、inline-block
5. position的值部位relative或static

#### 6.3.2 BFC 与浮动布局

普通流体元素设置overflow:hidden 后，会自动填满容器中除浮动元素以外的剩余空间，形成自适应布局的效果

基于BFC的浮动布局有以下优点：

1. 自适应内容由于封闭而更健壮，容错性更强
2. 自适应内容自动填满浮动以外区域，无须关心浮动元素宽度，可以整站大规模应用

### 6.4 最佳结界 overflow

想彻底清除浮动的影响，最适合的属性不是clear 而是 overflow，一般使用 overflow:hidden，利用BFC的“结界”特性彻底解决浮动对外部或兄弟元素的影响。

#### 6.4.1 overflow 剪裁界线 border box

当子元素内容超出容器宽度限制的时候，剪裁的边界是 border box 的内边缘，而非 padding box 的内边缘。

如果想实现元素剪裁同时四周留有间隙的效果，可以试试透明边框，此时内间距padding 属性是无能为力的

Chrome 浏览器下，如果容易可滚动，则padding-bottom 也算在滚动尺寸之内，IE和Firefox浏览器忽略padding-bottom

#### 6.4.2 了解 overflow-x 和overflow-y

支持的属性值和overflow一样

- visible：默认值
- hidden：剪裁
- scroll：滚动条区域一直存在
- auto：不足以滚动时没有滚动条，可以滚动时滚动条出现

除非overflow-x 和overflow-y 的属性值都是visible，否则visible会当成auto来解析

#### 6.4.3 overflow 与滚动条

1. 在PC端，无论什么浏览器，默认滚动条均来自于html，而不是body标签
    - PC端获取窗体滚动高度 document.documentElement.scrollTop
    - 移动端 document.body.scrollTop
2. 滚动条会占用容器的可用宽度或高度
    - IE7以上版本，Chrome、Firefox浏览器滚动栏所占据的宽度均是17px

#### 6.4.4 依赖 overflow 的样式表现

#### 6.4.5 overflow 与锚点定位

1. 锚点定位行为的触发条件
    1. URL地址中的锚链与锚点元素对应并有交互行为
    2. 可focus的锚点元素处于focus状态
2. 锚点定位作用的本质
    - 是通过改变容器滚动高度或宽度来实现的
    - 普通元素和窗体可同时滚动时，会由内而外触发所有可滚动窗体的锚点行为定位
    - 元素设置了overflow:hidden声明，里面内容高度溢出的时候，滚动依然存在，仅仅滚动条不存在
    - 基于父元素scrollTop 值来实现自定义滚动条效果
        1. 实现简单，边界无须判断
        2. 可与原生的scroll事件天然集成、无缝对接
        3. 无须改变子元素的结构
        4. 缺点：
            1. 无法添加类似Bounce回弹动效
            2. 渲染要比一般的渲染慢

### 6.5 float 的兄弟 position:absolute

当 absolute 和 float 同时存在的时候，float 属性是无任何效果的

元素一旦position属性为 absolute 或 fixed，其 display 计算值就是bloack或table

#### 6.5.1 absolute 的包含块

普通元素的百分比宽度是相对于父元素的 content box 宽度计算的，而绝对定位元素的宽度宽度是相对于第一个 position 不为 static 的祖先元素计算的

1. 根元素被称为初始包含块（很多情况是html根元素），其尺寸等于浏览器可视窗口的大小
2. 对于其他元素， 如果该元素的 position 是 relative 或者 statci，则包含块由其最近的块容器祖先盒的 content box 边界形成
3. 如果元素 position:fixed，则包含块是初始包含块
4. 如果元素 position:absolute，则包含块由最近的 position 不为static的祖先元素建立
    - 如果该祖先元素是纯inline元素，则规则略复杂
        - 假设给内联元素的前后各生成一个宽度为0的内联盒子，则这两个内联盒子的padding box 外面的包围盒就是内联元素的包含块
        - 如果该内联元素被跨行分割了，那么包含块是未定义的，也就是CSS2.1规范并没有明确定义，由浏览器自行发挥
    - 否则，包含块由该祖先的padding box边界形成

如果没有符合条件的祖先元素，则包含块是初始包含块

和常规元素相比，absolute 绝对定位元素的包含块有以下3个明显差异

1. 内联元素也可以作为包含块所在的元素
    1. absolute一般都是用来布局，而内联元素主要用来图文展示
    2. 理解和学习的成本比较高
        - 内联元素的包含块可以受::first-line伪元素影响，但不受::first-letter影响
        - 内联元素的包含块范围比较稳固，不会受line-height等属性影响
    3. 兼容性问题
        - Firefox浏览器的包含块仅覆盖第一行，而IE和Chrome浏览器包含块由第一行开头和最后一行结束的内联盒子共同决定
2. 包含块所在的元素不是父块级元素，而是最近position不为static的祖先元素或根元素
    - height:100%和height:inherit的区别
        - 对于普通元素，两者没什么区别
        - 对于绝对定位元素，height:100%是第一个具有定位属性值得祖先元素的高度，而height:inherit则是单纯的父元素的高度继承
3. 边界是padding box而不是content box

#### 6.5.2 具有相对特性的无依赖 absolute 绝对定位

absolute 是非常独立的CSS属性值，其样式和行为表现不依赖其他任何CSS属性就可以完成

1. 各类图标定位
2. 超越常规布局的排版
3. 下拉列表的定位
4. 占位符效果模拟
5. 进一步深入“无依赖绝对定位”
    - 虽然说元素position:absolute 后的display计算值都是块状的，但是其定位的位置和没有设置position:absolute 时候的位置相关

#### 6.5.3 absolute 与 text-align

text-align可以改变absolute元素的位置

具体的渲染原理如下：

1. 由于img是内联水平，p标签中存在一个宽度为0，看不见摸不着的幽灵空白节点，也是内联水平，于是受text-align:center影响而水平居中显示
2. img设置了position:absolute，表现为无依赖绝对定位，因此在幽灵空白节点后面定位显示，同时由于图片不占据空间，这里的幽灵空白节点正好在p元素水平中心位置显示，于是我们就看到图片从p元素水平中间位置显示的效果

### 6.6 absolute 与 overflow

绝对定位元素不总是被父级overflow属性剪裁，尤其当overflow在绝对定位元素及其包含块之间。

如果overflow不是定位元素，同时绝对定位元素和overflow容器之间也没有定位元素，则overflow无法对absolute元素进行剪裁

由于position:fixed固定定位元素的包含块是根元素，因此，除非是窗体滚动，否则所有overflow裁剪规则对固定定位都不适用

overflow元素自身transform的时候，Chrome和Opera浏览器下的overflow剪裁是无效的

当遇到absolute元素被剪裁或fixed固定定位失效时，可以看看是否是因为transform引起的

### 6.7 absolute 与 clip

clip属性要想起作用，position属性必须是absolute或fixed

#### 6.7.1 重新认识的clip属性

1. fixed固定定位的剪裁
2. 最佳可访问性隐藏

clip剪裁被称为最佳可访问性隐藏的原因是，它具有更强的普遍适应性，任何元素、任何场景都可以无障碍使用

#### 6.7.2 深入了解clip的渲染

使用clip进行剪裁的元素其clientWidth和clientHeight包括样式计算的宽高还是原来的大小

clip隐藏仅仅是决定了哪些部分是可见的，非可见部分无法响应点击事件等，虽然视觉上隐藏，但是元素的尺寸依然是原本的尺寸

### 6.8 absolute 的流体特性

#### 6.8.1 当absolute 遇到 left/top/right/bottom属性

#### 6.8.2 absolute的流体特性

绝对定位元素的流体特性成立的条件是：对立方向同时发生定位的时候

#### 6.8.3 absolute 的 margin:auto 居中

绝对定位元素的margin:auto的填充规则和普通流体元素一模一样

1. 如果一侧定值，一侧auto，auto为剩余空间大小
2. 如果两侧均是auto，平分剩余空间

### 6.9 position:relative 才是大哥

#### 6.9.1 relative 对 absolute 的限制

relative让absolute元素依然保持在正常的文档流中

#### 6.9.2 relative 与定位

relative定位有两大特性：一是相对自身，二是无侵入

相对定位元素的left\top\right\bottom的百分比值是相对于包含块计算的，而不是自身

top和bottom这两个垂直方向的百分比值得计算跟height一致，都是相对高度计算的，如果包含块的高度是0，那么计算值为0，偏移无效

当相对定位元素同时应用对立方向定位值得时候，也就是top\bottom，left\right同时使用的时候，只有一个方向的定位属性会起作用，这与文档流的顺序有关，默认的文档流是从上至下，从左到右

#### 6.9.3 relative的最小化影响原则

1. 尽量不适用relative，如果想定位某元素，看看能否使用无依赖的绝对定位
2. 如果一定要用relative，则该relative务必最小化

### 6.10 强悍的position:fixed 固定定位

#### 6.10.1 position:fixed不一样的包含块

position:fixed固定定位元素的包含块是根元素，可以近似看成html元素

无依赖的固定定位，利用absolute\fixed元素没有设置left\top\right\bottom的相对定位特性，可以将目标元素定位到想要的位置

#### 6.10.2 position:fixed 的 absolute 模拟

希望元素既有不跟随滚动的固定定位效果，又能被定位元素限制和精准定位

页面的滚动使用普通元素替代，此时滚动元素之外的其它元素自然就有了“固定定位”效果

#### 6.10.3 position:fixed 与背景锁定

- 如果是移动端项目，阻止touchmove事件的默认行为就可以阻止黑幕下的元素滚动
- 如果是桌面端项目，可以让根元素直接overflow:hidden
    - 但是Windows操作系统下的浏览器的滚动条占据了一定宽度，滚动条的消失必然会导致页面的可用宽度发生变化，页面会产生晃动问题
    - 解决方案：消失的滚动条可以用同等宽度的透明边框填充

## 第7章 CSS世界的层叠规则

层叠规则指的是网页中的元素发生层叠时的表现规则

### 7.1 z-index只是CSS层叠规则中的一叶小舟

z-index属性只有和定位元素（position不为static的元素）在一起时才有作用

z-index并非只对定位元素有效，flex盒子的子元素也可以设置z-index属性

### 7.2 理解CSS世界的层叠上下文和层叠水平

#### 7.2.1 什么是层叠上下文

#### 7.2.2 什么是层叠水平

层叠水平决定了同一个层叠上下文中元素在z轴上的显示顺序

### 7.3 理解元素的层叠顺序

层叠顺序表示元素发生层叠时有着特定的垂直显示顺序

从上到下依次是：

1. 正z-index
2. z-index:auto或者z-index:0
3. inline水平盒子
4. float浮动盒子
5. block块状水平盒子
6. 负z-index
7. 层叠上下文 background/border

补充说明：

1. 位于最下面的background/border特指层叠上下文元素的边框和背景色
2. inline水平盒子指的是包括inline/inline-block/inline-table元素的层叠顺序，它们都是同等级别的
3. 单纯从层叠水平看，z-index:auto 和 z-index:0 可以看成是一样的

### 7.4 务必牢记的层叠准则

当元素发生层叠的时候，其覆盖关系遵循下面两条准则：

1. 谁大谁上：当具有明显的层叠水平标识的时候，如生效的z-index属性值，在同一个层叠上下文领域，层叠水平值大的那一个覆盖小的那一个
2. 后来居上：当元素的层叠水平一致，层叠顺序相同的时候，在DOM流中处于后面的元素会覆盖前面的元素

### 7.5 深入了解层叠上下文

#### 7.5.1 层叠上下文的特性

层叠上下文具有如下特性：

1. 层叠上下文的层叠水平要比普通元素高
2. 层叠上下文可以阻断元素的混合模式
3. 层叠上下文可以嵌套，内部层叠上下文及其所有子元素均受制于外部的层叠上下文
4. 每个层叠上下文和兄弟元素独立，当进行层叠变化或渲染的时候，只需要考虑后代元素
5. 每个层叠上下文是自成体系的，当元素发生层叠的时候，整个元素被认为是在父层叠上下文的层叠顺序中

#### 7.5.2 层叠上下文的创建

1. 页面根元素天生具有层叠上下文
    - 可以看成是html标签，所以页面中的所有元素一定处于至少一个层叠上下文中
2. z-index值为数值的定位元素
    - 对于position值为relative/absolute以及Firefox/IE浏览器（不包含Chrome）下含有position:fixed声明的定位元素，当其z-index值不为auto的时候，会创建层叠上下文
    - 页面重构的时候发现z-index嵌套错乱，可能是因为受父级的层叠上下文元素干扰了
    - Chrome等webkit内核浏览器下position:fixed元素天然层叠上下文元素
3. 其他CSS3属性
    1. 元素为flex布局元素（父元素display:flex|inline-flex），同时z-index值不为auto
    2. 元素的opacity值不是1
    3. 元素的transform值不是none
    4. 元素的mix-blend-mode值不是normal
    5. 元素的filter值不为none
    6. 元素的isolation值是isolate
    7. 元素的will-change属性值为上面2~6任意一个
    8. 元素的-webkit-overflow-scrolling设为touch

#### 7.5.3 层叠上下文与层叠顺序

1. 如果层叠上下文元素不依赖z-index的值，则其层叠顺序是z-index:auto，可看成z-index:0级别
2. 如果层叠上下文元素依赖z-index数值，则层叠顺序由z-index的值决定

定位元素层叠在普通元素上的原理：

- 元素一旦成为定位元素，z-index就会自动生效，此时z-index的值为auto，也就是0级别，所以就被覆盖inline、block、float元素

不支持z-index的层叠上下文元素天然就是z-index:auto级别，所以层叠上下文元素和定位元素是一个层叠顺序的，当它们发生重叠时，遵循后来居中原则

### 7.6 z-index 负值深入理解

z-index负值元素的层级是在层叠上下文元素上面、block元素下面

z-index负值的实际用处

1. 可访问性隐藏
2. IE8下的多背景模拟
3. 定位在元素后面

### 7.7 z-index的不犯二原则

对于非浮层元素，避免设置z-index值，z-index值没有任何道理需要超过2

1. 定位元素一旦设置了z-index值，就从普通定位元素变为层叠上下文元素，相互间的层叠顺序就发生了根本的变化，很容易出现设置了巨大的z-index值也无法覆盖其他元素的问题
2. 避免z-index出现样式混乱问题

## 第8章 强大的文本处理能力

### 8.1 line-height 的另外一个朋友 font-size

#### 8.1.1 font-size 和 vertical-align 的隐秘故事

line-height 的部分类别属性值是相对于 font-size 计算的，vertical-align 百分比值属性值又是相对于 line-height 计算的，所以 vertical-align 和 font-size 属性有时也是有关联的。

#### 8.1.2 理解 font-size 与 ex、em 和 rem 的关系

ex 是字符高度，font-size 值越大，自然 ex 对应的大小也越大

em 是字模的高度，不是字符的高度，1em 的计算值等同于当前元素所在的 font-size 的计算值

要想实现带有缩放性质的弹性布局，使用 rem 是最佳策略，但是 rem 是 CSS3 的单位，IE9 以上才兼容

如果我们使用 SVG 图标，可以使用 em 做单位，这样无论图标是和大号文字还是和小号文字在一起，都能和当前文字大小保持一致

#### 8.1.3 理解 font-size 的关键字属性值

font-size 支持长度值，也支持百分比值，还支持关键字属性值

font-size 的关键字属性值分为以下两类

1. 相对尺寸关键字
    - larger：big 元素默认的 font-size 属性值
    - smaller：small 元素默认的 font-size 属性值
2. 绝对尺寸关键字：与当前元素 font-size 无关，仅受浏览器设置的字号影响
    - xx-large：和 h1 元素计算值一样
    - x-large：和 h2 元素计算值一样
    - large：和 h3 近似
    - medium：默认值，和 h4 元素计算值一样
    - small： 和 h5 近似
    - x-small：和 h6 近似
    - xx-small：无对应 HTML 元素

如何设置响应式：

1. 即使是定宽的传统桌面端网页，也需要做响应式处理，尤其是针对 1200 像素宽度设计的网页，但只需要响应到 800 像素即可，可以保证至少有 1.5 倍的缩放空间
2. 如果因各种元素无法做响应式处理，也没有必要全局都使用相对单位，只需在图文内容为主的重要局部区域使用可缩放的 font-size 处理即可
    - 容器设置 font-size:medium
    - 容器内的文字字号全部使用相对单位，如百分比或 em

#### 8.1.4 font-size:0 与文本的隐藏

桌面 Chrome 浏览器文字的 font-size 计算值不能小于 12px

如果 font-size 字号为 0，那么文字会直接被隐藏，哪怕 font-size 的值为 0.000000001px，也会被处理成 12px，所以如果要隐藏 logo 对应元素的文字，除了 text-indent 缩进隐藏外，还可以设置 font-size:0

### 8.2 字体属性家族的大家长 font-family

font-family默认值由操作系统和浏览器共同决定

font-family 支持两类属性值，一类是“字体名”，一类是“字体族”

1. 字体族就是使用的对应字体的名称，如果字体包含空格，就需要用引号包起来
2. 字体族类别
    - serif:衬线字体
    - sans-serif:无衬线字体
    - monospace:等宽字体
    - cursive:手写字体
    - fantasy:奇幻字体
    - system-ui:系统 UI 字体

#### 8.2.1 了解衬线字体和无衬线字体

字体分衬线字体和无衬线字体。

衬线字体就是笔画开始、结束的地方有额外装饰而且笔画的粗体会有所不同的字体

无衬线字体没有这些额外的装饰，而且笔画的粗细都差不多

大多数浏览器下，卸载 serif 和 sans-serif 后面的字体都会被忽略

#### 8.2.2 等宽字体的实践价值

东亚字体都是等宽的，就是每个字符在同等 font-size 下占据的宽度是一样的

1. 等宽字体与代码呈现
    - 等宽字体利于代码呈现
2. 等宽字体与图形呈现
3. ch 单位与等宽字体布局
    - 1ch 表示一个 0 字符的宽度

#### 8.2.3 中文字体与英文字体

为了规避乱码的风险，字体的属性值一般不使用中文，而是使用英文名称

1. windows 常见内置中文字体和对应英文名称

    | 字体中文名 | 字体英文名 |
    | --- | --- |
    | 宋体 | SimSun |
    | 黑体 |  SimHei |
    | 微软雅黑 | Microsoft Yahei |
    | 微软正黑体 | Microsoft JhengHei |
    | 楷体 | KaiTi |
    | 新宋体 | NSimSun |
    | 仿宋 | FangSong |
2. OS X系统内置中文字体与对应英文名称

    | 字体中文名 | 字体英文名 |
    | --- | --- |
    | 苹方 | PingFang SC |
    | 华文黑体 | STHeiti |
    | 华文楷体 | STKaiti |
    | 华文宋体 | STSong |
    | 华文仿宋 | STFangsong |
    | 华文中宋 | STZhongsong|
    | 华文琥珀 | STHupo |
    | 华文新魏 | STXinwei |
    | 华文隶书| STLiti |
    | 华文行楷 | STxingkai |
    | 冬青黑体简 | Hiragino Sans GB |
    | 兰亭黑-简 | Lantinghei SC |
    | 翩翩体-简 | Hanzipen SC |
    | 手札体-简 | Hannotate SC |
    | 宋体-简 | Songti SC |
    | 娃娃体-简 | Wawati SC |
    | 魏碑-简 | Weibei SC |
    | 行楷-简 | Xingkai SC |
    | 雅痞-简 | Yapi SC |
    | 圆体-简 | Yuanti SC |
3. Office 软件安装新增中文字体和对应英文名称

    | 字体中文名 | 字体英文名 |
    | --- | --- |
    | 幼圆 |  YouYuan |
    | 隶书 | LiSu |
    | 华文细黑 | STXihei |
    | 华文楷体 | STKaiti |
    | 华文宋体 | STSong |
    | 华文仿宋 | STFangsong|
    | 华文中宋 | STZhongsong |
    | 华文彩云 | STCaiyun |
    | 华文琥珀| STHupo |
    | 华文新魏 | STXinwei |
    | 华文隶书 | STLiti |
    | 华文行楷 | STxingkai |
    | 方正舒体 | FZShuTi |
    | 方正姚体 | FZYaoti |
4. 其他一些中文文字和对应英文名称

    | 字体中文名 | 字体英文名 |
    | --- | --- |
    | 思源黑体 | Source Han Sans CN |
    | 思源宋体 | Source Han Serif SC |
    | 文泉驿微米黑 | WenQuanYi Micro Hei |

#### 8.2.4 一些补充说明

OS X 中字体名称中的“SC”指的是简体，“TC”值得是繁体

英文名称最好首字母要大写，可以避免使用 CSS unicode-range 时可能遇到的麻烦
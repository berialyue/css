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

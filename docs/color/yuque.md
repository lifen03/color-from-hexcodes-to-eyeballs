[原文地址](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0)

作者：[Jamie Wong](http://jamie-wong.com/)@创作时间：2018-04-03  

*翻译&校验：[freedom](https://github.com/yylifen)*

## 摘要

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/Hero.png)

这篇文章也有俄语版本：[Цвет：отшестнадцатеричныхкодовдоглаза](https://habr.com/post/353582/)，和日语版本：色：[ヘキサコードから眼球まで](https://postd.cc/color/)。

为什么我们能感觉到`background-color: #9B51E0`是特定的紫色？

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/Purple.png)

很早我就认为这是我已经知道答案的问题之一，但是在我审视我对这个问题的认知时，我意识到这里面存在相当大的误解。

通过对电磁辐射、光学生物学、色度学和显示硬件的探索，我希望能开始填补其中的一些空白。如果你想跳过前面，下面是我们将要涉及到的领域：

+ [电磁辐射](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#electromagnetic-radiation)

+ [可见光](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#visible-light)

+ [人类感知亮度](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#human-perceived-brightness)

+ [量化色彩](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#quantifying-color)

+ [光学生物学](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#optical-biology)

+ [色彩空间](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#color-spaces)

+ [Wright和Guild的配色实验](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#wright-guild-s-color-matching-experiments)

+ [可视化色彩空间和色度](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#visualizing-color-spaces-chromaticity)

+ [色域和光谱轨迹](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#gamuts-and-the-spectral-locus)

+ [CIE XYZ色彩空间](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#cie-xyz-color-space)

+ [屏幕子像素](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#screen-subpixels)

+ [sRGB](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#srgb)

+ [sRGB十六进制编码](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#srgb-hexcodes)

+ [伽玛校正](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#gamma-correction)

+ [从十六进制编码到眼球](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#from-hexcodes-to-eyeballs)

+ [关于亮度设置的简要说明](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#a-brief-note-about-brightness-setting)

+ [补充](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#stuff-i-left-out)

+ [参考](http://jamie-wong.com/post/color/?from=groupmessage&isappinstalled=0#references)

现在，让我们从物理学开始吧。

## 电磁辐射

无线电波、微波、红外、可见光、紫外线、x射线和伽马射线都是电磁辐射的形式。虽然这些东西都有不同的名称，但这些名称实际上只是在电磁光谱中标记不同的波长范围。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/electromagneticSpectrum.png)

*电磁波谱*

电磁辐射的最小单位是光子。光子中包含的能量与其对应波的频率成正比，高能光子对应于高频波。

要真正理解色彩，我们首先需要了解辐射。让我们仔细看看白炽灯泡的辐射。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/incandescent.png)

*照片来自[Alex Iby](https://unsplash.com/photos/HfR0W6HW_Cw)*

我们可能想知道灯泡辐射了多少能量。物体的**辐射通量**![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/10.svg)是每秒发射的总能量，以瓦茨为单位。100W白炽灯泡的辐射通量约为80W，其余20W直接转化为无辐射热。

如果我们想知道每个波长产生了多少能量，我们可以看看**光谱通量**。一个物体的光谱通量![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/11.svg)是单位波长的辐射通量，通常以瓦茨/纳米计测量。

如果我们将白炽灯泡的光谱通量绘制为波长的函数，它可能看起来如下所示：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/SpectralFlux1.png)

这条曲线下的面积将给出辐射通量。作为方程，![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/3.svg)。在这种情况下，曲线下的面积约为80W。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/SpectralFlux2.png)

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/1.svg)

现在你可能已经从环保运动中听说白炽灯灯泡效率很低，你可能会想，“好吧，80%的白炽灯看上去并不那么糟糕”。

这是真的-白炽灯泡是将电转化为辐射的一种非常有效的方法。不幸的是，这也是一种将电转化为人类可见辐射的可怕方法。

## 可见光

可见光是电磁辐射的波长范围，从![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/6.svg)到![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/2.svg)。在我们的白炽灯泡图上，那是下面的阴影区域。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/SpectralFlux3.png)

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/12.svg)

因此，在可见光谱中辐射的能量为![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/32.svg)，效率为![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/33.svg)。这似乎很可怕。但情况变得更糟。

为了理解为什么，让我们考虑一下为什么可见光是可见的。

## 人类感知到的亮度

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/bweye.png)

*照片来自[Christopher Burns](https://unsplash.com/photos/QaGNhezu_5Q)*

正如我们看到白炽灯泡在所有波长上的辐射都不一样，我们的眼睛对所有波长的辐射敏感度也都不一样。如果我们测量人眼对每个波长的敏感度，就会得到一个光度函数。标准光度函数![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/8.svg)如下所示：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/SpectralFlux4.png)

这个光度函数的界限定义了可见光的范围。任何超出这个范围的东西都是看不见的，因为我们的眼睛对它不敏感！

这条曲线还表明，我们的眼睛对**550nm**处的辐射比在**650nm**和**450nm**时对辐射更敏感。

其他动物的眼睛对不同的波长范围很敏感，为此有不同的光度功能。鸟类可以看到的紫外线辐射范围为：从![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/5.svg) 到 ![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/7.svg)，因此，如果鸟类学者已经定义了电磁光谱，那就属于它们的“可见光”范围了！。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/owl.png)

*照片来自[Timothy Rhyne](https://unsplash.com/photos/0J6cTw0V2lE)*

通过将光谱通量图与光度函数![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/8.svg)​相乘，我们得到了一个描述光源发射的每个波长对人类感知亮度的贡献函数。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/SpectralFlux5.png)

这是**光谱光通量**![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/9.svg)​。为了承认这是人类的感知，而不是客观的力量，光通量通常用流明（lm）而不是瓦茨(W)来测量，其转换比为**683.002lm/W**。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/4.svg)​

光源的**光通量**![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/31.svg)​是人类感知到的光的总功率。

正如我们通过取光谱通量曲线下的面积来计算辐射通量一样，我们也可以根据光谱光通量曲线下的面积来求出光通量，并将感知到的瓦特转换为流明：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/SpectralFlux5.5.png)

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/16.svg)​

因此，我们的100W白炽灯泡的光通量仅为2.4W或1600磅！该灯泡的发光效率为2.4%，远低于80%的效率将电能转化为辐射。

也许，如果我们有一个光源，集中它的发射到可见范围，我们将能够获得更有效的照明。让我们比较一下白炽灯、荧光灯和LED灯泡的光谱：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/SpectralFlux6.png)

事实上，我们可以看到，荧光或LED灯泡中的辐射被浪费在人类看不见的波长上。如果白炽灯灯泡的效率可能达到13%，荧光灯可以达到10%的效率，LED灯泡可以达到20%的效率！

关于亮度已经说了够多，让我们回到这篇文章的焦点：色彩！

## 量化色彩

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/lemon.png)

*照片来自[Lauren Mancke](https://unsplash.com/photos/sil2Hx4iupI)*

我们如何识别给定的色彩？如果我面前有柠檬，我怎么能通过电话告诉你它是什么色彩的？我也许会告诉你“柠檬是黄色的”，但是哪个是黄色的呢？你如何准确地识别每一种黄色？

![](https://d2mxuefqeaa7sj.cloudfront.net/s_382135F512C449943D36A9C35B9E8A4F38EB382A3D72DF63DC63D011CB7A8322_1521414272066_Yellows.png)

由于了解到色彩是人类对电磁辐射的解释，我们可能会倾向于通过光谱通量从数学上定义色彩。任何人类可见的色彩将是一些加权组合单色(单波长)的色彩。单色色彩也称为光谱色彩。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/Rainbow.png)

*波长单色*

对于任何给定的物体，我们都可以测量它的发射(或反射率)光谱，并利用它精确地识别色彩。如果我们能复制光谱，我们当然可以复制色彩！

从柠檬上反射出来的阳光可能有这样的反射光谱：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/ReflectanceSpectrum.png)

*注：到达你眼睛的辐射的功率和光谱分布将取决于光源的功率和发射光谱、光源与被照明物体的距离、物体的大小和形状、物体的吸收光谱、以及你与物体的距离。这是要考虑很多问题，所以让我们关注一下当光线照射到你的眼睛时会发生什么。让我们现在暂时不考虑单元，先关注概念。*

当这种光谱分布的能量击中我们的眼睛时，我们就把它看作是“黄色”。现在，假设我拍了一张柠檬的照片，然后上传到我的电脑上。接下来，我仔细地调整屏幕上的色彩，直到屏幕上的柠檬的一个特定点与我实际手中的实际柠檬的色彩有了很大的不同。

如果你要测量屏幕上的频谱功率分布，你会期望分布看起来像什么？你可以合理地期望它看起来类似于上面柠檬的反射光谱。但实际上它看起来是这样的：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/EmissionSpectrum.png)

对于人类观察者来说，两种不同的光谱功率分布看起来是相同的，它们被称为[“元”](https://en.wikipedia.org/wiki/Metamerism_(color))。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/Metamers1.png)

为了理解这是如何发生的，让我们来看看眼睛的生物学。

## 光学生物学

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/coloreye.png)

*照片来自[Amanda Dalbjörn](https://unsplash.com/photos/UbJMy92p8wk)*

我们对光的感知是我们眼睛中特殊的称为“视杆细胞”和“视锥细胞”的责任。视杆细胞在弱光环境下非常重要，而且在彩色视觉中也不起多大作用，所以我们将重点放在视锥细胞上。

人类通常有3种视锥细胞。三种不同的视锥细胞，使人类成为“三色视者 ”。然而，至少有一个[人类的确诊病例](http://nymag.com/scienceofus/2015/02/what-like-see-a-hundred-million-colors.html)是四色视者！其他动物有更多的视锥细胞种类。[螳螂虾](http://theoatmeal.com/comics/mantis_shrimp)有十六种不同的视锥细胞。

每种视锥细胞都被它们激发的波长范围所标记。标准标签是“**S**”、“**M**”和“**L**”(短、中、长)。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/Cones.png)

这三条曲线表明对应的视锥细胞对每个波长有多敏感。每条曲线上的最高点称为“峰值波长”，表示视锥细胞最敏感的辐射波长。

让我们看看我们的视锥细胞是如何处理光从我手里的柠檬反射出来的。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/ConeExcitation1.png)

通过观察曲线下的归一化区域，我们可以看到真实柠檬反射的辐射对每个视锥细胞的刺激程度。在这种情况下，**S**、**M**和**L**锥的归一化激发分别为0.02、0.12和0.16。现在让我们对屏幕上的柠檬重复这个过程。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/ConeExcitation2.png)

尽管到达眼睛的辐射光谱完全不同，但视锥细胞激发的结果是相同的<b>(S=0.02，M=0.12，L=0.16)</b>。这就是为什么真正的柠檬和数字柠檬在我们看来是一样的根本原因！

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/Metamers2.png)
*在变异构体的情况下，对于刺激所有3种视锥细胞类型曲线下的归一化锥面积始终相等。*

我们的3组视锥细胞将任意谱通量曲线![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/19.svg)​降为三重组![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/30.svg)​，每个不同的![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/30.svg)​三个量度都是不同的色彩！这非常方便，因为(0.02，0.12，0.16)比一个复杂的连续函数更容易通信。对于数学上的倾向，我们的眼睛正在做一个从无限维空间到三维的维度缩减，这是一件非常酷的事情，能够在潜意识中完成。

这![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/30.svg)​三个量度实际上是我们关于**色彩空间**的第一个例子。

## 色彩空间

色彩空间允许我们精确地定义我们正在谈论的色彩。在上一节中，我们看到在SML色彩空间中，特定的黄色可以表示为(0.02，0.12，0.16)，这通常被称为[LMS色彩空间](https://en.wikipedia.org/wiki/LMS_color_space)。

由于这个色彩空间描述的是对视锥细胞的刺激，根据定义，任何人类可见的色彩都可以用正的LMS坐标来表示(不包括极罕见的四色视者，他们需要四个坐标而不是三个坐标)。

但是，唉，这个色彩空间也有一些无用的属性。

首先，并不是所有的三重态值(也称为**三刺激值**)在物理上都是可能的。考虑LMS坐标(0，1，0)。为了在物理上实现这个坐标，我们需要找到刺激M锥的方法，而不需要刺激L或S锥。由于M锥的灵敏度曲线在所有波长上都明显重叠于L或S中的至少一个，这是不可能的！

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/Cones.png)

*任何刺激M锥的波长也会刺激L锥或S锥(或两者兼而有之)。*

这个事实的一个有问题的副作用是很难只增加对其中一个锥的刺激。特别是，这将使它不是一个很好的选择，以构建显示硬件。

另一个历史上的、实用的问题是，直到20世纪90年代，视锥细胞的敏感性才被准确地知道，而在此之前，需要建立一个精确的色彩数学模型。在20世纪20年代末产生了这方面的第一个重大进展。

## Wright和Guild的配色实验

20世纪20年代末，威廉·大卫·赖特(William David Wright)和约翰·吉尔德(John Guild)进行了实验，用3个特定波长的光精确地定义色彩。

尽管他们可能还不知道眼睛里有三种色彩，但至少早在一百年前就有人提出了这样的观点，即所有可见的色彩都可以由三种色彩组合而成。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/tricolor.png)

*查尔斯·海特(Charles Hayter，1826)关于三色理论的一个例子*

Wright和Guild的想法是，建造一种仪器，让测试对象将三种固定波长光源组合在一起，重建测试色彩。设置应该如下所示：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/ColorMatching1.png)

实验者将底部的灯设置为目标波长(例如600nm)，然后要求被试调整三种灯的功率控制，直到它们看到的色彩匹配为止。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/ColorMatching2.png)

这三个刻度盘的功率设置给我们一个(红色，绿色，蓝色)三重识别与600nm相关的纯光谱色彩。每5nm对大约10名被试重复这一过程，一个图表显示了重建给定波长的外观所需的红色(700nm)、绿色(546nm)和蓝色(435nm)光的数量。这些函数被称为**色彩匹配函数(CMFs)**。

这些特殊的色彩匹配函数称为![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/21.svg)​、![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/23.svg)​和![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/13.svg)​。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/cmfs1.png)

这给出了与600nm每个![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/27.svg)​坐标(0.34，0.062，0.00)相关的纯光谱色彩。这是[CIE 1931年RGB色彩空间](https://en.wikipedia.org/wiki/CIE_1931_color_space#CIE_RGB_color_space)中的一个值。

等等，当函数变成负值是什么意思，就像这里？

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/cmfs2.png)

与500nm相关的纯光谱色的![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/27.svg)坐标为(-0.72，0.85，0.48)。那么-0.72到底是什么意思？

事实证明，无论你把红色(700nm)刻度盘设置到什么位置，都不可能匹配500nm的输出光，不管蓝色和绿色刻度盘的值是多少。然而，你可以通过在底部加上红灯来使两面相匹配。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/ColorMatching3.png)

实际设置可能会有一套完整的3种可变功率，固定波长灯的任何一边的分频器，以允许他们中的任何一个调整为负值。

利用我们的配色功能，我们可以使用(可能是负的)红色(700nm)、绿色(546nm)和蓝色(435nm)光的组合来匹配任何单色光。

就像我们能够用L，M，S锥灵敏度函数来确定任何光谱分布的锥激励一样，我们也可以用我们的配色函数来做同样的事情。让我们把它应用到之前的柠檬色中：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/ColorMatchingLemon.png)

通过取光谱曲线乘积下的面积和配色函数，我们得到一个![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/27.svg)三重态(1.0，0.8，0.2)唯一识别这种色彩。

而![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/30.svg)色彩空间给了我们一种精确的色彩识别方法，而这个![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/27.svg)色彩空间为我们提供了一种精确的色彩再现方法。但是，正如我们在配色函数中所看到的，任何带有负![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/27.svg)坐标的色彩都不能被实际再现。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/cmfs3.png)

但这张图只显示哪些光谱色彩不能再现。非光谱色彩呢？我能用R，G，B组合出粉红色吗？那蓝绿色呢？

要回答这些问题，我们需要一种更好的可视化色彩空间的方法。

## 色彩空间的视觉化与色度

到目前为止，我们的大多数图表都将波长放置在水平轴上，我们绘制了多个系列来表示其他感兴趣的值。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/WavelengthPlots.png)

相反，我们可以把色彩绘制成![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/27.svg)或![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/30.svg)的函数。让我们看看在3D![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/27.svg)空间中绘制的色彩是什么样子的。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/LinearRGBCube.png)

太棒了!这给了我们一种更广泛的色彩的可视化，而不仅仅是彩虹的光谱色彩。

将其降到两个维度的一个简单方法是为每一对值都有一个单独的图，如下所示：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/RGBPairPlots.png)

*绘制组件对，保持第三个坐标常数*

在每一个场景中，我们通过保持一个常量来丢弃一维。与其保持一个红色、绿色和蓝色的常量，不如有一个场景显示彩虹的所有色彩以及它们的组合，同时保持亮度不变。

再看看立方体图片，我们可以看到(0，0，0)是黑色的，(1，1，1)是白色的。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/LinearRGBCube.png)

如果我们在包含(1，0，0)，(0，1，0)和(0，0，1)的平面上对角地分割立方体会发生什么？

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/TriangleSliceRGB.png)

这个立方体的三角形切片具有![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/17.svg)的性质，我们可以用![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/34.svg)作为亮度的粗略逼近。如果我们对这个三角形切片进行自顶向下的观察，我们会得到这样的结果：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/rgChromaticity1.png)

这种色彩的二维表示称为**色度**。这种特殊的色彩叫做[**Rg色度**](https://en.wikipedia.org/wiki/Rg_chromaticity)。色度为我们提供了与亮度无关的原色比例的信息。

这意味着我们可以有相同的色度在许多不同的强度。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/rgChromaticity2.png)

我们甚至可以制作一个色度图，其中强度随r和g的变化，以使强度最大化，同时保持**R**、**G**和**B**之间的比率。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/rgChromaticity3.png)

色度是一种有用的要考虑的色彩特性，因为只要光源保持相同的光谱分布，它就会随着光源的强度变化而保持不变。当你改变你的屏幕的亮度，色度是保持不变的东西！

把色度分为两个维度有许多不同的方法。其中一种常用的方法是在**HSL**和**HSV**色彩空间中使用。这两个色彩空间将色度分为“色调”和“饱和度”，如下所示：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/HSL.png)

乍一看，Rg色度三角形和这些色调与饱和度平方包含了彩虹的每一种色彩。是时候重新审视我们的配色函数中那些讨厌的负值了。

## 伽玛与光谱轨迹

如果我们使用色彩匹配函数![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/21.svg)​、![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/23.svg)​和![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/13.svg)​，并使用它们来绘制光谱色彩的Rg色度，我们将得到这样一个图：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/rgChromaticityPlot1.png)

带有彩色点的黑色曲线显示了所有纯光谱色彩的色度。这条曲线被称为**光谱轨迹**。用星星标记在色彩匹配实验中使用的可变功率测试灯的波长。

如果我们将以前的色度三角形叠加到这张图表上，我们就会发现：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/rgChromaticityPlot2.png)

光谱轨迹内的区域代表了所有对人类可见的色度。棋盘区域代表了人类可以识别的色度，但它不能通过任何435nm、546nm和700nm光的正组合来再现。从这张图中，我们可以看到，我们无法复制任何在435nm到546nm之间的光谱色彩，其中包括纯青色。

右边没有棋盘的三角形是所有可以通过正组合再现的色度。我们把可以复制的区域称为色彩空间的**色域**。

在我们最终返回到十六进制编码之前，我们还有一个需要覆盖的色彩空间。

## CIE XYZ色彩空间

1931年，国际照明学会召集并创造了两个色彩空间。第一个是我们已经讨论过的RGB色彩空间，它是根据Wright和Guild的色彩匹配实验结果创建的。第二个是XYZ色彩空间。

XYZ色彩空间的目标之一是对所有人类可见色彩都有正值，因此在两个轴上，所有色度都在[0，1]范围内。为此，仔细选择了RGB空间的线性变换。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/15.svg)

对于XYZ空间，Rg色度的模拟是XY色度，是用于色度图的更标准的坐标系。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/xyChromaticityPlot.png)

GAMUT通常由放置在XY色度图中的三角形表示。例如，这是CIE RGB的范围，这次是在XY空间。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/gamut1.png)

随着对色域和色度的理解，我们终于可以开始讨论数字显示器如何能够显示预定的色彩。

## 屏幕子像素

不管你的显示器是哪个制造商，如果你使用一个强大的放大镜来显示，你将发现一个像素网格，其中每个像素由3种类型的子像素组成：一种是发射红色、一种是发射绿色和一种是发射蓝色。它看起来可能是这样的：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/Subpixels.png)

与在配色实验中使用的测试灯不同，亚像素不发射单色光。每种亚像素都有它自己的光谱分布，而且每个设备都有不同的光谱分布。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/subpixelSpectra.png)

*MacBook Air按[频率计](https://fluxometer.com/rainbow/)的亚像素光谱数据*

使用Macbook Pro上的ColeSync实用程序，我能够确定屏幕的XY空间范围。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/gamut3.png)

注意，色域的角不再沿着光谱轨迹。这是有道理的，因为亚像素不发射纯单色光。这个色域代表了这个监视器可以忠实地再现的全部色度。

虽然监视器的色域会有所不同，但现代监视器应该试图包含另一个特定的范围：sRGB。

## sRGB

sRGB(“标准红绿蓝”)是惠普和微软在1996年创建的一个色彩空间，以帮助确保在媒体之间忠实地传输色彩数据。

该标准指定了红色、绿色和蓝色原色的色度。

| 色度 | 红 | 绿 | 蓝 |
| :----: | :----: | :----: | :----: |
| x |   0.6400 |	0.3000 |	0.1500 |
| y |	0.3300 |	0.6000 |    0.0600 |
| Y |	0.2126 |	0.751 |    0.0722 |

如果我们绘制这些图形，我们最终会得到一个类似于MacBook LCD屏幕但略小于MacBook LCD屏幕的色域。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/gamut2.png)

有一些官方的sRGB色域不在MacBook Pro LCD色域中，这意味着LCD不能如实地复制它们。为了适应这种情况，我的MacBook似乎使用了修改后的sRGB色域。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/gamut4.png)

sRGB是几乎在任何地方使用的默认色彩空间，也是浏览器使用的标准色彩空间([在CSS标准中指定](https://www.w3.org/TR/css-color-4/#color-type))。这篇博客文章中的所有图表都在sRGB色彩空间中。这意味着，sRGB色域之外的所有色彩都不能在本文中的图表中准确地再现！

这就引出了我们最后一个问题，如何在网络上指定色彩。

## sRGB十六进制编码

`#9B51E0`指定sRGB空间中的色彩。为了将其转换为关联的![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/27.svg)坐标，我们将这三个组件除以0xFF(又名255)。在这种情况下：

> 0x9B/0xFF = 0.61
>
> 0x51/0xFF = 0.32
>
> 0xE0/0xFF = 0.88
>

因此，与`#9BE1E0`相关的坐标是![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/20.svg)。

在我们将这些值发送到显示硬件设置亚像素强度之前，只有一个步骤：伽马校正。

## 伽马校正

当RGB空间中的每个坐标被赋予256个可能的值时，我们希望确保每个相邻的对尽可能不同。例如，我们希望`#030000`与`#040000`不同，因为`#F40000`与`#F50000`不同。

人类的视觉对低能灯的微小变化比对高能灯的小变化更敏感，因此我们希望将256个数值中的更多的值分配给代表低能值。

为了了解如何实现，让我们想象一下，我们希望编码灰度值，但只有3位，给出了8个可能的值。

如果我们把灰色值画成能量的线性函数，它会是这样的：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/linearEnergy.png)

我们将调用我们的3位编码值**Y**。如果我们的编码方案平均编码每个值![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/25.svg)，则如下所示：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/gamma1.png)

可以看出，![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/28.svg)和![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/24.svg)的知觉差异显著大于![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/26.svg)和![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/22.svg)的差异。

现在让我们来看看如果我们用幂函数来代替它会发生什么。让我们试试![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/29.svg).

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/gamma2.png)

我们在这里越来越接近于感知的一致性，在这里，每一对相邻的值都和其他相邻的值一样不同。

这种获取能量值并将其映射到离散值的过程称为**伽马编码**。逆运算(将离散值转换为能量值)称为**伽马解码**。

一般情况下，伽马校正方程![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/18.svg)。指数是希腊字母“伽马”，因此这个名字。

sRGB的编码和解码规则使用类似的思想，但稍微复杂一些。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/14.svg)

如果我们根据线性值绘制sRGB值，则如下所示：

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/gamma3.png)

太好了!这是我们要了解的最后一块，看看我们是如何从十六进制编码到眼球的！让我们进行演练😀。

## 从十六进制编码到眼球

首先，我们取`#9B51E0`，将其分解为R，G，B分量，并将这些分量规范化为![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/35.svg)范围。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/summary1.png)

这给出了sRGB空间中的坐标为![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/20.svg)。接下来，我们使用sRGB组件并将它们转换为线性值。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/summary2.png)

这给出了线性RGB空间中的坐标![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/36.svg)。这些值用于设置屏幕上子像素的强度。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/summary3.png)

子像素的谱分布与整个像素的单一谱分布相结合。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/summary4.png)

电磁辐射从像素穿过你的角膜，击中你的视网膜，刺激你的3种视锥细胞。

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/summary5.png)

为了不同的色彩而将其组合在一起，我们会留下打开此帖子的图像！

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/Hero.png)

## 浅谈亮度设置

![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/brightness.png)

在sRGB值转换为子像素亮度之前，它们将由设备的亮度设置衰减。因此，以50%亮度显示的`0xFF0000`可能与100%亮度的同一显示器上的`0x7F0000`匹配。

在理想的屏幕中，这意味着无论亮度设置如何，黑色像素![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/svg/37.svg)都不会发光。然而，大多数手机和笔记本电脑屏幕都是液晶屏幕，每个亚像素都是一个在白光下工作的滤镜。这段视频对LCD的工作原理有很大的帮助：

<!-- <iframe width="730" height="315" src="https://www.youtube.com/embed/jiejNAUwcQ8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> -->
![](https://yylifen.github.io/color-from-hexcodes-to-eyeballs/color/image/v.jpg)

[播放链接：https://youtu.be/jiejNAUwcQ8](https://youtu.be/jiejNAUwcQ8)

过滤器是不完美的，因此，随着亮度的增加，黑色像素将发出光时，背光通过。OLED屏幕(比如在iPhoneX和Pixel 2上)不使用背光，这使得它们的黑色与屏幕亮度无关。

## 补充

这篇文章有意忽略色彩复制和识别的许多方面。例如，我们没有讨论你的大脑如何处理[对手过程理论](https://psych.ucalgary.ca/PACE/VA-Lab/colourperceptionweb/theories.htm)中的视锥细胞激发信息，或者[色彩不变性](https://en.wikipedia.org/wiki/Color_constancy)的影响。我们没有讨论[加色]((https://en.wikipedia.org/wiki/Additive_color))和[减色](https://en.wikipedia.org/wiki/Subtractive_color)。我们没说[色盲](http://www.colour-blindness.com/general/how-it-works-science/)。我们没有讨论[光通量、发光强度、亮度、照度和发光率]((https://en.wikipedia.org/wiki/Photometry_(optics)#Photometric_quantities))之间的区别。我们没有谈论[ICC设备的色彩配置文件](https://en.wikipedia.org/wiki/ICC_profile)，也没有讨论像[f.lux](https://justgetflux.com/)这样的程序对色彩感知的作用。

我忽略它们因为这个帖子已经太久了!正如[我的一个朋友](https://twitter.com/amtinits)说的：即使你是一个人，知道大多数事情都比他们看起来更复杂，色彩比你想象的更有深度。

## 参考

我专门花了大部分时间写这篇文章，只是为了学习，因为我不断地发现我遗漏了一些我想要解释透彻的东西。

下面列出了一些更有帮助的建议：

*   [比色学入门指南](https://medium.com/hipster-color-science/a-beginners-guide-to-colorimetry-401f1830b65a)

*   [CIE 1931彩色空间](https://en.wikipedia.org/wiki/CIE_1931_color_space)

*   [HSL和HSV](https://en.wikipedia.org/wiki/HSL_and_HSV)

*   [伽马校正](https://en.wikipedia.org/wiki/Gamma_correction)

*   [实时渲染，第三版](https://www.amazon.com/Real-Time-Rendering-Third-Tomas-Akenine-Moller/dp/1568814240?ie=UTF8&amp;tag=stackoverfl08-20) p210-217

我还需要利用许多数据表来生成这篇文章中的图表：

*   [伦敦大学色彩与视觉研究实验室数据库](http://www.cvrl.org/) (XYZ配色函数，视锥的基本原理)

*   [fluxometer.com](https://fluxometer.com/rainbow/#!id=iPad%20Pro/6500K-iPad%20Pro) (RGB液晶屏亚像素光谱)

*   [CIE15：技术报告：比色法，第3版](https://archive.org/details/gov.law.cie.15.2004) (GB配色功能)

特别感谢[Chris Cooper](http://www.coopernetics.com/blog/)和[Ryan Kaplan](http://rykap.com/)就该职位草案提供反馈。

*如果你喜欢看这篇文章，你应该在[twitter上关注我(Jamie Wong)](https://twitter.com/jlfwong)，看看[我写的其他博客文章](http://jamie-wong.com/)，或者甚至[和我一起在Figma工作](https://www.figma.com/careers)！*


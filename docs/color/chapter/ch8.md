## Wright和Guild的配色实验

20世纪20年代末，威廉·大卫·赖特(William David Wright)和约翰·吉尔德(John Guild)进行了实验，用3个特定波长的光精确地定义色彩。

尽管他们可能还不知道眼睛里有三种色彩，但至少早在一百年前就有人提出了这样的观点，即所有可见的色彩都可以由三种色彩组合而成。

![](http://jamie-wong.com/images/color/tricolor.png)

*查尔斯·海特(Charles Hayter，1826)关于三色理论的一个例子*

Wright和Guild的想法是，建造一种仪器，让测试对象将三种固定波长光源组合在一起，重建测试色彩。设置应该如下所示：

![](http://jamie-wong.com/images/color/ColorMatching1.png)

实验者将底部的灯设置为目标波长(例如600nm)，然后要求被试调整三种灯的功率控制，直到它们看到的色彩匹配为止。

![](http://jamie-wong.com/images/color/ColorMatching2.png)

这三个刻度盘的功率设置给我们一个(红色，绿色，蓝色)三重识别与600nm相关的纯光谱色彩。每5nm对大约10名被试重复这一过程，一个图表显示了重建给定波长的外观所需的红色(700nm)、绿色(546nm)和蓝色(435nm)光的数量。这些函数被称为**色彩匹配函数(CMFs)**。

这些特殊的色彩匹配函数称为![](https://yylifen.github.io/sundries-trans/other/color/svg/21.svg)​、![](https://yylifen.github.io/sundries-trans/other/color/svg/23.svg)​和![](https://yylifen.github.io/sundries-trans/other/color/svg/13.svg)​。

![](http://jamie-wong.com/images/color/cmfs1.png)

这给出了与600nm每个![](https://yylifen.github.io/sundries-trans/other/color/svg/27.svg)​坐标(0.34，0.062，0.00)相关的纯光谱色彩。这是[CIE 1931年RGB色彩空间](https://en.wikipedia.org/wiki/CIE_1931_color_space#CIE_RGB_color_space)中的一个值。

等等，当函数变成负值是什么意思，就像这里？

![](http://jamie-wong.com/images/color/cmfs2.png)

与500nm相关的纯光谱色的![](https://yylifen.github.io/sundries-trans/other/color/svg/27.svg)坐标为(-0.72，0.85，0.48)。那么-0.72到底是什么意思？

事实证明，无论你把红色(700nm)刻度盘设置到什么位置，都不可能匹配500nm的输出光，不管蓝色和绿色刻度盘的值是多少。然而，你可以通过在底部加上红灯来使两面相匹配。

![](http://jamie-wong.com/images/color/ColorMatching3.png)

实际设置可能会有一套完整的3种可变功率，固定波长灯的任何一边的分频器，以允许他们中的任何一个调整为负值。

利用我们的配色功能，我们可以使用(可能是负的)红色(700nm)、绿色(546nm)和蓝色(435nm)光的组合来匹配任何单色光。

就像我们能够用L，M，S锥灵敏度函数来确定任何光谱分布的锥激励一样，我们也可以用我们的配色函数来做同样的事情。让我们把它应用到之前的柠檬色中：

![](http://jamie-wong.com/images/color/ColorMatchingLemon.png)

通过取光谱曲线乘积下的面积和配色函数，我们得到一个![](https://yylifen.github.io/sundries-trans/other/color/svg/27.svg)三重态(1.0，0.8，0.2)唯一识别这种色彩。

而![](https://yylifen.github.io/sundries-trans/other/color/svg/30.svg)色彩空间给了我们一种精确的色彩识别方法，而这个![](https://yylifen.github.io/sundries-trans/other/color/svg/27.svg)色彩空间为我们提供了一种精确的色彩再现方法。但是，正如我们在配色函数中所看到的，任何带有负![](https://yylifen.github.io/sundries-trans/other/color/svg/27.svg)坐标的色彩都不能被实际再现。

![](http://jamie-wong.com/images/color/cmfs3.png)

但这张图只显示哪些光谱色彩不能再现。非光谱色彩呢？我能用R，G，B组合出粉红色吗？那蓝绿色呢？

要回答这些问题，我们需要一种更好的可视化色彩空间的方法。


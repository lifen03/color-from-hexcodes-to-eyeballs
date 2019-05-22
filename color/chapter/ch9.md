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


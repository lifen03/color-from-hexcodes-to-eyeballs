## 摘要

![](http://jamie-wong.com/images/color/Hero.png)

这篇文章也有俄语版本：[Цвет：отшестнадцатеричныхкодовдоглаза](https://habr.com/post/353582/)，和日语版本：色：[ヘキサコードから眼球まで](https://postd.cc/color/)。

为什么我们能感觉到`background-color: #9B51E0`是特定的紫色？

![](http://jamie-wong.com/images/color/Purple.png)

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


{{ target: partial-post-effect }}

#${prefix|default('#')} postEffect(Object)

后处理特效的相关配置，后处理特效可以为画面添加高光，景深，环境光遮蔽（SSAO），调色等效果。可以让整个画面更富有质感。

下面分别是关闭和开启 `postEffect` 的区别。

<div class="twentytwenty-container" style="width: 700px;">
    <img src="documents/asset/gl/img/globe-posteffect-disable.png" width="100%" title="Disable">
    <img src="documents/asset/gl/img/globe-posteffect-enable.png" width="100%" title="Enable">
</div>

注意在开启 postEffect 的时候默认会开启 [temporalSuperSampling](${componentType}.temporalSuperSampling) 在画面静止后持续对画面增强，包括抗锯齿，景深，SSAO，阴影等。

##${prefix|default('#')} enable(boolean) = false

是否开启后处理特效，默认关闭。

##${prefix|default('#')} bloom(Object)

高光特效。高光特效用来表现很“亮”的颜色，因为传统的 RGB 只能表现`0 - 255`范围的颜色，所以对于超出这个范围特别“亮”的颜色，会通过这种高光溢出的特效去表现。如下图

![](~globe-posteffect-bloom.png)

###${prefix|default('#')} enable(boolean) = false

是否开启光晕特效。

###${prefix|default('#')} bloomIntensity(number) = 0.1

光晕的强度，默认为 0.1

##${prefix|default('#')} depthOfField(Object)

景深效果。景深效果是模拟摄像机的光学成像效果，在对焦的区域相对清晰，原理对焦的区域则会逐渐模糊。

景深效果可以让观察者几种注意力到对焦的区域，而且让画面的镜头感更强，大景深还能塑造出微距的模型效果。

下面分别是关闭和开启景深的区别。

<div class="twentytwenty-container" style="width: 700px;">
    <img src="documents/asset/gl/img/geo-no-dof.png" width="100%" title="Disable">
    <img src="documents/asset/gl/img/geo-dof.png" width="100%" title="Enable">
</div>

###${prefix|default('#')} enable(boolean) = false

是否开启景深

###${prefix|default('#')} focalDistance(boolean) = 50

初始的焦距，用户可以点击区域自动聚焦。

###${prefix|default('#')} focalRange(boolean) = 20

完全聚焦的区域范围，在此范围内的物体时完全清晰的，不会有模糊

###${prefix|default('#')} fstop(number) = 2.8

镜头的[F值](https://zh.wikipedia.org/wiki/%E7%84%A6%E6%AF%94)，值越小景深越浅。

###${prefix|default('#')} blurRadius(number) = 10

焦外的模糊半径

不同模糊半径的区别：

<div class="twentytwenty-container" style="width: 700px;">
    <img src="documents/asset/gl/img/geo-dof-small.png" width="100%" title="blurSize: 3">
    <img src="documents/asset/gl/img/geo-dof-large.png" width="100%" title="blurSize: 10">
</div>

##${prefix|default('#')} SSAO(Object)

屏幕空间的环境光遮蔽效果。环境光遮蔽可以让角落，缝隙等大部分光无法到达的区域变暗，是传统的阴影贴图的补充，可以让整个场景更加自然，有层次。

下面是无 SSAO 和有 SSAO 的对比。

<div class="twentytwenty-container" style="width: 700px;">
    <img src="documents/asset/gl/img/geo-no-ssao.png" width="100%" title="No SSAO">
    <img src="documents/asset/gl/img/geo-ssao.png" width="100%" title="SSAO">
</div>

###${prefix|default('#')} enable(boolean) = false

是否开启环境光遮蔽，默认不开启

###${prefix|default('#')} quality(string) = 'medium'

环境光遮蔽的质量，支持`'low'`, `'medium'`, `'high'`, `'ultra'`

###${prefix|default('#')} radius(number) = 1

环境光遮蔽的采样半径。半径越大效果越自然，但是需要设置较高的`'quality'`。

下面是半径值较小与较大之间的区别

<div class="twentytwenty-container" style="width: 700px;">
    <img src="documents/asset/gl/img/geo-ssao-small-radius.png" width="100%" title="Radius: 1">
    <img src="documents/asset/gl/img/geo-ssao-large-radius.png" width="100%" title="Radius: 10">
</div>

###${prefix|default('#')} intensity(number) = 1

环境光遮蔽的强度。值越大颜色越深。



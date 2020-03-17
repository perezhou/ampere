移动端适配方案（终极版）
法忍受rem适配布局带来的问题与书写的不便（虽然我可以写loader自动将px转成rem），所以早前写过NickFlex移动端适配方案，现在的方案与NickFlex方案核心原理是一样的，但这次解决掉了之前适配方案中的几个致命问题。 刚才在看书的时候回顾了关于移动适配的问题，于是灵光一闪似乎想到了解决方案， 于是就立马打开电脑写代码到现在，现在已经是02：18点了，验证完了方案又去测试了安卓4.2与ios8.1系统均兼容没有问题。好了赶紧发布吧。

之前适配方案出现的致命问题
由于之前的方案使用的transform:scale进行缩放，导致fixed定位失效。
由于整个页面进行缩放导致在事件中获取event.clientX等事件相关的坐标不准确（事件中的坐标信息是缩放之后的值，导致取值不正确需要将事件的坐标再*缩放比例）
先说说这个适配方案解决了什么问题
0成本享受移动端开发适配，与开发PC一样
不需要使用rem单位，按设计稿上的尺寸写就可以了
不会出现1像素的问题，没有rem也就不会有计算后小数的产生
画重点！使用这个之后设计稿上是20px你就写20px！跟开发pc是一样的！！！
画重点！使用这个之后设计稿上是20px你就写20px！跟开发pc是一样的！！！
画重点！使用这个之后设计稿上是20px你就写20px！跟开发pc是一样的！！！

安装
使用npm或cnpm安装

    // npm安装
    npm install  nick-mobile-adaptation
    // cnpm安装
    cnpm install nick-mobile-adaptation
    // yarn安装
    yarn nick-mobile-adaptation
如果不使用npm或cnpm传统的方式直接下载src/index.js 使用传统的script标签引入也可以

    <script src="NickMobileAdaptation.js"></script>
使用
npm安装的方式

    const NickMobileAdaptation = require('nick-mobile-adaptation');
如果是script引入的方式NickMobileAdaptation就已经是全局函数了不需要额外做什么

    // 一句话就可以了
    NickMobileAdaptation();
配置设计稿尺寸
默认设计稿尺寸是750，这个值是可以配置的
如果您的设计稿尺寸不是750的那么一定要配置自己的设计稿尺寸！！！否则比例就会出问题！！！
假如您的设计稿是640则可以按如下参数进行配置，当然也可以是任意数值
    NickMobileAdaptation({width:640})
大屏下也想显示手机尺寸
有的时候是不是想在PAD或者PC下以手机的宽度展示？
大屏下默认显示比例为0.6即60%，比如在ipad或pc下显示区域仅占60%且居中显示
假如您希望大屏下最大显示比例为50%则可以按如下配置
    NickMobileAdaptation({scale:0.5})
如果你即需要配置设计稿尺寸又需要设置最大显示宽度则可以如下

    NickMobileAdaptation({width:640,scale:0.5})
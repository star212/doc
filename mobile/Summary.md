##已覆盖可用的css3特性及特殊

* 没有hack（如：用_开头的属性可以区别ie6，在mobile上没有这些东西）
* -webkit-box 运用广泛
* -webkit-appearance: none; 用于清除各种默认的浏览器样式，主要用在表单元素的样式上面
* border-radius,box-sizing,box-shadow,-webkit-gradient,tranform 等支持良好，参见www.caniuse.com
* -webkit-tap-highlight-color: rgba(255,255,255,0); 用于清除默认的点击反馈样式
* -webkit-text-size-adjust: none; 禁止浏览器自动配置字体大小
* http://cubic-bezier.com 贝塞尔曲线

##html标签的覆盖情况

###meta标签
* [viewport](http://dev.w3.org/csswg/css-device-adapt/)
* `<meta content="yes" name="apple-mobile-web-app-capable" />`该属性添加以后，如果把图标添加到主屏幕，点击打开以后将全屏显示，而不显示浏览器地址栏等周边按钮
* `<meta name="apple-itunes-app" content="app-id=451400917" />` 在ios6以上会在浏览器顶部生成一个提示下载对应app的小banner。
* `<meta content="black-translucent" name="apple-mobile-web-app-status-bar-style" />` 这个属性在web添加到主屏幕以后，并开启了capable以后，才生效。content的值有default，blank，black-translucent。以black-translucent显示时，网页是真正的全屏，顶部的状态栏是透明的。以后blank和default显示时，网页显示在状态栏的下面。
* `<meta content="telephone=no" name="format-detection" />` 该属性值使得网页上的手机号码不自动显示为电话号码的超链接

###href属性

* 特殊的url协议：tel:18758052819
* http://developer.apple.com/library/safari/#featuredarticles/iPhoneURLScheme_Reference/Introduction/Introduction.html 
* http://stackoverflow.com/questions/433907/how-to-link-to-apps-on-the-app-store

##javascript上的特性

* querySelector，querySelectorAll

### touch事件
* touchstart、touchmove、touchend、touchecancel

##调试
* http://www.atatech.org/article/detail/8966/0?key=4f6c04845893a9f752f8ae5cdfbabf39&replay_id=8093
* android上的console开启方法是：在地址栏输入 about:debug 进入。	
 
##各种bug收集
* https://github.com/Araw/MobileWeb-Dev-Wiki

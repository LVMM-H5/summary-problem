# summary-problem
常见问题总结

## 目录

* [HTML相关](#html相关)
* [CSS相关](#css相关)
* [JS相关](#js相关)

### HTML相关
* `<meta name="format-detection" content="telephone=no" />` 防止IOS数字自动识别为电话号码；

### CSS相关
* 用border-image和border-width写1px线时，记得加上border-style:solid，不然小米手机不显示边框；
* webkit-touch-callout:none，H5页面想禁止长按链接或长按图片后弹出菜单，这个属性可以让你禁用系统默认菜单（iOS有效）;
* -webkit-user-select: none，H5页面想禁止用户在页面上选中文字、图片等，也就是，让页面内容不可选。这个属性可以让页面内容不被选中；
* -webkit-tap-highlight-color : rgba(255,0,0,0.5)，这个属性只用于iOS (iPhone和iPad)。当你点击一个链接或者通过Javascript定义的可点击元素的时候，它就会出现一个半透明的灰色背景。要重设这个表现，你可以设置webkit-tap-highlight-color为任何颜色，想要禁用这个高亮，设置颜色的透明值为0即可；
* 多余字符串显示点点，不设高，火狐不生效；
* input设置disabled属性时，IOS会使用input value disabled的默认样式#ccc，若要改变其颜色须设置样式属性如下：
    ``` css
    input:disabled{
        -webkit-text-fill-color: #333;
        -webkit-opacity: 1;
        color: #333;
    }
    ```
* 一行两列样BFC Block Formatting Context
    ``` html
    <span class="s1"></span>
    <span class="s2"></span>
    ```
    ``` css
    .s1{float:left;}
    .s2{display:block; overflow:hidden;}
    ```
实现两栏的自适应（类似于一行两列）。


### JS相关
* 无痕浏览模式下，localStorage、sessionStorage是禁用的，可使用cookie；
* 多开webview，http(s)协议 cookie和localStorage可共享，sessionStorage不可共享；
多开webview，file协议（本地化） localStorage可共享， cookie和sessionStorage不共享。
* ios app和微信的webview会对ajax请求做缓存，当同一个接口连续两次请求发的参数完全一致时webview有可能会把缓存的响应结果直接传给回调函数并执行（调整系统时间后必现），此种现象会导致本来应该获取不同结果的接口始终返回同一个结果——加时间戳；
* app的iPad兼容性问题：ua.indexOf("iPad; CPU OS")>-1，注意中间有个空格；
* console.log异步：chrome或safri等WebKit的console.log并没有立即拍摄对象快照，相反，它只存储了一个指向对象的引用，然后在代码返回事件队列时才去拍摄快照；**Node的console.log是另一回事，它是严格同步的，因此同样的代码输出的却为{}。**
    ```js
    var obj = {};
    console.log(obj);
    obj.aa = 'hello';
    ```


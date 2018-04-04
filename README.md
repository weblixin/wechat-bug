# wechat-bug
小程序开发过程中踩过的坑

1、height:auto;失效，必须指定image的高度为具体数值,不然高度为0。

2、真机和模拟器的问题总结：  
  
  <dl>
    <dd> ① input标签中设置为value属性，缩进样式text-indent在模拟器中失效，在真机中正常运行。placeholder则无此现象</dd>
    <dd> ② 测试过程中，域名为http格式的请求，在模拟器下可以正常运行，在真机中必须打开调试才能看到效果</dd>
    <dd> ③ 设置视频暂停，分享后继续播放时，会出现模拟器视频需再次分享才能继续播放，而真机可以继续播放</dd>
    <br />
    <dd> ④ 由于video组件调用的是客户端创建的原生组件，它的层级是最高的，模拟器中不会出现这个问题，而真机中会覆盖其他的内容</dd>
    <dd> ⑤ video组件的播放控件，当设置为false时，模拟器中还会显示，而真机中会隐藏</dd>
  </dl>
  
3、input组件设置text-indent，在没有获取焦点的时候是有效果的，但是在获取焦点时会失去缩进的效果，所以喜欢用text-indent的同学们就换换口味吧，用padding实现缩进吧  

4、input组件用rgba设置背景色透明透明度0.7，加padding会出现色差，改用opacity解决

5、下拉刷新不能和scroll-view组件共同使用，想要实现既可以下拉刷新又可以下滑加载，需要换成view组件，并且将onScrollLower函数改为onReachBottom

6、小程序上线，域名必须采用https和SSL证书，部分小程序的服务类目，域名必须在ICP备案，否则审核不通过

7、小程序相互之间可以跳转的前提是必须关联在同一个公众号下，设置跳转时，需要设置envVersion: 'release'，release为线上版本

8、跳转到带有tabBar的页面，必须使用switchTab，否则无法实现跳转

9、小程序中的图片要用绝对路径，否则无法显示

10、快速创建项目文件夹的方式：在app.json文件中直接配置路径即可

11、wxss编译错误：在控制台输入openVendor()，清除里面的wcsc/wcsc.exe 然后重启工具

12、如何获取 openId, sessionKey, unionId？
    
    在app.js 中 wx.login中 发送 res.code 到后台换取openId, sessionKey,unionId  
    
13、小程序中target和currentTarget有什么区别

    target指的是当前点击的组件 和currentTarget 指的是事件捕获的组件  
    
14、模板的定义和使用
    <ul>
        <li>使用 name 属性，作为模板的名字</li>
        <li>使用 is 属性，声明需要的使用的模板，然后将模板所需要的 data 传入</li>
    </ul>  
      
15、小程序的长度单位  
  
    小程序的长度单位为rpx，按照iphone6的来计算，1rpx=0.5px=1物理像素  
      
16、在页面中引入模板的wxss文件，采用@import引入，且需要以分好结尾，否则会出错  

17、bindTap是不会冒泡到父级，而catchTap会进行事件冒泡  

18、data-aaa 这样设置的值可以用event.target.dataset.aaa进行获取  

19、所有组件的所有属性均可以采用 插值表达式 + 三目运算符进行赋值  

20、除了采用三目运算符进行判断，也可用使用wx:if和wx:else配合实现  

21、获取app.js中的字段或数据，采用getApp()可以实现  

22、可以将一些公共的函数封装在一个js中，通过require的方式引入当前的js文件中  

23、编写复用的模板时，从最小的模板开始编写，由小到大，使用时，wxml和wxss必须引入到当前的页面  

24、wx.previewImage({  
    	urls: [src], //需要预览的http链接列表  
    	current: src //当前显示图片的http链接  
        })  
    
25、小程序不需要写保存图片的方法，默认长按可以保存图片

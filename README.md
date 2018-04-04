# wechat-bug
小程序开发过程中踩过的坑

1、height:auto;失效，必须指定image的高度为具体数值,不然高度为0。

2、真机和模拟器的问题总结：  
  
  > ① input标签中设置为value属性，缩进样式text-indent在模拟器中失效，在真机中正常运行。placeholder则无此现象  
  > ② 测试过程中，域名为http格式的请求，在模拟器下可以正常运行，在真机中必须打开调试才能看到效果  
  > ③ 设置视频暂停，分享后继续播放时，会出现模拟器视频需再次分享才能继续播放，而真机可以继续播放  
  > ④ 由于video组件调用的是客户端创建的原生组件，它的层级是最高的，模拟器中不会出现这个问题，而真机中会覆盖其他的内容  
  > ⑤ video组件的播放控件，当设置为false时，模拟器中还会显示，而真机中会隐藏  
  
3、input框设置text-indent，在没有获取焦点的时候是有效果的，但是在获取焦点时会失去缩进的效果，所以喜欢用text-indent的同学们就换换口味吧，用padding实现缩进吧  

4、

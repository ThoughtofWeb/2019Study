## [微信小程序](https://developers.weixin.qq.com/miniprogram/dev/framework)

    小程序的逻辑层和渲染层是分开的，逻辑层运行在 JSCore 中，
    并没有一个完整浏览器对象，因而缺少相关的DOM API和BOM API,例如 jQuery、 Zepto 等，
    在小程序中是无法运行的。同时 JSCore 的环境同 NodeJS 环境也是不尽相同，
    所以一些 NPM 的包在小程序中也是无法运行的。
    
### JSON配置

    1. app.json
        
        pages字段 —— 用于描述当前小程序所有页面路径，这是为了让微信客户端知道当前你的小程序页面定义在哪个目录。
        "pages":[
            "pages/index/index",
            "pages/logs/logs"
          ]
        window字段 —— 定义小程序所有页面的顶部背景颜色，文字颜色定义等。
        
    2. project.config.json
    
        个性化配置，其中会包括编辑器的颜色、代码上传时自动压缩等等一系列选项
        
    3. 页面配置 page.json
    
        每个页面都有不一样的色调来区分不同功能模块，让开发者可以独立定义每个页面的一些属性
        紧接着客户端就会装载这个页面的 WXML 结构和 WXSS 样式,会装载 JS
        Page({
          data: { // 参与页面渲染的数据
            logs: []
          },
          onLoad: function () {
            // 页面渲染后 执行
          }
        })
        Page 是一个页面构造器，这个构造器就生成了一个页面。
        在生成页面的时候，小程序框架会把 data 数据和 index.wxml 一起渲染出最终的结构
    
    4. sitemap 配置
        
        根目录下的 sitemap.json 文件用来配置小程序及其页面是否允许被微信索引
        {
          "desc": "关于本文件的更多信息，请参考文档 https://developers.weixin.qq.com/miniprogram/dev/framework/sitemap.html",
          "rules": [{
          "action": "allow", // 支持索引
          "page": "*"
          }]
        }   

### 框架
    
    小程序框架系统分为两部分：逻辑层（App Service）和 视图层（View）
    框架的核心是一个响应的数据绑定系统，可以让数据与视图非常简单地保持同步。
    当做数据修改的时候，只需要在逻辑层修改数据，视图层就会做相应的更新。
    
    1. 场景值用来描述用户进入小程序的路径
        onShow(res) {
                if (res.scene === 1038) { // 场景值1038：从被打开的小程序返回
                    const { appId, extraData } = res.referrerInfo
                    if (appId == 'wxbd687630cd02ce1d') { // appId为wxbd687630cd02ce1d：从签约小程序跳转回来
                        if (typeof extraData == 'undefined'){
                            // TODO
                            // 客户端小程序不确定签约结果，需要向商户侧后台请求确定签约结果
                            return;
                        }
                        if(extraData.return_code == 'SUCCESS'){
                            // TODO
                            // 客户端小程序签约成功，需要向商户侧后台请求确认签约结果
                            var contract_id = extraData.contract_id
                            return;
                        } else {
                            // TODO
                            // 签约失败
                            return;
                        }
                    }
                }
        }
    
    2. 逻辑层
    
        注册小程序 （整个小程序只有一个 App 实例，是全部页面共享的）
        通过 getApp 方法获取到全局唯一的 App 实例
        App({
          onLaunch (options) {
            // Do something initial when launch.
          },
          onShow (options) {
            // Do something when show.
          },
          onHide () {
            // Do something when hide.
          },
          onError (msg) {
            console.log(msg)
          },
          globalData: 'I am global data'
        })
         
       注册页面 
       Page()
       Component() 构造器构造页面
       Page 构造器适用于简单的页面。但对于复杂的页面， Page 构造器可能并不好用
       
       生命周期
       onLoad: function(options) {
         // 页面创建时执行
       },
       onShow: function() {
         // 页面出现在前台时执行
       },
       onReady: function() {
         // 页面首次渲染完毕时执行
       },
       onHide: function() {
         // 页面从前台变为后台时执行
       },
       onUnload: function() {
         // 页面销毁时执行
       },
       
       路由 https://developers.weixin.qq.com/miniprogram/dev/framework/app-service/route.html
       
       模块化
       
       模块只有通过 module.exports 或者 exports 才能对外暴露接口
       在模块里边随意更改 exports 的指向会造成未知的错误，推荐用 module.exports 来暴露模块接口
       
    3. 视图层
    
       WXML
       <view> {{message}} </view>
       <view wx:for="{{array}}"> {{item}} </view>
       <view wx:if="{{view == 'WEBVIEW'}}"> WEBVIEW </view>
       
       WXSS
       尺寸单位
       750rpx = 375px = 750物理像素，1rpx = 0.5px = 1物理像素
       样式导入
       @import
       
       WXS
       <wxs module="m1">
       var msg = "hello world";
       module.exports.message = msg;
       </wxs>
       
       事件绑定
       bind 不会阻止事件向上冒泡
       catch 会阻止事件向上冒泡
       
       现有组件 https://developers.weixin.qq.com/miniprogram/dev/component/
       
       动画
       创建 this.animate(selector, keyframes, duration, callback)
       清除 this.clearAnimation(selector, options, callback)
       
### WXML
        小程序的 WXML 用的标签是 view, button, text 等等
        <view class="container">
          <view class="userinfo">
            <button wx:if="{{!hasUserInfo && canIUse}}"> 获取头像昵称 </button>
            <block wx:else>
              <image src="{{userInfo.avatarUrl}}" background-size="cover"></image>
              <text class="userinfo-nickname">{{userInfo.nickName}}</text>
            </block>
          </view>
          <view class="usermotto">
            <text class="user-motto">{{motto}}</text>
          </view>
        </view>

### WXSS

    1. 新的尺寸单位 rpx
    2. 提供了全局的样式和局部样式
    
### 组件

    1. 地图 <map></map>
    
### Api

    1. 获取用户的地理位置 wx.getLocation
    2. 微信扫一扫 wx.scanCode
    3. 事件监听 wx.onCompassChange
    4. 异步 wx.request，wx.login 
    5. 获取节点信息 wx.createSelectorQuery()
    
    
    
    
    
    
    
    
    
    
    
    
    

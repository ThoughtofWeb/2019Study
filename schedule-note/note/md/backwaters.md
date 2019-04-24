## Backwaters背水一战

1. 自我介绍

        我先自我介绍一下吧，我叫曹相相，有两年多的工作经验，
        上一家公司是在鲁班软件做前端开发这块的工作，
        主要的工作内容是还原ui设计稿，配合后端程序调用接口，展示数据。
        前端这块用的技术框架有vue和angular，我平时喜欢研究技术网站，
        有时候会针对某些业务看其中的原理，再看看有没有更好的方式实现，
        通过平时的项目经验以及对技术的研究，自己的技术也受益了很多。

2. 离职原因

        公司用的技术站太旧了，我想要换个环境拓宽自己的知识体系

3. 我们公司的技术站也老旧，你怎么看？

        至少我处于一个沉淀自己的阶段，不会频繁跳槽的

4. 你做过哪些项目？

        电销客户管理系统是电销人员为客户订制个人套餐的系统
        Luban Inspector 系统是服务九寨沟至绵阳高速公路的质检和计量系统
        Luban Cooperation 系统是公司内部人员协作及人事变动的系统
        Luban Center 系统是针对不同项目、分公司及人员处理权限及工作流问题
        Luban Tong 系统是统计及节省各种材料采购成本的系统

5. 平时看的技术网站？

        一般是根据技术论坛上最新的推文去关注一些博客和github上有意思的文章网站
        最近在看的是树组件的实现原理。。。

6. 为什么用这样的框架？

        质检这个系统当时的项目框架比较大，基于公司当时的技术背景，保守选择了angular1.x+

        Luban Center这个系统当时内部技术人员还组织了一个会议沟通过，针对当时的技术背景下，
        vue框架还是比较成熟的，而且简单上手，后期迭代组件化维护成本低，最终选择了vue

7. 项目中担当的角色是什么？

        质检项目上主线都是我在架构和维护的，中间小版本变动不大的情况下交给其他同事，
        遇到问题我们俩协商怎么做比较合适，其他时间我就会去负责其他项目大方向的迭代和开发

8. 通过项目学到了什么？

        如何抽象化组件？

            首先组件化思想的核心在于增加不同的组件组合去展示，
            而不是往一个组件中去塞不同的内容，从而达到业务解耦

            CSS方面抽象化一般考虑到布局到页面再到具体的功能，
            比如一般将flex布局单独抽出来放到layout.scss文件中处理，
            再根据页面上相似且多处使用到的功能如按钮、列表以及统一处理的面板都放到element.scss中，
            最后在单独的业务模块中引入element.scss，再做样式处理

            JS方面抽象化与CSS类似，由整体到局部，尽量抽象到每一个业务组件都能用

        如何设计模块化？

            首先将公共的模块抽出来放到public目录下，如header/navbar等，
            其次根据具体的功能将复用性高的抽成组件提取到core模块下，如btn/日历/分页等，
            最后针对单一的业务开发模块，每个业务储备一个单独的文件引入所有的功能组件

        如何独立构建项目？
            webpack 构建和配置项
            babel 编译各种loader加载器
            webpack-dev-server 热更新、渲染服务

        如何上线？
            1) js压缩 npm i --save uglifyjs-webpack-plugin
               webpack.config.js 引入&初始化
            2) css压缩 minimize
            3) npm run build

9. 项目有什么特色？解决过什么难题？(面试官不问，自己也要找机会说出来！！！)

       就和面试官聊聊 CSS组件化设计 模块化设计

       自适配问题面试官不问，暂时不说
       回答技巧 自适配一般大家处理的方法是media + viewport联合使用
       产生的问题是 1. media样式层叠覆盖
                  2. 设备太多，覆盖的面很窄，不具备通用性
       技术方案 动态计算font-size
               原理是利用viewport和设备像素比调整基准像素
                     利用px2rem自动转换css单位
                     px2rem 将设计稿所有的px转成rem,再根据rem动态计算font-size

10. 这么多项目哪个是你最满意的项目？

        电销客户管理系统

11. 项目的改进空间？

        可以聊聊gzip压缩
        由于需求开发时间有限加上这个项目体积比较小，我们没有尝试gzip压缩，
        从性能的角度上考虑，使用gzip压缩css和js还是很有必要的

        参考网站：https://segmentfault.com/a/1190000012571492

12. 如果让你重新设计这个项目，你会怎么思考？

        像质检系统，我觉得这个项目的技术成长空间还是很大的，
        首先这种业务需求复杂而又要求快速迭代开发的框架我会选择vue,
        其次项目目录结构的设计要划分资源文件、css、js以及公共的入口文件，
        最后组件化的设计要拆分公共组件、可复用的功能组件以及单独的业务组件，
        抽象化，尽量做到业务解耦，这样做不仅能够提高开发效率，对于后期的迭代和维护也是很有益的。
13. 介绍一下你近期做的项目？

        请问我需要介绍一下这个项目的背景吗？
        可以。。
        电销客户管理系统是一款电销人员营销个人套餐产品的系统，
        这个项目是19年年初做的，人员配比是一个前端一个后台，
        由于电销人员是通过excel查找和管理客户数据很费时间，
        这个系统提升了他们的工作效率，使用组件化开发大大的节省了开发资源。
        组件化的设计是拆分公共组件、可复用的功能组件以及单独的业务组件，
        抽象化，尽量做到业务解耦，这样做不仅能够提高开发效率，对于后期的迭代和维护也是很有益的，
        通过这个项目我业务的理解更加深入，对组件化的处理更有把握，后面新开的项目都尝试了这种方式进行开发，
        不足之处就是由于开发时间的限制，加上这个项目体积比较小，后来没有尝试gzip压缩

14. 提到vue,必问的双向绑定的原理？

        利用es5的observer观察者模式，获取视图的变化，通知Model改变；
        监听数据的改变，作用到视图===>双向数据绑定

15. 开启CSS Module后如何使用第三方样式库？

        :class="$style.btn"
        <style lang="scss" module></style>

16. vue安装有几个版本，遇到问题如何解决的？

        安装的时候根据命令行的错误提示尝试自己解决一下，
        没效果再去网站上搜索相关资料收藏一下

17. 有没有使用CSS Module，它的原理是什么？

        先整体再部分最后颗粒化（布局、页面、功能、业务）
        上面的组件化再说一遍

18. 如何进行前后端分离？

        前后端分离开发在之前公司内部有两种解决方案，
            一种是前端请求跨域浏览器，访问服务器；
            另一种是使用node中间件做代理，使用node在本地开启服务的时候，
            客户端直接和node中间件接收和传送数据，不需要直接和服务器交互

19. 为什么使用webpack打包？

        Grunt和Gulp只能将一些CSS和JS文件分别压缩合并成单个文件，
        当然也具有一些编译功能，比如Less和Sass的编译、ES6到ES5的编译等等。
        但是Webpack不仅具有它们所具备的这些编译压缩合并功能，同时还具备模块化开发
        和组件式开发等优点，在目前流行的前端框架React和Vue中也得到很好的支持。

20. webpack loader的原理？

        Webpack本身只能处理 js模块，如果要处理其他类型的文件，就需要使用 loader 进行转换。
        Loader 可以理解为是模块和资源的转换器，它本身是一个函数，接受源文件作为参数，返回转换的结果

21. 如何使用webpack的？

22. 前端路由的原理？

        History Api  优雅，但对浏览器有要求    onpopstate    onpushstate
        Hash         不优雅，但没有兼容性问题  onhashchange  location.href

23. 自适应方案怎么做？原理是什么？

24. rem和em的区别？

25. HTML5新规范？

        语义化标签
        音频视频
        localStorage & sessionStorage
        postMessage
        web worker
        WebSocket
        Geolocation（地理定位）用于定位用户的位置
        拖拽

26. web request动画帧

        浏览器会遍历动画帧请求回调函数列表
        css3不能实现scrollTop，但是requestAnimationFrame可以
        css3对贝塞尔曲线轨迹有限制，但是requestAnimationFrame没有
        与setTimeout用法类似，但是requestAnimationFrame调用一次只会重绘一次动画，资源高效利用

27. 布局

        假设高度已知，实现三栏布局，其中左右两栏各300px,中间自适应？
        高度未知？
        上下左右垂直居中？

28. 对CSS盒模型的理解？

29. CSS如何设置两种模型？

30. JS如何获取对应盒模型的宽高?

31. BFC原理&解决方案&应用场景？

32. DOM事件模型

33. DOM事件流、描述DOM事件捕获的具体流程

34. Event对象的常见应用

35. 自定义事件

36. 继承的方式

        构造函数实现继承
        原型链实现继承
        组合继承
        寄生组合继承

37. 创建对象的几种方式

38. 原型、构造函数、对象实例、原型链？

39. 手写Object.create()

40. 手写new运算符

41. 函数柯里化

42. 同源策略&同源策略下限制条件

43. 前后端通信方式？

44. http协议的主要特点

45. http协议的方法

46. get和post的区别

47. 状态码

        1xx: 接受，继续处理
        200: 成功，并返回数据
        201: 已创建
        202: 服务器已接受请求,但尚未处理
        203: 成为，但未授权
        204: 成功，无内容
        205: 成功，重置内容
        206: 成功，部分内容
        301: 永久移动，重定向
        302: 临时移动，可使用原有URI
        304: 资源未修改，可使用缓存
        305: 需代理访问
        400: 请求语法错误
        401: 要求身份认证
        403: 拒绝请求
        404: 资源不存在
        500: 服务器错误

48. 管线化的特点&原理

49. 跨域请求的几种方式？

        jsonp原理
        hash
        Web Socket
        CORS
        postMessage

50. CSRF、XSS

51. 什么是DOCTYPE及作用

52. 去除浮动三种方式

53. 层叠上下文

54. CSS预处理器功能及作用

55. link 与 @import 的区别

56. CSS 动画

57. 执行上下文的过程

58. instanceof原理

        while(x.__proto__!==null) {
            if(x.__proto__===y.prototype) {
                return true;
            }
            x.__proto__ = x.__proto__.proto__;
        }
        if(x.__proto__==null) {return false;}

59. 闭包

60. script引入方式

61. 对象拷贝的方式 深拷贝、浅拷贝

62. 防抖与节流

63. 改变this指向

64. instanceof 、typeof和isArray之间的区别

65. this指向

66. 模块化分类、require和import区别

67. babel编译原理

            babylon 将 ES6/ES7 代码解析成 AST
            babel-traverse 对 AST 进行遍历转译，得到新的 AST
            新 AST 通过 babel-generator 转换成 ES5

68. AST是什么？

69. 不同标签页间的通讯

70. JS单线程

71. Event Loop 事件循环

72. 宏任务和微任务

73. 任务队列

74. 重绘和回流(重排)？

75. 触发回流的因素

        页面初次渲染
        浏览器窗口大小改变
        元素尺寸、位置、内容发生改变
        元素字体大小变化
        添加或者删除可见的 dom 元素
        激活 CSS 伪类（例如：:hover）

76. 触发重绘的因素

        visibility：hidden
        字体颜色、背景色改变

76. 减少回流的方法?

77. 从输入url到渲染的过程

        1.浏览器的地址栏输入URL并按下回车。
        2.浏览器查找当前URL是否存在缓存，并比较缓存是否过期。
        3.DNS解析URL对应的IP。
        4.根据IP建立TCP连接（三次握手）。
        5.HTTP发起请求。
        6.服务器处理请求，浏览器接收HTTP响应。
        7.浏览器解析渲染页面。
        8.关闭TCP连接（四次挥手）。

78. 浏览器如何渲染页面？

        HTML parser --> DOM Tree 生成DOM树
        CSS parser --> Style Tree解析 css 代码，生成样式树
        结合 dom树 与 style树，生成Render Tree渲染树
        通过layout确定元素的位置、宽高等
        展示页面

80. 什么会造成内存泄露？

81. 强缓存和协商缓存？(浏览器缓存的原理)

        浏览器在第一次请求发生后，再次请求时：

        访问本地缓存直接验证看是否过期，如果没过期直接使用本地缓存，使用强缓存，并返回 200，
        强缓存是利用http的返回头中的Expires或者Cache-Control两个字段来控制的，用来表示资源的缓存时间，
        Cache-Control的 max-age 优先级高于 Expires;

        当缓存已经过期时，使用协商缓存，请求服务器判断资源是否被修改，如果没有才继续使用本地缓存，
        此时返回的是 304,协商缓存主要包括 last-modified 和 etag,Etag 的优先级高于 Last-Modified

82. http2.0优化了什么？

83. http1.1优化了什么？

84. V8垃圾回收机制（一定要看下）

85. TCP三次握手(画个图即可)

        在第一次通信过程中，A向B发送信息之后，B收到信息后可以确认自己的收信能力和A的发信能力没有问题。
        在第二次通信中，B向A发送信息之后，A可以确认自己的发信能力和B的收信能力没有问题，但是B不知道自己的发信能力到底如何，所以就需要第三次通信。
        在第三次通信中，A向B发送信息之后，B就可以确认自己的发信能力没有问题。

86. TCP四次挥手
        与上面类似(画个图即可)

87. Web Worker原理

88. 存储方式

        cookie
        localStorage
        sessionStorage
        IndexDB

89. 提升页面性能的方式？

        1. 使用浏览器缓存
        2. 资源压缩
        3. 非核心代码异步加载
        4. 使用CDN
        5. DNS预解析

90. 异步加载的方式

91. defer和async区别

92. 前端错误的分类 以及 错误的捕捉方式

        即时运行错误：代码错误
            try...catch
            window.onerror()捕获
        资源加载错误（文件加载失败）
            object.onerror
            performance.getEntries() 获取所有文件的加载(根据获取所有的页面元素减去该方法捕获到的)
            Error事件捕获
                window.addEventListener('error', function (e) {
                    console.log('捕获', e);
                }, false);

93. 上报错误的基本原理

        采用Ajax通信上报
        采用Image对象上报

94. [跨域访问报错怎么捕获到？](https://www.jianshu.com/p/a45c9d089c93)

        给<script>标签添加 crossorigin 属性，
        并在服务器端设置 Access-Control-Allow-Origin 响应头，允许脚本被跨域访问
        window.onerror = ...

95. 近几年的职业规划？

        1. 我平时很崇拜那些技术大牛，我也要经过几年的努力，不断吸收，成为技术大牛
        2. 近阶段，如果公司给我安排某个岗位，我要先清楚这个岗位做什么，难点是什么，突破点在哪里，在一年内做到极致
        3. 针对公司一些成熟的组件，可以开源作品或者放到技术博客上去
        4. 我希望公司给我一些技术分享的机会，让自己不断成长

96. 手写bind/call/apply?

97. 这边是一个vue重构到react的项目，最近招人来做这块的内容，包括webpack之类的都是重新搭，你觉得你能hold住吗？

98. 打算在上海定居吗？是打算啥时候回二线？

99. 为什么不推荐用style内联元素？内联元素有什么缺点？

        css文件可以缓存

100. 你对团队的要求是怎么样的?

            人员配比
            解决问题
            开发效率

101. Fetch 相对于传统的 Ajax 有哪些改进？

102. 异步函数中使用this无法指向vue实例对象

         用箭头函数或者指定变量赋值为this

103. 定时器在组件销毁后还在执行

         在销毁组件的生命周期中销毁定时器或者一些动画的js
         beforeDestroy(){
              //我通常是把setInterval()定时器赋值给this实例，然后就可以像下面这么停止。
             clearInterval(this.intervalId);
         }

104. 动态添加的dom没有样式

         1 当添加的部分样式不会太多，而且是动态加载的，可以将其设置为非scoped的
         2 将添加dom部分用的样式放到非scoped样式标签中
         3 将添加的部分，如果有必要，可以另外写一个页面拆分的vue组件
         4 如果你想整个项目覆盖，就可以在src/styles下定义common.scss 这样的来重写覆盖样式

105. vue中直接修改数据，页面视图不更新

         1 this.$set(你要改变的数组/对象，你要改变的位置/key，你要改成什么value)
             this.$set(this.arr, 0, "OBKoro1"); // 改变数组
             this.$set(this.obj, "c", "OBKoro1"); // 改变对象

         2 数组原生方法触发视图更新: splice()、 push()、pop()、shift()、unshift()、sort()、reverse()

106. vue中的data必须为函数?

         为了避免多个组件使用同一数据互相影响，所以讲data约定为了返回函数类型，返回需要的对象，
         以此保证子组件在数据渲染的时候不会互相影响

107. ES6 import 引用问题

         ES6中，导入与导出指向的是内存地址，如果修改了对象中的属性，导出值会受导入值影响，影响到其他模块的使用。

         对象不复杂时，可以使用 JSON.parse(JSON.stringify(str)) 来生成一个全新的深度拷贝的数据对象。
         不过当组件较多、数据对象复用程度较高时，很明显会产生性能问题，这时我们可以考虑使用 Immutable.js

108. 路由参数变化组件不更新（使用路由出现问题如何解决）

          原因：获取参数写在了created路由钩子函数中，路由参数变化的时候，生命周期不会重新执行。
          解决方案1：watch监听router
                 2：用activated钩子代替原来在created、mounted钩子中获取数据
                 3：给router-view添加一个不同的key，只要url变化了，就一定会重新创建这个组件。

109. 怎么快速定位哪个组件出现性能问题

110. 实现 Promise.finally

         finally 方法用于指定不管 Promise 对象最后状态如何，都会执行的操作
         finally 特点：
                 不接收任何参数。
                 finally 本质上是 then 方法的特例

         Promise.prototype.finally = function (callback) {
           let P = this.constructor
           return this.then(
             value  => P.resolve(callback()).then(() => value),
             reason => P.resolve(callback()).then(() => { throw reason })
           )
         }

111. 实现 Vue SSR

112. grid 布局

113. babel-plugin-transform-runtime可以兼容并转化大部分的es6语法，但是部分语法不能转化

               推荐使用完整的 babel-polyfill

114. 动态懒加载组件

                1 webpack的路径使用变量拼接，必须预先给出一个相对路径，然后把具体的组件路径在传入
                2 用一个箭头函数，将需要传入的组件名或者相对路径传入
                3 用process.env.NODE_ENV确定使用哪种加载方式

                import vOther from '@/components/other'
                //修改后
                const vOther = () => import('@/components/other')

115. 当改变对象的非第一层属性或者值时，虽然值改变了，但是并未触发其watch方法监听

                使用deep，并且改变数值的方式要使用this.$set(this.obj,key,value)
                watch:{
                 person:{
                      deep:true,
                      immediate:true
                    }
                 },
                 created(){
                    setTimeout(()=>{
                      // this.$set(this.person,'tip',45);
                    },2000)
                  }
                }

116. 使用eventBus跨页面传参错误

                问题 ：第一次触发并没有执行接收
                      后续的触发都会积累之前的

                解决： this.$nextTick(function(){
                        //codes here
                      })

117. 在进行项目优化的时候，我们需要针对性的分析出哪些文件大，以及如何优化

                vue-cli初始化的项目，会默认安装webpack-bundle-analyzer插件

118. $nextTick

119. 生命周期

120. 数据响应(数据劫持)

121. virtual dom 原理实现

            更新dom结点是非常昂贵的，用js对象来代替dom结点，更新高效且便宜

122. Proxy 相比于 defineProperty 的优势

123. vue-router

124. vuex

125. 组件间通信

126. Vue computed 实现

127. Vue complier 实现

128. 组件间通信

129. [window的onload事件和domcontentloaded谁先谁后？](https://www.jianshu.com/p/d5cedce95acc)

                1 onload事件是DOM事件，onDOMContentLoaded是HTML5事件。
                2 onload事件会被样式表、图像和子框架阻塞，而onDOMContentLoaded不会。
                3 当加载的脚本内容并不包含立即执行DOM操作时，onDOMContentLoaded比onload事件执行时间更早。

130. 说一下箭头函数This指向问题

131. 说一下你对generator的了解？

132. 说一下你对promise的了解？

133. for...in和for...of和Object.keys有什么区别？

134. 使用过flex布局吗？flex-grow和flex-shrink属性有什么用？

135. 箭头函数和普通函数有什么区别？

136. 怎么优化页面的加载速度？

            HTML优化：
                使用语义化标签
                减少iframe：iframe是SEO的大忌，iframe有好处也有弊端
                避免重定向
            CSS优化：
                布局代码写前面
                删除空样式
                不滥用浮动，字体，需要加载的网络字体根据网站需求再添加
                选择器性能优化
                避免使用表达式，避免用id写样式
            js优化：
                压缩
                减少重复代码
            图片优化：
                使用WebP
                图片合并，CSS sprite技术

            减少DOM操作
            利用缓存
            使用CDN加速
            使用DNS预解析

137. promise和async/await和setTimeout区别

138. promise如何实现then介绍

139. 介绍es6的功能

140. state和props区别

141. 介绍defineProperty,什么时候用到？

142. 原生dom事件为什么不移除会造成内存泄漏？

143. 定时器为什么是不精确的？

144. setInterval有什么注意的？

145. 单例、工厂、观察者模式项目中的实际场景？

146. 项目中树组件的使用场景及了解？

147. 为什么虚拟dom比真实dom性能好？

148. html语义化的理解？

149. 介绍单页应用和多页应用？

                单页应用优点：  前后端分离
                              减轻服务器压力
                              增强用户体验
                       缺点：  prerender预渲染优化SEO

150. 介绍localStorage的API？

                getItem
                setItem
                removeItem
                clear

151. b和strong区别

            ```
                <b>是html的标签，而<strong>是web标准中xhtml的标签
                <b>标签是一个实体标签，<strong>标签是一个逻辑标签，它的作用是加强字符的语气
            ```

152. 介绍事件委托

153. 如何处理异常捕获

154. 类数组和数组的区别？如何将类数组转为数组

155. 平时怎么做继承？

156. 深拷贝怎么实现的？

157. let作用域怎么实现的？

158. 发布订阅者模式和观察者模式区别？

159. async、await怎么实现的

160. promise构造函数是同步还是异步，then呢？

161. 词法作用域和this的区别？

162. setState为什么默认是异步的？什么时候是同步的？

163. promise的三种状态

164. promise.all的实现原理

165. 遇到的复杂的业务场景举例

166. 介绍Immuable.js

167. webpack和gulp的区别

168. 如何实现异步加载

169. 网站seo处理

170. call和apply区别

171. async里有多个await请求，怎么优化

172. 介绍Fiber

173. 前端怎么做单元测试？

174. 如何解决props层级过深的问题？

175. webpack生命周期

176. 常用的plugins

177. 比较两个对象是否相等

178. 快速排序、选择排序、冒泡排序

179. 表单跨域

180. position:sticky

181. 事件代理及优缺点

182. promise如何进行异常捕获

183. 有时间看下http1.1和http2.0

184. webpack的plugins怎么实现











## Backwaters背水一战

1. 自我介绍

        我先自我介绍一下吧，我叫曹相相，有三年多的工作经验，
        之前是在鲁班软件做前端开发这块的工作，
        主要的工作内容是还原ui设计稿，配合后端程序调用接口，展示数据。
        前端这块用的技术框架有react、vue和angularjs，我平时喜欢研究技术网站，
        有时候会针对某些业务看其中的原理，通过平时的项目经验以及对技术的研究，自己的技术也受益了很多。

2. 离职原因

        在鲁班达到了一个瓶颈，现在的工作没什么挑战性，希望有一个更好的平台

3. 我们公司也没挑战性了，你怎么看？

        至少我处于一个沉淀自己的阶段，不会频繁跳槽的

4. 你做过哪些项目？

        梁场信息化管理系统是对预制梁的施工质量、施工进度、材料质量等进行信息化管理
        电销客户管理系统是电销人员为客户订制个人套餐的系统
        Luban Inspector 系统是服务九寨沟至绵阳高速公路的质检和计量系统
        Luban Cooperation 系统是公司内部人员协作及人事变动的系统
        Luban Center 系统是针对不同项目、分公司及人员处理权限及工作流问题
        Luban Tong 系统是统计及节省各种材料采购成本的系统

5. 平时看的技术网站？

        一般是根据技术论坛上最新的推文去关注一些博客和github上有意思的文章网站

6. 为什么用这样的框架？

        梁场这个系统当时内部技术人员还组织了一个会议沟通过，针对当时的技术背景下，
        react框架还是比较成熟的，而且简单上手，加上平时公司的技术分享会也学习过，后期迭代组件化维护成本低，最终选择了react

7. 项目中担当的角色是什么？

        梁场项目上主线都是我在架构和维护的，中间小版本变动不大的情况下交给其他同事，
        遇到问题我们俩协商怎么做比较合适，其他时间我就会去负责其他项目大方向的迭代和开发

8. 通过项目学到了什么？

        如何抽象化组件？

            首先组件化思想的核心在于增加不同的组件组合去展示，
            而不是往一个组件中去塞不同的内容，从而达到业务解耦

            CSS方面抽象化一般考虑到布局到页面再到具体的功能，
            比如一般将flex布局单独抽出来放到layout.js文件中处理，
            再根据页面上相似且多处使用到的功能如按钮、列表以及统一处理的面板都放到element.js中，
            最后在单独的业务模块中引入element.js，再做样式处理

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

        梁场信息管理系统

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

        首先要对数据进行劫持监听，所以我们需要设置一个监听器Observer，用来监听所有属性。
        如果属性发上变化了，就需要告诉订阅者Watcher看是否需要更新。因为订阅者是有很多个，
        所以需要一个消息订阅器Dep来专门收集这些订阅者，在监听器Observer和订阅者Watcher之间进行统一管理的。


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

        webpack能够将各个模块进行按需加载,实现了模块化开发和文件处理。
        npm init
        npm i --save webpack
        ...

        解析webpack配置参数，合并从shell传入和webpack.config.js文件里配置的参数，生产最后的配置结果。
        注册所有配置的插件，好让插件监听webpack构建生命周期的事件节点，以做出对应的反应。
        从配置的entry入口文件开始解析文件构建AST语法树，找出每个文件所依赖的文件，递归下去。
        在解析文件递归的过程中根据局文件类型和loader配置找出合适的loader用来对文件进行转换。
        递归完后得到每个文件的最终结果，根据entry配置生成代码块chunk。
        输出所有chunk到文件系统。

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

        与setTimeout相比，requestAnimationFrame最大的优势是由系统来决定回调函数的执行时机，
        系统每次刷新之前会主动调用requestAnimationFrame中的回调函数,它能保证回调函数在屏幕每一次的刷新间隔中只被执行一次，
        这样就不会引起丢帧现象，也不会导致动画出现卡顿的问题。
        兼容性问题

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
            动态创建script标签，绑定src属性，向服务端传入一个callback函数，服务端将返回结果以函数参数的形式返回。
        hash
        Web Socket(服务端可以主动向客户端推送数据)
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

         postMessage

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

96. 怎么快速定位哪个组件出现性能问题

97. 这边是一个vue重构到react的项目，最近招人来做这块的内容，包括webpack之类的都是重新搭，你觉得你能hold住吗？

98. 打算在上海定居吗？是打算啥时候回二线？

        暂时没有回去的打算

99. 为什么不推荐用style内联元素？内联元素有什么缺点？

        css文件可以缓存

100. 你对团队的要求是怎么样的?

         人员配比
         解决问题
         开发效率

101. Fetch 相对于传统的 Ajax 有哪些改进？

         语法简洁，更加语义化
         基于标准 Promise 实现，支持 async/await
         同构方便，使用 isomorphic-fetch

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

105. vue中直接修改数组，页面视图不更新

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
         不过当组件较多、数据对象复用程度较高时，很明显会产生性能问题，这时我们可以考虑使用 Immutable.js(
         持久化数据结构,使用旧数据创建新数据时，要保证旧数据同时可用且不变)

108. 路由参数变化组件不更新（使用路由出现问题如何解决）

          原因：获取参数写在了created路由钩子函数中，路由参数变化的时候，生命周期不会重新执行。
          解决方案1：watch监听router
                 2：用activated钩子代替原来在created、mounted钩子中获取数据
                 3：给router-view添加一个不同的key，只要url变化了，就一定会重新创建这个组件。

109. position:sticky

           当元素在屏幕内，表现为relative，就要滚出显示器屏幕的时候，表现为fixed

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

111. 事件代理及优缺点

         优点：1.可以大量节省内存占用，减少事件注册。比如ul上代理所有li的click事件就很不错。
              2.新增子对象时，无需再对其进行事件绑定
         缺点：如果把所有事件都用事件代理，可能会出现事件误判。即本不该被触发的事件被绑定上了事件。

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

          可以看做是一个微任务，在数据更新后调用，做异步处理

119. vue生命周期

          beforeCreate（创建实例，对象未绑定属性）
          created（对象绑定属性）
          beforeMount（Dom挂载前）
          mounted（DOM放置在页面内）
          beforeUpdate（更改已完成，但尚未准备好更新DOM）
          updated（更新DOM）
          beforeDestroy（组件销毁前）
          destroyed（组件销毁）

120. 数据响应(数据劫持)

         当我们访问或设置对象的属性的时候，触发Object.defineProperty来劫持对象属性的setter和getter

121. virtual dom 原理实现

         更新dom结点是非常昂贵的，用js对象来代替dom结点，更新高效且便宜

122. Proxy 相比于 defineProperty 的优势

         Proxy可以直接监听对象而非属性,可以劫持整个对象,并返回一个新对象,而Object.defineProperty只能遍历对象属性直接修改。
              可以直接监听数组的变化
         Proxy的劣势就是兼容性问题,而且无法用polyfill磨平

123. vue-router

         两种模式history和hash, 可以归为单页应用的核心

         query和params区别？

124. vuex

         1. Vuex 是为Vue提供的一种状态管理机制。
         2、Actions 执行异步操作如调用后台api 然后dispatch actions 方法 再commit mutations 再对state 进行修改
         3、Mutataions 执行的是同步的操作。可以直接使用改变state
         4、state 作为状态，改变后会直接作用到View上

125. 组件间通信

         父  :name="projectName"
         子   props接收

         子  $emit('事件'，属性)
         父  @事件 接收
             父级若不在html结构上绑定事件，使用$on()接收

         父级直接修改子级实例上的数据 $child
         子级直接修改父级实例上的数据 $parent

         vuex   数据量很大时
                通过mutation同步操作state
                通过action异步操作state

         provide返回一个对象，内部的属性值可以在所有子孙结点inject获取

126. 词法作用域和this的区别？

         词法作用域是在写代码或者说定义时确定的，而this是在运行时确定的。
         词法作用域关注函数在何处声明，而this关注函数从何处调用。

127. 常用的webpack plugins

         html-webpack-plugin 生成html
         copy-webpack-plugin 静态资源直接拷贝到打包后的文件夹
         extract-text-webpack-plugin 优化压缩
         uglifyjs-webpack-plugin

128. promise构造函数是同步还是异步，then呢？

129. [window的onload事件和domcontentloaded谁先谁后？](https://www.jianshu.com/p/d5cedce95acc)

         1 onload事件是DOM事件，onDOMContentLoaded是HTML5事件。
         2 onload事件会被样式表、图像和子框架阻塞，而onDOMContentLoaded不会。
         3 当加载的脚本内容并不包含立即执行DOM操作时，onDOMContentLoaded比onload事件执行时间更早。

130. 说一下箭头函数This指向问题

          父级作用域

131. 说一下你对generator的了解？

132. 说一下你对promise的了解？

133. for...in和for...of和Object.keys有什么区别？

         Object.keys与for in区别在于不能遍历出原型链上的属性
         for of不支持遍历普通对象，可通过与Object.keys()搭配使用遍历
         for of遍历后的输出结果为数组元素的值

134. 使用过flex布局吗？flex-grow和flex-shrink属性有什么用？

135. 箭头函数和普通函数有什么区别？

         无arguments
         无new
         不绑定this
         无原型属性

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

         function Promise(fn){
           var state = 'pending';
           var doneList = [];
           var failList= [];
           this.then = function(done ,fail){
             switch(state){
               case "pending":
                 doneList.push(done);
                 //每次如果没有推入fail方法，我也会推入一个null来占位
                 failList.push(fail || null);
                 return this;
                 break;
               case 'fulfilled':
                 done();
                 return this;
                 break;
               case 'rejected':
                 fail();
                 return this;
                 break;
             }
           }
           function resolve(newValue){
             state = "fulfilled";

           }
           function reject(newValue){
             state = "rejected";

           }
           fn(resolve,reject);
         }
         var p = function (){
             return new Promise(function(resolve,reject){
                 setTimeout(function(){
                   reject('p 的结果');
                 }, 100);
             });
         }

139. 介绍es6的功能

140. call和apply区别

141. 介绍defineProperty,什么时候用到？

142. 原生dom事件为什么不移除会造成内存泄漏？

143. 定时器为什么是不精确的？

144. setInterval有什么注意的？

            1.第一个参数必须是一个方法且必须加引号，否则只会执行一次
            2.SetInterval只能在方法外使用

145. 单例、工厂、观察者模式项目中的实际场景？

146. 项目中树组件的使用场景及了解？

147. 为什么虚拟dom比真实dom性能好？虚拟dom优缺点

            虚拟DOM不会进行排版与重绘操作,减少对dom操作的次数

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

            <b>是html的标签，而<strong>是web标准中xhtml的标签
            <b>标签是一个实体标签，<strong>标签是一个逻辑标签，它的作用是加强字符的语气

152. 介绍事件委托

153. 如何处理异常捕获

154. 类数组和数组的区别？如何将类数组转为数组

155. 平时怎么做继承？

156. 深拷贝怎么实现的？

157. let作用域怎么实现的？

158. 发布订阅者模式和观察者模式区别？

159. async、await怎么实现的

160. 如何解决props层级过深的问题？

161. 比较两个对象是否相等

         function isObjectValueEqual(a, b) {
             var aProps = Object.getOwnPropertyNames(a);
             var bProps = Object.getOwnPropertyNames(b);
             if (aProps.length != bProps.length) {
                 return false;
             }
             for (var i = 0; i < aProps.length; i++) {
                 var propName = aProps[i];
                 if (a[propName] !== b[propName]) {
                     return false;
                 }
             }
             return true;
         }

162. promise如何进行异常捕获

163. promise的三种状态

164. promise.all的实现原理

            function promiseAll(promises){
                return new Promise(function(resolve,reject){
                    if(!Array.isArray(promises)){
                        return reject(new TypeError("argument must be anarray"))
                    }
                    var countNum=0;
                    var promiseNum=promises.length;
                    var resolvedvalue=new Array(promiseNum);
                    for(var i=0;i<promiseNum;i++){
                        (function(i){
                            Promise.resolve(promises[i]).then(function(value){
                                countNum++;
                                resolvedvalue[i]=value;
                                if(countNum===promiseNum){
                                    return resolve(resolvedvalue)
                                }
                            },function(reason){
                                return reject(reason)
                            })

                        })(i)
                    }
                })
            }


165. webpack和gulp的区别

         gulp是基于流的自动化构建工具，但不包括模块化的功能，如果要用到的话，就需要引入外部文件，比如require.js等；
         而webpack是基于入口文件的自动化模块打包工具，自动地递归解析入口所需要加载的所有资源文件，本身就具有模块化，并且也具有压缩合并的功能。

166. 遇到的复杂的业务场景举例

167. 介绍Immuable.js

168. 如何实现异步加载

            defer/async/promise/动态script/ajax

169. 网站seo处理

170. 手写bind/call/apply?

171. async里有多个await请求，怎么优化

          promise.all()

172. 介绍Fiber

173. 前端怎么做单元测试？

174. 快速排序、选择排序、冒泡排序

175. 表单跨域

176. 实现 Vue SSR

            服务端渲染（服务器返回组装好的HTML字符串）
                    优点：更好的SEO
                         首屏加载更快，用户体验好
                    缺点：开发成本比较高，第三方中间件，如node

177. 有时间看下http1.1和http2.0

178. webpack的plugins怎么实现

179. Vue computed 实现

180. Vue complier 实现

181. webpack生命周期

182. chrome和safari的区别

        不同的 JavaScript 引擎定义初始化环境是不同的，这就形成了所谓的浏览器兼容性问题，
        因为不同的浏览器使用不同 JavaScipt 引擎(内核不同)。

183. 跨域是什么

184. Object.defineProperty能不能监视数组的变化？不能，那vue官方怎么解决的

185. 对加班怎么看的

          平时开发尽量提高自己的效率，在工作时间内完成，如果项目需求紧急当然加班是不可避免的,我也会全力配合的

186. http和tcp的区别

187. 如何判断两个对象相等

188. v-show和v-if的区别

            1. 频繁操作时，使用 v-show，一次性渲染完的，使用 v-if
            2. css
            3. v-if="false" 时，内部组件是不会渲染的，所以在特定条件才渲染部分组件（或内容）时，可以先将条件设置为 false，需要时（或异步，比如 $nextTick）再设置为 true，这样可以性能优化

189. props单向数据流的问题

190. 计算属性和 watch 的区别

                区别来源于用法，只是需要动态值，那就用计算属性；
                需要知道值的改变后执行业务逻辑，才用 watch

            computed 和 methods 有什么区别？

                methods 是一个方法，它可以接受参数，而 computed 不能；
                computed 是可以缓存的，methods 不会；一般在 v-for 里，
                需要根据当前项动态绑定值时，只能用 methods 而不能用 computed，因为 computed 不能传参。

            watch 是一个对象时，它有哪些选项？

                handler 执行的函数
                deep 是否深度
                immediate 是否立即执行

191. 递归组件

            要给组件设置 name；
            要有一个明确的结束条件

192. keep-alive 的理解

            keep-alive可以看做对组件的缓存方式，将组件的状态抽象成一个虚拟对象，每次缓存的时候将该对象存在数组中，
            路由更新的时候，直接获取缓存的对象

193. 自定义组件的语法糖 v-model 是怎样实现的

194. Vuex 中 mutations 和 actions 的区别

195. render函数是什么

196. 路由的跳转方式

            通过 <router-link to="home">，router-link 标签会渲染为 <a> 标签，在 template 中的跳转都是用这种；
            另一种是编程式导航，也就是通过 JS 跳转，比如 router.push('/home')。

197. vue-router 有哪几种导航守卫?

198. 对MVVM的理解？

200. React 中 keys 的作用是什么？

            在 React Diff 算法中 React 会借助元素的 Key 值来判断该元素是新近创建的还是被移动而来的元素，
            从而减少不必要的元素重渲染。

201. React中调用setState之后发生了什么？

            React会将当前传入的参数对象与组件当前的状态合并,
            根据新的状态构建React元素树自动计算出新的树与老的树的节点的差异,然后根据差异对界面进行按需更新

202. shouldComponentUpdate 是做什么的

            没有导致state的值发生变化的setState是否会导致重渲染？会
            组件的state没变化，从父组件接受的props也没变化，那还可能重渲染吗？可能

            shouldComponentUpdate接受两个参数：nextProps和nextState，当函数返回false时候，
            阻止接下来的render()函数的调用，阻止组件重渲染，而返回true时，组件照常重渲染。

            基本数据类型
            PureComponent避免state和props不变下的冗余的重渲染
            复杂数据类型
            immutable.js
            1 优点：深拷贝/浅拷贝本身是很耗内存，而immutable本身有一套机制使内存消耗降到最低
            2 缺点：你多了一整套的API去学习，并且immutable提供的set,map等对象容易与ES6新增的set,map对象弄混

203. react生命周期函数

            * 初始化阶段：
                * getDefaultProps:获取实例的默认属性
                * getInitialState:获取每个实例的初始化状态
                * componentWillMount：组件即将被装载、渲染到页面上
                * render:组件在这里生成虚拟的 DOM 节点
                * componentDidMount:组件真正在被装载之后
            * 运行中状态：
                * componentWillReceiveProps:组件将要接收到属性的时候调用
                * shouldComponentUpdate:组件接受到新属性或者新状态的时候（可以返回 false，接收数据后不更新，阻止 render 调用，后面的函数不会被继续执行了）
                * componentWillUpdate:组件即将更新不能修改属性和状态
                * render:组件重新描绘
                * componentDidUpdate:组件已经更新
            * 销毁阶段：
                * componentWillUnmount:组件即将销毁

204. 为什么虚拟 dom 会提高性能

            虚拟DOM，就是用JavaScript对象来构建DOM树。
            元素状态变更时会生成一颗新的JS结构树，利用差异算法与原来的JS对象树比较，
            由于减少了实际DOM操作次数，性能会有很大提升。

205. react diff 原理

            * 把树形结构按照层级分解，只比较同级元素。
            * 给列表结构的每个单元添加唯一的 key 属性，方便比较。
            * React 只会匹配相同 class 的 component（这里面的 class 指的是组件的名字）
            * 合并操作，调用 component 的 setState 方法的时候, React 将其标记为 dirty.到每一个事件循环结束, React 检查所有标记 dirty 的 component 重新绘制.
            * 选择性子树渲染。开发人员可以重写 shouldComponentUpdate 提高 diff 的性能。

206. 了解redux么，说一下redux原理

            redux主要是解决了组件间状态共享的问题，主要有三个核心方法: action，store，reducer。用户组件dispatch
            action给store,store接收action，通知reducer更新state,用户组件通过getState获取最新的数据
            优点：
                结构简单清晰，提高了编码效率
            缺点：
                * 一个组件所需要的数据，必须由父组件传过来，而不能像 flux 中直接从 store 取。
                * 当一个组件相关数据更新时，即使父组件不需要用到这个组件，父组件还是会重新 render，可能会有效率影响，或者需要 shouldComponentUpdate 进行判断。

207. react 组件的划分业务组件技术组件

            * 根据组件的职责通常把组件分为 UI 组件和容器组件。
            * UI 组件负责 UI 的呈现，容器组件负责管理数据和逻辑。
            * 两者通过 React-Redux 提供 connect 方法联系起来

208. React 中有三种构建组件的方式

            React.createClass()、ES6 class 和无状态函数

209. createElement 和 cloneElement 有什么区别？

210. 应该在 React 组件的何处发起 Ajax 请求

211. 调用 super(props) 的目的是什么

            在 super() 被调用之前，子类是不能使用 this 的，在 ES2015 中，子类必须在 constructor 中调用 super()。
            传递 props 给 super() 的原因则是便于(在子类中)能在 constructor 访问 this.props。

212. 描述事件在 React 中的处理方式

            为了解决跨浏览器兼容性问题，React 中的事件处理程序将传递 SyntheticEvent 的实例，它是 React 的浏览器本机事件的跨浏览器包装器。
            React 实际上并没有将事件附加到子节点本身。React 将使用单个事件监听器监听顶层的所有事件。
            这对于性能是有好处的，这也意味着在更新 DOM 时，React 不需要担心跟踪事件监听器。

213. 除了在构造函数中绑定 this，还有其它方式吗

            箭头函数
            bind(this)

214. 为什么建议传递给 setState 的参数是一个 callback 而不是一个对象

            异步更新

215. 何为高阶组件(HOC)

            一个以组件为参数并返回一个新组件的函数(如Redux 的 connect 函数)

216. 展示组件(Presentational component)和容器组件(Container component)之间有何不同

            * 展示组件关心组件看起来是什么。展示专门通过 props 接受数据和回调，并且几乎不会有自身的状态，但当展示组件拥有自身的状态时，通常也只关心 UI 状态而不是数据的状态。
            * 容器组件则更关心组件是如何运作的。容器组件会为展示组件或者其它容器组件提供数据和行为，它们会调用 redux，并将其作为回调提供给展示组件。

217. React 中 refs 的作用是什么？

            Refs 是 React 提供给我们的安全访问 DOM 元素或者某个组件实例的句柄。
            我们可以为元素添加 ref 属性然后在回调函数中接受该元素在 DOM 树中的句柄

218. 什么是 React?

            React.js 帮助我们将界面分成了各个独立的小块，每一个块就是组件，组件之间组合、嵌套，就成了我们的页面。
             * 一个组件的显示形态和行为有可能是由某些数据决定的。数据发生改变时，组件的显示形态就会发生相应的改变。
               React.js 提供了一种非常高效的方式帮助我们做到了数据和组件显示形态之间的同步。
             * React.js 不是一个框架，它只是一个库，只提供 UI （view）层面的解决方案。

219. Vue与Angular以及React的区别？

            Vue与AngularJS的区别

            Angular采用TypeScript开发, 而Vue可以使用javascript也可以使用TypeScript
            AngularJS依赖对数据做脏检查，所以Watcher越多越慢；Vue.js使用基于依赖追踪的观察并且使用异步队列更新，所有的数据都是独立触发的。
            AngularJS社区完善, Vue的学习成本较小

            React和Vue的区别？

            数据是不是可变的
            通过js操作一切还是各自的处理方式
            类式的组件写法还是声明式的写法（vue3.0后支持类式写法）
            什么交给社区去做，什么功能内置

            * vue组件分为全局注册和局部注册，在react中都是通过import相应组件，然后模版中引用；
            * props是可以动态变化的，子组件也实时更新，在react中官方建议props要像纯函数那样，输入输出一致对应，而且不太建议通过props来更改视图；
            * 子组件一般要显示地调用props选项来声明它期待获得的数据。而在react中不必需，另两者都有props校验机制；
            * 每个Vue实例都实现了事件接口，方便父子组件通信，小型项目中不需要引入状态管理机制，而react必需自己实现；
            * 使用插槽分发内容，使得可以混合父组件的内容与子组件自己的模板；
            * 多了指令系统，让模版可以实现更丰富的功能，而React只能使用JSX语法；
            * Vue增加的语法糖computed和watch，而在React中需要自己写一套逻辑来实现；
            * react的思路是all in js，通过js来生成html，所以设计了jsx，还有通过js来操作css，社区的styled-component、jss等；而 vue是把html，css，js组合到一起，用各自的处理方式，vue有单文件组件，可以把html、css、js写到一个文件中，html提供了模板引擎来处理。
            * react做的事情很少，很多都交给社区去做，vue很多东西都是内置的，写起来确实方便一些， 比如 redux的combineReducer就对应vuex的modules， 比如reselect就对应vuex的getter和vue组件的computed， vuex的mutation是直接改变的原始数据，而redux的reducer是返回一个全新的state，所以redux结合immutable来优化性能，vue不需要。
            * react是整体的思路的就是函数式，所以推崇纯组件，数据不可变，单向数据流，当然需要双向的地方也可以做到，比如结合redux-form，组件的横向拆分一般是通过高阶组件。而vue是数据可变的，双向绑定，声明式的写法，vue组件的横向拆分很多情况下用mixin。

220. 状态(state)和属性(props)之间有何不同

            State是一种数据结构，用于组件挂载时所需数据的默认值
            Props是组件的配置，props由父组件传递给子组件，就子组件而言，props 是不可变的。

221. 命令式编程(Imperative)、声明式编程(Declarative)和函数式编程(Functional)

            声明式编程的编写方式描述了应该做什么，而命令式编程描述了如何做，函数式编程是声明式编程的一部分。

222. 什么是 JSX

            JSX是javascript的语法扩展，结合了javascript和HTML，并生成了可以在DOM中呈现的react元素。

223. 什么是PropTypes

            PropTypes为组件提供类型检查

224. 什么是 React Router Dom 及其工作原理

            react-router-dom 提供两个路由器BrowserRouter和HashRoauter。
            区别：browserHistory 是使用浏览器中的 History API 用于处理 URL，由于路径是指向服务器的真实路径，
            如果该路径下并没有相关资源，所以用户访问的资源不存在；hashHistory 使用 URL 中的 hash（#）部分去创建路由。

225. 什么是错误边界

            如果类实现了componentDidCatch 那么这个类就会成为错误边界。
            前者返回{hasError: true}来呈现回退UI，后者用于记录错误。

226. 什么是 Fragments

            在React中，我们需要有一个父元素，同时从组件返回React元素。使用 Fragments，我们不需要在DOM中添加额外的节点。

227. 什么是上下文

            有时我们必须将props 传递给组件树，即使所有中间组件都不需要这些props 。上下文是一种传递props 的方法，而不用在每一层传递组件树。


228. 如何提高性能

            * 适当地使用shouldComponentUpdate生命周期方法。 它避免了子组件的不必要的渲染。 如果树中有100个组件，则不重新渲染整个组件树来提高应用程序性能。
            * 使用create-react-app来构建项目，这会创建整个项目结构，并进行大量优化。
            * 不可变性是提高性能的关键。不要对数据进行修改，而是始终在现有集合的基础上创建新的集合，以保持尽可能少的复制，从而提高性能。
            * 在显示列表或表格时始终使用 Keys，这会让 React 的更新速度更快
            * 代码分离是将代码插入到单独的文件中，只加载模块或部分所需的文件的技术。

229. redux-thunk 工作流程

            用户组件dispatch触发actionCreator函数，actionCreator函数异步请求拿到数据，
            将数据传递给store,store派发给reducer,reducer去更新对应的state。

230. 如何在重新加载页面时保留数据

            localStorage

231. 什么是 Hooks

            Hooks是React 16.8提出的新特性，体现在处理组件之间复用状态逻辑的问题，
            保证在函数组件中可以使用state以及生命周期等功能处理.

            * Hooks 应该在外层使用，不应该在循环，条件或嵌套函数中使用
            * Hooks 应该只在函数组件中使用。

232. React中组件通信的几种方式,分别说说

            父组件向子组件通信
                父级绑定属性 子级props接收
            子组件向父组件通信
                调用父级的回调函数去更新
            跨级组件通信
                * 层层组件传递props
                * context
                    父组件提供Context需要通过childContextTypes进行“声明”，
                    子组件使用父组件的Context属性需要通过contextTypes进行“申请”，
                    所以，我认为React的Context是一种“带权限”的组件作用域
            没有嵌套关系组件之间的通信
                自定义事件events,父组件通过emitter自定义事件声明,子组件触发事件更新
            redux
                actionCreators、constants、reducer增加多点约束来保证代码质量

233. 受控组件和非受控组件

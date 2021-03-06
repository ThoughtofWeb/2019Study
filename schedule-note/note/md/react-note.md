# ReactJS 学习之路

## React.js简介

 >  * React.js 将帮助我们将界面分成了各个独立的小块，每一个块就是组件，组件之间组合、嵌套，就成了我们的页面。
 * 一个组件的显示形态和行为有可能是由某些数据决定的。数据发生改变时，组件的显示形态就会发生相应的改变。
      React.js 提供了一种非常高效的方式帮助我们做到了数据和组件显示形态之间的同步。
 * React.js 不是一个框架，它只是一个库，只提供 UI （view）层面的解决方案。
      在实际的项目当中，它并不能解决我们所有的问题，需要结合其它的库，
      例如 Redux、React-router 等来协助提供完整的解决方法。


## JSX简介

    JSX，一种 JavaScript 的语法扩展，在 JavaScript 内部实现的，使用时必须引入React库

  1. 表达式要包含在大括号里

  ```
      1. {formatName(user)} 参数user也可以是一个JSX表达式 ==> JS对象
      2. {1+1}
      3. 大括号来定义以 JavaScript 表达式为值的属性
         const element = <img src={user.avatarUrl}></img>;
  ```
  2. 引号来定义以字符串为值的属性

  `const element = <div tabIndex="0"></div>;`

  3. * 驼峰命名属性
     * 闭合式
     * 可相互嵌套

  4. 防注入攻击

            React DOM 在渲染之前默认会过滤/转义所有传入的值。
            它可以确保你的应用不会被注入攻击。
            所有的内容在渲染之前都被转换成了字符串。
            这样可以有效地防止 XSS(跨站脚本) 攻击。

            转义html字符串
            dangerouslySetInnerHTML = {{_html:this.props.content}}

  5. 元素渲染
      * 定义一个根节点
          `<div id="root"></div>`
      * 渲染(React DOM只会更新渲染文本节点中发生变化的内容)

            创建一个新的元素，然后将它传入ReactDOM.render()方法
            const element = <h1>Hello, world</h1>;
            ReactDOM.render(element, document.getElementById('root'));

  6. 自定义组件

    * 组件开头必须大写字母

    * 函数定义

            function Welcome(props) {
                return <h1>Hello, {props.name}</h1>;
            }

    * ES6 Class定义

            import { Component } from 'react';
            等价于
            import React from 'react';
            const Component = React.Component;

            class Welcome extends React.Component {
                 render() {
                   return <h1>Hello, {this.props.name}</h1>;
                   <!-- return 的内容可为空数组 标签 但不可为对象 -->
                 }
            }

    * 组件传参

            父级向子级父级绑定属性，子级使用props接收，只读性，子级可以通过这种方式修改父级的数据

    * [事件内this的指向问题](https://blog.csdn.net/qq_34829447/article/details/81705977)
        https://www.jianshu.com/p/c1ee12a328d2
        箭头函数 VS bind(this)

  7. State & 生命周期

      * 添加一个类构造函数来初始化状态 this.state

                constructor(props){
                <!-- 子组件无法直接获取父组件的属性值 通过super()继承便可 -->
                   super(props);
                   this.state = {date: new Date()}
                }

      * 生命周期-钩子

                componentWillMount页面挂载之前执行
                render页面挂载
                componentDidMount(数据请求 )页面挂载之后执行

                shouldComponentUpdate组件更新之前执行（要求返回一个布尔类型的值）
                componentWillUpdate组件更新之前执行（shouldComponentUpdate返回true才会执行）
                render组件更新
                componentDidUpdate组件更新之后执行

                componentWillReceiveProps（子组件从父组件接收参数，只要父组件的render函数被触发了，则生命周期被触发，如果该组件第一次存在于父组件则不会被触发）
                componentWillUnmount移除组件


      * 不要直接更新状态，因为 this.props 和 this.state 可能是异步更新的，不应该依靠它们的值来计算下一个状态，应当使用 setState():

                this.setState({comment: 'Hello'},() => {异步函数});
                异步更新的时候，e.target.value当前的e获取不到，需要在setState函数外面定义一下

      * state和props的更新都会触发render函数的更新

  9. immutable 不允许对state做任何修改，拷贝一份再修改

  10. 虚拟DOM

            优点：性能优化
                 跨终端运行 ReactNative

            diff算法
                 利用key值进行同层比对(一般不用index做key值，因为index不稳定)

  11.

  12. ref(一般用于获取页面上的DOM节点)

            ref="(ul) => (this.ul = ul)"
            不推荐使用，一般用数据绑定，不要直接操作dom，有异步问题

  12. > 注意点

          1. 样式类名使用className而不是class
          2. label中的for更新为htmlFor
          3. propTypes规定组件传值的值类型
          4. defaultProps设置默认属性
          5. 代码注释
                 { /*狗屎 */ }
                 或者
                 {
                   // 狗屎
                 }

          6. UI组件（用于页面渲染，render函数）
             容器组件（处理业务逻辑）
             无状态组件（一个组件不需要处理任何逻辑，只有render函数，建议改写为无状态组件）

## Redux = reducer + flux

        执行过程：
            创建公共数据仓库createStore，用户组件执行某个动作，触发dispatch函数,传递action对象,
            (如果要进行一些异步操作，需要使用react中间件，使dispatch能传递异步函数)，
            store通知reducer的action函数去判断并进行数据操作，组件调用store.subscribe(callback...)，
            只要store数据更新，subscribe函数就被调用。用户组件通过this.state = store.getState()去获取，通过setState()去更新

        使用原则：
            store是唯一的
            只有store可以改变自己的内容
            reducer是纯函数(给定固定的输入，一定会有固定的输出，而且不会有任何的副作用
            （不能直接修改给定的参数，不能有如setTimeout、ajax、时间操作）)

        * store 公共数据存储仓库（依赖reducer）
        * reducer 存储store中的所有数据
                传递两个参数：
                   state  仓库里上一次所有的数据集合
                          reducer可以接收state, 但绝不能修改state(拷贝一份再做修改)
                   action 用户要处理的行为函数
        * redux-thunk 使用中间件处理异步请求，使action抽象为一个函数传入，便于统一管理代码，便于自动化测试
        * redux-saga

        代码优化

            1. actionTypes文件 变量和常量抽出来引用
               const CHANGE_TYPE = 'change_type';
            2. actionCreator

## styled-components 使组件的样式单一，不会互相影响

        * styled-components v4+解决全局样式'injectGlobal' 废除的问题
          https://www.cnblogs.com/cxx9759/p/9807866.html

## [immutable.js 保证state是不可变更的](https://segmentfault.com/a/1190000002909224)

        避免reducer中总是返回一个新的state对象，同时保证state是不可变更的，
        使用immutable对象(state = fromIs({...}))的set()方法，
        会结合之前的immutable对象的值，和设置的值，返回一个全新的对象，用户组件通过get()方法去获取设置的值

        常用的api见链接

## [React-router](https://www.cnblogs.com/sunLemon/p/9020153.html)

##









## Get Started
   1. npx create-react-app my-app
      或者npm install -g create-react-app
         create-react-app my-app
   2. cd my-app
   3. npm start     运行项目
   4. npm run build 打包项目
   5. 文件介绍
        src/index.js  入口文件
        registerServiceWorker https协议在服务器上，离线访问（PWA）
        manifest.json 快捷方式到桌面进行离线访问
        App.test.js 前端自动化测试文件（一般用于自动化测试）
   > 这两个命令主要有以下区别：
        * 前者中默认使用 webpack.config.js 作为配置文件
        * 而后者中强制使用 webpack.production.config.js 作为配置文件
        * 前者NODE_ENV=dev而后者NODE_ENV=production，标识不同的环境
        * 而这个"dev" "production"可以在代码中通过process.env.NODE_ENV获取

    ```
    "scripts": {
        "start": "NODE_ENV=dev webpack-dev-server --progress --colors",
        "build": "rm -rf ./build && NODE_ENV=production webpack --config ./webpack.production.config.js --progress --colors"
      },
    ```

## 项目技术点介绍
    ├─构建工具
    │  ├─webpack (搭建react环境)
    │  ├─babel (编译ES6)
    │  ├─less (写css)
    │  ├─postcss (编译css)
    ├─系统框架
    │  ├─React
    │  ├─React-router
    │  ├─Redux
    ├─数据交互
    │  ├─fetch (原生支持promise)
    │  ├─mock (数据模拟，便于前后端分离)

   切换端口号

        npm run build
        cd build
        http-server -p 8881

   安装依赖

        package.json中 devDependencies ==> npm install webpack-dev-server --save-dev 不需要更新的插件
                         dependencies ==> npm i react react-dom --save 迭代开发中需要更新

   webpack.config.js 开发环境下

        文件格式
        普通的js文件，符合commonJS规范，基于node环境，最后输出一个对象
        require("xxx") --> 先去package.json安装的依赖中找xxx插件，系统会自动捕获到node_modules中xxx.js

        输入&输出
        entry  入口文件 app/index.jsx
        output 输出文件 bundle.js webpack在开发环境下所有的js&css代码，实时更新 上线后与其无关

        resolve:{'','.js','.jsx'}
        后缀名扩展

        module
        loaders 加载器
                编译es6和jsx时用到babel
                加载css/less时用postcss
                图片、字体...

        plugins 插件
        使用html模版 html-webpack-plugin 可以将输出的文件名（如bundle.js）自动注入到html中，
                                        不用手写，手写需要改两个地方
        使用热加载插件
        使用自动打开浏览器插件
        使用_DEV_插件判断是否是开发环境

        devServer
        color 终端输出是否为彩色
        historyApiFallback 不跳转 *单页应用*
        inline 实时刷新
        hot 是否使用热加载插件

   webpack.production.config.js 发布系统后，需考虑系统的性能（加速度、缓存等）

        发布到./build文件夹中

        vendor 将第三方依赖单独打包 （将node_modules文件夹中的代码打包为vendor.js 将自己的业务代码打包为app.js）
                有利于缓存 （原因：项目维护中，第三方依赖不经常变化，而业务代码经常变化）

        md5后缀 为每个打包的文件都加md5后缀，使文件强缓存

        分目录 不同的文件打包在不同的目录下

        plugins
        分模块
        new webpack.optimize.OccurenceOrderPlugin()

        压缩代码
        使用 Uglify 压缩代码，其中warnings: false是去掉代码中的 warning

        分离 css 和 js 文件
        开发环境下，css 代码是放在整个打包出来的那个 bundle.js 文件中的，发布环境下当然不能混淆在一起，使用new ExtractTextPlugin('/css/[name].[chunkhash:8].css'),将 css 代码分离出来。

## [源码解析](https://react.jokcy.me/book/api/react-element.html)

   1. 背景

          react16版本以后完全改写了以前的代码，但是使用者未有丝毫感觉，
          不像vue和angular迭代更新需要处理很多兼容问题，最重要的是
          引入了fiber,从根本上解决了如果js单线程计算量太大的话会有卡顿情况。
          React16版本后新增Fragment标签替换最外层的div元素，不会被展示出来

   2. jsx语法到js转化(jsx-->虚拟DOM-->真实的DOM对象)

   (使用babel观察https://www.babeljs.cn/repl#?babili=false&browsers=&build=&builtIns=false&spec=false&loose=false&code_lz=DwEwlgbgBGILwCIQgVAdgQwLYFNEGN8EA-AFxwA9SAoYAZwAcM1iAmV4AekeeNs_ARiQA&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=es2015%2Creact%2Cstage-2&prettier=false&targets=&version=7.4.5)

   3. ReactElement

          ReactElement通过createElement创建，调用该方法需要传入三个参数：
               type 指代这个ReactElement的类型
               config 属性参数
               children

   4. ref使用方式
     
          * string ref
               绑定 <a ref="stringRef"></a>
               获取 this.refs.stringRef.textContent
          * function
               绑定 <a ref = {ele => (this.methodRef = ele)}></a>
               获取 this.methodRef.textContent
          * createRef
               绑定 <a ref={this.objRef}></a>
                    this.objRef = React.createRef()
               获取 this.objRef.current.textContent
               








## 学习锦囊

  * [react集锦](http://huziketang.mangojuice.top/books/react/lesson2)
  * [JSX语法](https://react.docschina.org/docs/introducing-jsx.html)
  * [CodePen代码调试工具](https://codepen.io/gaearon/pen/PGEjdG?editors=0010)

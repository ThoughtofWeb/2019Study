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

      * 不要直接更新状态，因为 this.props 和 this.state 可能是异步更新的，不应该依靠它们的值来计算下一个状态，应当使用 setState():

                this.setState({comment: 'Hello'});
                异步更新的时候，e.target.value当前的e获取不到，需要在setState函数外面定义一下

   8. React16版本后新增Fragment标签替换最外层的div元素，不会被展示出来

   9. immutable 不允许对state做任何修改，拷贝一份再修改

   10. 代码注释

            { /*狗屎 */ }
            或者
            {
              // 狗屎
            }

   11. 样式类名使用className而不是class

   12. label中的for更新为htmlFor


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






## 学习锦囊

  * [react集锦](http://huziketang.mangojuice.top/books/react/lesson2)
  * [JSX语法](https://react.docschina.org/docs/introducing-jsx.html)
  * [CodePen代码调试工具](https://codepen.io/gaearon/pen/PGEjdG?editors=0010)

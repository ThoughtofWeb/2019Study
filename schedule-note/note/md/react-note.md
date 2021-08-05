🤔️ReactJS 学习

## React.js简介

 >  React.js 将帮助我们将界面分成了各个独立的小块，每一个块就是组件，组件之间组合、嵌套，就成了我们的页面。
 * 一个组件的显示形态和行为有可能是由某些数据决定的。数据发生改变时，组件的显示形态就会发生相应的改变。
      React.js 提供了一种非常高效的方式帮助我们做到了数据和组件显示形态之间的同步。
 * React.js 不是一个框架，它只是一个库，只提供 UI （view）层面的解决方案。
      在实际的项目当中，它并不能解决我们所有的问题，需要结合其它的库，
      例如 Redux、React-router 等来协助提供完整的解决方法。

## React.js特点

- 单向数据流
- 数据不可变
- 组件复用
- 函数式编程

## Get Started

 > create-react-app 集成了webpack,可以直接做脚手架构建react单页应用

1. 安装命令
   npx create-react-app my-app
   或者
   npm install -g create-react-app
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

    "scripts": {
        "start": "NODE_ENV=dev webpack-dev-server --progress --colors",
        "build": "rm -rf ./build && NODE_ENV=production webpack --config ./webpack.production.config.js --progress --colors"
      }

## [JSX简介](https://react.docschina.org/docs/introducing-jsx.html)

    由于渲染的逻辑处理与UI逻辑其实是耦合的，所以需要将html和js结合成一个模块，而JSX，可以理解为是一种 JS 的语法扩展，将DOM节点以react元素的形式展现（使用时必须引入React库）

  1. 表达式要包含在大括号里

  ```
      1. {formatName(user)} 参数user也可以是一个JSX表达式 ==> JS对象
      2. {1+1}
      3. 大括号来定义以 JavaScript 表达式为值的属性
         const element = <img src={user.avatarUrl}></img>;
  ```
  2. 引号来定义以字符串为值的属性

```
const element = <div tabIndex="0"></div>;
```

  3. 组件特点
  * 驼峰命名属性
  * 闭合式
  * 可相互嵌套

4. 防注入攻击

```
    React DOM 在渲染之前默认会过滤/转义所有传入的值。
    它可以确保你的应用不会被注入攻击。
    所有的内容在渲染之前都被转换成了字符串。
    这样可以有效地防止 XSS(跨站脚本) 攻击。

    转义html字符串
    dangerouslySetInnerHTML = {{_html:this.props.content}}
```
## 元素渲染（render）

* 定义一个根节点
      `<div id="root"></div>`
  
* 渲染(React DOM只会更新渲染文本节点中发生变化的内容)

     // 创建一个新的元素，然后将它传入ReactDOM.render()方法
     
     1. 元素变量
     
     const element = <h1>Hello, world</h1>;
     ReactDOM.render(element, document.getElementById('root'));
     
     2. 条件返回
       
             const isGoodWord = true
             return (
                 <div>
                 <h1>                
                     {isGoodWord ? 
                     <strong> is good</strong> : 
                     <span> is not good</span>        
                     }      
                 </h1>    
             </div>) 
     
     3. 表达式

            render () {
                const word = 'is good'
                return (
                  <div>
                    <h1>React 小书 {word}</h1>
                  </div>
              )
            }
     4. Tips
```
 // 返回并列多个 JSX 元素是不合法的， 必须要用一个外层元素把内容进行包裹
render () {
  return (
    <div>
      <div>第一个</div>
      <div>第二个</div>
    </div>
  )
}
```

## 自定义组件

    * 组件开头必须大写字母，普通的 HTML 标签都用小写字母开头。
    
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

## state和props

- state 是组件的数据结构，挂载了组件的初始状态，可通过用户事件更新数据状态
- props是组件的属性配置，由父组件向子组件传递的，就子组件而言，数据不可变

## 事件监听

        1. React.js 封装好了一系列的 on* 的事件，但是监听只能用在普通的 HTML 的标签上，而不能用在组件标签上
    
        class Title extends Component {
            handleClickOnTitle (event) {  
                // React.js 将浏览器原生的 event 对象封装了一下，对外提供统一的 API 和属性， 这样就不用考虑兼容性问题
                console.log('Click on title.')
                console.log(this) // => null or undefined
            }
            render () {
                return (
                <h1 onClick={this.handleClickOnTitle}>React</h1>
                )
            }
        }
        2. this指向
        因为react调用方法时，onclick相当于中间变量，处理函数中的this指向会丢失，不是通过对象方法的方式调用（this.handleClickOnTitle），所以事件监听函数内并不能通过 this 获取到实例。
        解决方案：
        * 箭头函数
          handleClickOnTitle = () => {...}
        * bind方法
          <h1 onClick={this.handleClickOnTitle.bind(this)}>...</h1>

## 组件更新setState

> 注意： 不能直接用 `this.state = xxx` 这种方式来修改， 因为react没有双向数据绑定，无法监视组件状态的更新，所以需要setState去触发

* 参数为对象

```
constructor (props) {
    super(props)
    this.state = {
      name: 'Tomy',
      isLiked: false
    }
  }

  handleClickOnLikeButton () {
    console.log(this.state.isLiked)   ===> false
    this.setState({
      isLiked: !this.state.isLiked
    })
    console.log(this.state.isLiked)	  ===> false	
  }
  // react调用setState时，不会立即更新state,首先将该对象放到更新队列里，稍后将队列中的对象与传入的对象状态进行合并，再触发更新
```

* 参数为函数

```
// react会将上一个setState的结果传入下一个函数，依赖传递（对象也适用）
handleClickOnLikeButton () {
    this.setState((prevState) => {
      return { count: 0 }
    })
    this.setState((prevState) => {
      return { count: prevState.count + 1 } // 上一个 setState 的返回是 count 为 0，当前返回 1
    })
    this.setState((prevState) => {
      return { count: prevState.count + 2 } // 上一个 setState 的返回是 count 为 1，当前返回 3
    })
    // 最后的结果是 this.state.count 为 3
  }
```

## 组件传值通信

        * 父 -> 子            
        父级向子级父级绑定属性，子级使用props接收，只读性
        * 子 -> 父
        子级可以通过调用父级的回调函数修改父级的数据
        * 兄弟节点通信 -> EventEmitter
        * 系统级应用组件通信(避免层层嵌套props) -> redux/mobx
    
    * [事件内this的指向问题](https://blog.csdn.net/qq_34829447/article/details/81705977)
        https://www.jianshu.com/p/c1ee12a328d2
        箭头函数 VS bind(this)

## State & 生命周期

* 添加一个类构造函数来初始化状态 this.state

          constructor(props){
          <!-- 子组件无法直接获取父组件的属性值 通过super()继承便可 -->
             super(props);
             this.state = {date: new Date()}
          }

* 生命周期-钩子

  1. react v16之前

              componentWillMount页面挂载之前执行
              render生成虚拟DOM
              componentDidMount(数据请求 )页面挂载之后执行
                
              shouldComponentUpdate组件更新之前执行（要求返回一个布尔类型的值）
              componentWillUpdate组件更新之前执行（shouldComponentUpdate返回true才会执行）
              render组件重绘
              componentDidUpdate组件更新之后执行
                
              componentWillReceiveProps（子组件从父组件接收参数，只要父组件的render函数被触发了，则生命周期被触发，如果该组件第一次存在于父组件则不会被触发）
              componentWillUnmount移除组件
  2. react v16之后
  
             初始化：getDrivedStateFromProps  获取组件的初始状态
             render  组件生成虚拟DOM节点
             componentDidMount  组件实例挂载
             运行中：getDrivedStateFromProps  获取组件的更新状态
             shouldComponentUpdate  判断哪个组件状态需要更新
             render  组件重绘
             getSnapShotBeforeUpdate  组件即将更新，不能修改属性和状态
             componentDidUpdate  组件已更新
             销毁：componentWillUnmount  组件销毁.

> Tips:
      * 不要直接更新状态，因为 this.props 和 this.state 可能是异步更新的，不应该依靠它们的值来计算下一个状态，应当使用 setState():
            this.setState({comment: 'Hello'},() => {异步函数});
            异步更新的时候，e.target.value当前的e获取不到，需要在setState函数外面定义一下
            * state和props的变化都会触发render函数的更新

## Ref

         ref用于获取组件实例或者DOM节点，进行传值通信
         绑定方式：
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
    
         // 不推荐使用，一般用数据绑定，不要直接操作dom，有异步问题

## 样式处理

    style接受一个对象，这个对象里面是这个元素的 CSS 属性键值对，驼峰命名，如 font-size 换成 fontSize    
    <h1 style={{fontSize: '12px', color: 'red'}}>React.js </h1>
    
    styled-components 使组件的样式单一，不会互相影响（https://styled-components.com/docs/basics）
    (利用createGlobalStyle 新的API ，作为一个样式组件出现，按照样式组件思想，以一个标签形式被引入)

## Redux = reducer + flux

        原理：context(状态上下文)
        	父组件设置了 context，那么子组件都可以直接访问到里面的内容，任意深度的子组件都可以通过 contextTypes 来声明想要的 context 里面的哪些状态，然后可以通过 this.context 访问到那些状态。
        
        执行过程：
            创建公共数据仓库createStore，用户组件执行某个动作，触发dispatch函数,传递action对象,
            (如果要进行一些异步操作，需要使用react中间件，使dispatch能传递异步函数)，
            store通知reducer的action函数去判断并进行数据操作，组件调用store.subscribe(callback...)，
            只要store数据更新，subscribe函数就被调用。用户组件通过this.state = store.getState()去获取，通过setState()去更新
           
             // 定一个 reducer
            function reducer (state, action) {
            /* 初始化 state 和 switch case */
            }
            // 生成 store
            const store = createStore(reducer)
            // 监听数据变化重新渲染页面
            store.subscribe(() => renderApp(store.getState()))
            // 首次渲染页面
            renderApp(store.getState())
            // 后面可以随意 dispatch 了，页面自动更新
            store.dispatch(...)
    
        使用原则：
            store是唯一的
            只有store可以改变自己的内容
            reducer是纯函数(给定固定的输入，一定会有固定的输出，而且不会有任何的副作用
            （不能直接修改给定的参数，不能有如setTimeout、ajax、时间操作）)
    
        核心模块：
        * store 公共数据存储仓库（依赖reducer）
        * reducer 存储store中的所有数据
                传递两个参数：
                   state  仓库里上一次所有的数据集合
                          reducer可以接收state, 但绝不能修改state(拷贝一份再做修改)
                   action 用户要处理的行为函数
        * redux-thunk/redux-saga 使用中间件处理异步请求，使action抽象为一个函数传入，便于统一管理代码，便于自动化测试
        * redux-promise-middleware 使用promise处理异步
        * immutable.js 保证state是不可变更的(https://segmentfault.com/a/1190000002909224)
            避免reducer中总是返回一个新的state对象，同时保证state是不可变更的，
            使用immutable对象(state = fromIs({...}))的set()方法，
            会结合之前的immutable对象的值，和设置的值，返回一个全新的对象，用户组件通过get()方法去获取设置的值

## [mobx](https://cn.mobx.js.org/)

    	原理：
    类比vue --> Object.defineProperty(Mobx4)或Proxy(Mobx5)
    mobx模拟observer这个装饰器，对React组件的render方法进行track(依赖收集)。调用render方法，加入到各个observable的依赖中。当observable发生变化，会调用set方法，就是依次执行该Observable之前收集的依赖函数，track方法就会执行。track中，还是先进行依赖收集，调用forceUpdate去更新组件
    
    	执行过程：
    通过provide将所有的stores注入，在当前组件中inject引入该store，使用observer保证组件的observerable能监视到状态的更新，store通过dispatch action通知组件视图更新
    
    	核心模块：
    	* store 公共数据存储仓库（依赖observer）
    	* observable 观察数据对象的变化
    	* action 用户要处理的行为函数
    		runInAction 内置异步回调
    
    import { observable, computed } from "mobx";
    class OrderLine {
        @observable price = 0;
        @observable amount = 1;
    
        @computed get total() {
            return this.price * this.amount;
        }
    }
    
    	mobx与redux区别：
    	* store的管理不同（redux是多个模块共享一个store，而mobx是根据模块划分多个store）
    	* 数据可变性（redux更新对象遵循的是数据的不可变性，通过返回一个新的对象去更新，而mobx是监听观察对象，直接更新该对象）
    	* 对数据的更新方式（redux是通过dispatch actions更新视图，而mobx是通过监听对象的属性去更新视图）
    
    

## [React-router](https://www.cnblogs.com/sunLemon/p/9020153.html)

HashRouterr

HistoryRouter

## react和vue区别

- 数据是不是可变的（react推崇单向数据流，数据不可变，vue是双向数据绑定）
- 通过js操作一切还是各自的处理方式（react可以用js生成html，用js操作css，而vue是各文件单独处理）
- 类式的组件写法还是声明式的写法（vue3.0后支持类式写法）
- 什么交给社区去做，什么功能内置

## 注意点


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

## 项目工程化介绍

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

  * [react小书](http://huziketang.mangojuice.top/books/react/lesson2)
  * [JSX语法](https://react.docschina.org/docs/introducing-jsx.html)
  * [源码解析](https://react.jokcy.me/book/api/react-element.html)
  * [router配置](http://react-guide.github.io/react-router-cn/)
  * [router入门](http://www.ruanyifeng.com/blog/2016/05/react_router.html)
  * 


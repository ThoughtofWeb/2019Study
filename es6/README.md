# 深入理解es6

## let 声明（禁止重复声明）(同const)

    var a = 1;
    let a = 3;
    ----------wrong---------
    var a = 2;
    if(condition){
        let a = 4;
    ----------true----------
    }


## const声明
1. 声明必须赋值（初始化），否则wrong
    ```
    const q;
    ----------wrong---------
    let q;
    ----------true----------
    ```

2. 试图对之前用const声明的常量赋值会报错
    ```
    const q = 3;
    q = 4;
    ----------wrong---------
    let q = 3;
    q = 4
    ----------true----------
    ```

3. 声明对象(阻止对变量绑定的修改，而非对成员值的修改)
    ```
    const person = {
        name : 'cxx'
    }

    person.name = 'ppc'
    ----------true----------
    person = {
        name : 'ppc'
    }
    ----------wrong---------
    ```

4. 暂时性死区(声明之前都是无法被访问的)
    ```
    console.log(typeof a)
    let a = 1;
    ----------wrong---------
    const a = 1;
    ----------wrong---------
    ```

5. 循环内的声明

    for-in和for of中const和let声明一样

    单纯的for循环不能用const定义

## 字符串的方法
1. repeat(value) (value为重复的次数)
    ```
    'cxx'.repeat(1) --> 'cxxcxx'
    ```

2. 模版字面量(反引号``)
    ```
    let message = `cxx`;
    <!--  多行字符串  -->
    let message = `cxx
    ppc`;
    ```

3. 制造替换位${变量名}

## 函数
1. 参数模拟默认值
    ```
    第一个参数始终要被传递，其余参数都有默认值，调用时优先使用传递的 其次考虑默认的
    传递的参数可以为null或undefined
    function getMessage(name,age = 12 , callback = function(){}){
    }
    ```

2. 参数默认值影响arguments
    ```
    function getMessage(name,age = 12){
        name = 'ppx';
        age = 22;
    }
    getMessage('cxx')
    函数内改变参数值不会对arguments产生影响 arguments受实参的值影响
    ```
3. 暂时性死区
    ```
    function getMessage(name=age,age){
            name = 'ppx';
            age = 22;
        }
    getMessage(undefined,'cxx')
    ----------wrong---------
    ```
4. 剩余参数···args
    ```
    1. 函数只能有一个剩余参数，并且它必须被放在最后
    1. 剩余参数不能在对象字面量的setter属性中使用
    function pick(object, ...args){
    }
    ```

5. ***牛逼好用*** [扩展运算符和剩余参数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

6. ES6的名称属性( ES6给所有函数都添加了name属性 )

    判断函数如何被调用
    * ES5 --> A instance of B
    * ES6 --> new target 元属性 函数构造器会在未使用new 调用时报错

7. 块级函数
    ```
        if(true) {
            consolo.log(typeof getData)
            function getData(){}
            getData()
        }
        consolo.log(typeof getData)
    ES6 严格模式      函数为块级声明，允许他在所定义的代码块内访问

    ES6 非严格模式    函数会被提升到全局作用域，代码块外部仍然可以使用
    ```

8. 箭头函数

    * 小括号（）的使用情况
        1. 需要传入多于一个参数 -- Condition 2
        2. 函数内没有参数，声明时需要使用一对空括号 -- Condition 4
        3. 箭头函数想要从函数体内向外返回一个对象字面量，必须将该字面量包裹在圆括号内 -- Condition 3

    ```
    Condition 1
        var getData = value => value

    ```
    ```
    Condition 2
        var getData = (s1,s2) => {
                return s1 + s2
        }

        ==>

        var getData = (s1,s2) => s1 + s2
    ```
    ```
    Condition 3
        var getData = id => ({name : 'cxx' , id : id})
    ```
    ```
    Condition 4
        var message = () => 'cxx'
    ```
    * 花括号｛｝的使用情况 -- 函数体

    * 创建立即调用函数表达式
    ```
        (function() {/*函数体*/}()) || (function() {/*函数体*/})()

        ==>

        (() => {/*函数体*/})()
    ```
    * 没有this绑定

    箭头函数内部的this只能通过作用域链来确定

        1. 如果箭头函数被包含在非箭头函数内，this指向为该非箭头函数对象
        2. 反之，this指向全局对象window

    ```
        var handler = {
            name: 'cxx',
            init: function() {
                document.addEventListener('click',(function () {
                    console.log(this.name);
                }).bind(this),false)

                ==>

                document.addEventListener('click',() => console.log(this.name),false)
            }
        }
    ```

    * 不能使用new运算符调用
    ```
        var getData = () => {},
        object = new getData();
        --------------wrong-----------------

    ```
    * 没有arguments绑定
    ```
        尽管箭头函数没有自己的arguments对象。但是可以访问包含它的函数的arguments对象
        function getData(s1) {
                    return () => arguments[0]
        }
        var message = getData(5)
        console.log(getData(5)())
    ```

## 扩展对象
   * 属性简写
    ```
        function person(name, age) {
            return {
                name,
                age
            }
        }
    ```

   * 方法简写
    ```
        var person = {
            getName() {}
            ==>
            getName: function(){}
        }
    ```
   * 计算属性名  用方括号表示法[] 可以包含表达式
   ```
      var suffix = 'name';
      var person = {
        ['first'+name] : 'C'
      }
   ```
   * 新方法
    1. Object.is() ----用来弥补严格相等运算符===残留的怪问题
    ```
        console.log(NaN === NaN) --> false
        Object.is(NaN, NaN) --> true
        console.log(+0 === -0) --> true
        Object.is(+0, -0) --> false
    ```
    2. Object.assign(receiver,suplier) 浅拷贝
    ```
        将suplier对象的属性复制到receiver对象（当属性值为对象时，复制其引用，改变原suplier对象）

        <!-- 属性值为非对象 -->
        var object1 = {'name':'cxx', age:'24'}
        var object4 = Object.assign({},object1)
        object4.name = 'dog'
        object1.name -------------------> 'cxx'
        <!-- 属性值为对象 -->
        var object6 = { a: {color : 'red'}}
        var object7 = Object.assign({} , object6)
        object7.a.color = 'green'
        object6.a.color ----------------> 'green'
        <!-- 三个参数 -->
        Object.assign({}, [{ a: 3 }, { b: 4 }, { c: 5 }], {
              "color": 'red'
        })

        Object.assign接受一个接受者以及任意数量的提供者，返回接受者
                             提供者后者会覆盖前者相同的属性值
    ```
    3. 自有属性的枚举顺序（数值类型和字符串类型可排序）

        ***枚举属性时，数字优先升序排列，其次是字符串和符号类型（分别按照添加的顺序排列）***

## 解构
   1. 对象解构
      ```
      Condition 1
        let node = {
            type : '1',
            name : 'func'
        }
        let {type, name} = node
        console.log(type)   1
        console.log(name)   'func'
      ```
      ```
      Condition 2
         let node = {
             type : '1',
             name : 'func'
         }
         let type = '2', name = 'foo';
         ({type, name} = node);//必须加括号，暴露的花括号会被解析成代码块，代码块语句不可以出现在等于号左侧
         console.log(type)   1
         console.log(name)   'func'
      ```
      ```
      Condition 3
          用解构配合var/let/const声明变量时，一定要初始化
          let {type, name};
          -----------wrong--------------
      ```
      ```
      Condition 4
          解构赋值时，未赋值的对象为undefined
          let node = {
              type : '1',
              name : 'func'
          }
          let {type, name, age} = node
          console.log(type)   1
          console.log(name)   'func'
          console.log(age)   undefined
      ```
      ```
      Condition 5
        解构赋值给不同的本地变量名 currentName currentAge 与传统对象字面量相反 值 --> 键
        let node = {
            type : '1',
            name : 'func'
        }
        let {type, name : currentName, age : currentAge = 12} = node
        console.log(currentName)   'func'
        console.log(currentAge)     12
      ```
      ```
      Condition 6
          嵌套对象解构
          let node8 = {
              type2 : '1',
              name : 'func',
              log7 : {
                  line : { a:1, b:2 }
              }
          }
          let { log7: { line: line3 }} = node8
          console.log(line3)            { a:1, b:2 }
      ```
   2. 数组解构
      ```
      Condition 1
          let node = ['red','green','pink']
          let [firstColor,secondColor] = node
          let [,,thirdColor] = node
          console.log(firstColor)           'red'
          console.log(secondColor)          'green'
          console.log(thirdColor)          'pink'
      ```
      ```
      Condition 2
          用解构配合var/let/const声明变量时，一定要初始化
          let [type, name];
          -----------wrong--------------
      ```
      ```
      Condition 3
          默认值同对象解构Condition 4
      ```
      ```
      Condition 4
          let a = 1,b = 2;
          [a, b] = [b, a]
      ```
      ```
      Condition 5
           嵌套数组解构
           let node = ['red',['green','blue'],'pink']
           let [firstColor,[secondColor]] = node
           console.log(secondColor)          'green'
      ```
      ```
      Condition 6
          剩余项
          let node = ['red','green','pink']
          let [...nodeArr] = node
          console.log(nodeArr)          ['red','green','pink']
      ```
   3. 参数解构
        ```
        Condition 1
            function getData(name, {age, grade, sex}) {
                console.log(age)
            }
            getData('cxx',{
                age: 12,
                grade: 2,
                sex: 'female'
            })
            ***默认情况下，调用函数未给参数解构传值会报错***
            getData('cxx')   解决方法 --> Condition 2
        ```
        ```
        Condition 2
            默认值
            function getData(name, {age, grade, sex} = {}) {
                console.log(age)
            }
            getData('cxx')
        ```

## 符号与符号属性
   **[新增基本类型 Symbol](https://juejin.im/entry/58466c6e61ff4b00589b8269)** ( 详细介绍Click here )

            使用全局Symbol函数创建符号值
            let color = Symbol();
            let book = {};
            book[color] = 'red'
            console.log(book[color])        'red'

            Symbol函数可接受一个参数用于描述符号值（描述信息），但不可用来访问，只读或调试
            let color = Symbol('color');

            识别符号值
            let color = Symbol('color');
            console.log(typeof color)       'symbol'

## Set与Map
   1. 创建 Set 并添加项

          创建: new Set()
          添加项: add() 方法
          查看项length: size 属性
          测试某个值是否存在: has()
          移除单个值: delete()
          移除所有值: clear()
          遍历所有值: forEach()
      ```
      Condition 1
            let set = new Set();
            set.add(5);
            set.add("5");
            set.size();         --> 2
            > 不会使用强制类型转换来判断值是否重复
            > Object.is() 方法，来判断两个值是否相等，唯一的例外是 +0 与 -0 在 Set 中被判断为是相
              等的
            > 添加多个对象，它们不会被合并为同一项
            > 重复了，该调用被忽略 （数组去重）
      ```
      ```
      Condition 2
            let set = new Set();
            set.add(5);
            set.add("5");
            console.log(set.has(5)); // true
            console.log(set.has(6)); // false
      ```
      ```
      Condition 3
            forEach() 方法接受三个参数：
                1. Set 中下个位置的值；
                2. 与第一个参数相同的值；
                3. 目标 Set 自身

            let set = new Set([1, 2]);
            set.forEach(function(value, key, ownerSet) {
                console.log(key + " " + value);
                console.log(ownerSet === set);
            });

            echo --> 1 1
                     true
                     2 2
                     true
      ```
      ```
      Condition 4
            Set中forEach内的this对象同数组的forEach
            let set = new Set([1, 2]);
            let processor = {
                output(value) {
                    console.log(value);
                },
                process(dataSet) {
                    dataSet.forEach((value) => this.output(value));
                }
            };
            processor.process(set);
      ```
      ```
      Condition 5
            转换为数组
                let set = new Set([1, 2, 3, 3, 3, 4, 5]),
                array = [...set];
                console.log(array); // [1,2,3,4,5]
            去重函数
                function eliminateDuplicates(items) {
                    return [...new Set(items)];
                }
      ```

   2. 创建 WeakSet

          产生原因:  Set 实例的引用仍然存在，所存储的对象就无法被垃圾回收机制回收，从而无法释放内存
          let set = new Set(),
              key = {};
          set.add(key);
          console.log(set.size); // 1
          key = null;            // 取消原始引用
          console.log(set.size); // 1

          同Set的区别:
          1. 对于 WeakSet 的实例，若调用 add() 方法时传入了非对象的参数，就会抛出错误（
          has() 或 delete() 则会在传入了非对象的参数时返回 false ）；
          2. Weak Set 不可迭代，因此不能被用在 for-of 循环中；
          3. Weak Set 无法暴露出任何迭代器（例如 keys() 与 values() 方法），因此没有任何编
          程手段可用于判断 Weak Set 的内容；
          4. Weak Set 没有 forEach() 方法；
          5. Weak Set 没有 size 属性。

    ```
    Condition 1
        > 不接受基本类型的值
        let key1 = {};
        set = new WeakSet([key1]);
        ------------correct----------------
        let key1 = 1;
        set = new WeakSet([key1]);
        ------------wrong------------------
    ```
    ```
    Condition 2
        > 对象的弱引用
          let set = new WeakSet(),
          key = {};
          // 将对象加入 set
          set.add(key);
          console.log(set.has(key)); // true
          key = null;
          console.log(set.has(key)); // false
    ```
   3. 创建Map

            set() 设置一个键与一个关联的值
            get() 获取键对应的值
            与Set对象共用 size()
                        has()
                        delete()
                        clear()
                        forEach()

        ```
        Condition 1
            let map = new Map();
            map.set("title", "Understanding ES6");
            console.log(map.get("title"));
            获取不存在的键会返回undeifined
        ```
        ```
        Condition 2
            对象可以作为键
            let map = new Map(),
            key2 = {};
            map.set(key2, 42);
            console.log(map.get(key2));  //42
        ```

   4. 创建Weak Map

            原因: 能优化内存使用并规避内存泄漏
            方法: 只有has()和delete()
        ```
        Condition 1
            let map = new WeakMap(),
            element = document.querySelector(".element");
            map.set(element, "Original");
            console.log(map.has(element)); // true
            console.log(map.get(element)); // "Original"
            map.delete(element);
            console.log(map.has(element)); // false
            console.log(map.get(element)); // undefined
        ```
        ```
        Condition 2
            对象的私有属性
            let Person = (function() {
                let privateData = new WeakMap();
                function Person(name) {
                    privateData.set(this, { name: name });
                }
                Person.prototype.getName = function() {
                    return privateData.get(this).name;
                };
                return Person;
            }());
        ```
   > Tips:
        要使用 Weak Map 还是使用正规 Map 时，首要考虑因素在于你是否只想使用对象类
        型的键。如果你打算这么做，那么最好的选择就是 Weak Map 。因为它能确保额外数据在不
        再可用后被销毁，从而能优化内存使用并规避内存泄漏。

## 类 （ 以 class 关键字开始，语法是对象字面量方法简写，方法之间不需要使用逗号）

   > Tips :
        在构造器函数内创建所有可能出现的自有属性，利于代码检查
        1. 类声明不会被提升，这与函数定义不同。类声明的行为与 let 相似，因此在程序的执行
        到达声明处之前，类会存在于暂时性死区内。
        2. 类声明中的所有代码会自动运行在严格模式下，并且也无法退出严格模式。
        3. 类的所有方法都是不可枚举的
        4. 类的所有方法内部都没有 [[Construct]] ，因此使用 new 来调用它们会抛出错误。
        5. 调用类构造器时不使用 new ，会抛出错误。
        6. 试图在类的方法内部重写类名，会抛出错误。

1. 类声明

        class PersonClass {
            // 等价于 PersonType 构造器
            constructor(name) {
                this.name = name;
            }
            // 等价于 PersonType.prototype.sayName
            sayName() {
                console.log(this.name);
            }
        }
        let person = new PersonClass("Nicholas");
        person.sayName(); // 输出 "Nicholas"

        // 直接等价于 PersonClass
        let PersonType = (function() {
            "use strict";
            const PersonType = function(name) {
                // 确认函数被调用时使用了 new
                if (typeof new.target === "undefined") {
                    throw new Error("Constructor must be called with new.");
                }
                this.name = name;
            }
            Object.defineProperty(PersonType.prototype, "sayName", {
                value: function() {
                    // 确认函数被调用时没有使用 new
                    if (typeof new.target !== "undefined") {
                        throw new Error("Method cannot be called with new.");
                    }
                    console.log(this.name);
                },
                enumerable: false,
                writable: true,
                configurable: true
            });
            return PersonType;
        }());

  2. 类表达式 （ 除语法差异，== 类声明）

            Condition 1
            let PersonClass = class {
                // 等价于 PersonType 构造器
                constructor(name) {
                    this.name = name;
                }
                // 等价于 PersonType.prototype.sayName
                sayName() {
                    console.log(this.name);
                }
            };
            let person = new PersonClass("Nicholas");
            person.sayName(); // 输出 "Nicholas"

            Condition 2
            立即调用类构造器
            let person = new class {
                constructor(name) {
                    this.name = name;
                }
                sayName() {
                    console.log(this.name);
                }
            }("Nicholas");
            person.sayName(); // "Nicholas"

  3. 具名类

            let PersonClass = class PersonClass2 {
                >> PersonClass2只能在类的内部使用
                // 等价于 PersonType 构造器
                constructor(name) {
                    this.name = name;
                }
                // 等价于 PersonType.prototype.sayName
                sayName() {
                    console.log(this.name);
                }
            };
            console.log(typeof PersonClass); // "function"
            console.log(typeof PersonClass2); // "undefined"

  4. 静态成员
    > 静态成员不能用实例来访问，你始终需要直接用类自身来访问它们

            class PersonClass {
                // 等价于 PersonType 构造器
                constructor(name) {
                    this.name = name;
                }
                // 等价于 PersonType.prototype.sayName
                sayName() {
                    console.log(this.name);
                }
                // 等价于 PersonType.create
                static create(name) {
                    return new PersonClass(name);
                }
            }
            let person = PersonClass.create("Nicholas");

  5. 派生类 （ 继承了其他类的类）

        * 使用熟悉的 extends 关键字来指定当前类所需要继承的函数
        * 如果派生类指定了构造器，就需要使用 super() ，否则会造成错误。
          若你选择不使用构造器， super() 方法会被自动调用，并会使用创建新实例时提供的所有参数
        * 使用 super() 时需牢记以下几点：
              1. 你只能在派生类中使用 super() 。若尝试在非派生的类（即：没有使用 extends
              关键字的类）或函数中使用它，就会抛出错误。
              2. 在构造器中，你必须在访问 this 之前调用 super() 。由于 super() 负责初始化
              this ，因此试图先访问 this 自然就会造成错误。
              3. 唯一能避免调用 super() 的办法，是从类构造器中返回一个对象。

                class Square extends Rectangle {
                    // 没有构造器
                }
                // 等价于：
                class Square extends Rectangle {
                    constructor(...args) {
                        super(...args);
                    }
                }

## 数组方法

1.  Array.of() 方法创建数组

        let items = Array.of(1, 2);
        console.log(items.length); // 2
        console.log(items[0]); // 1
        console.log(items[1]); // 2

2. Array.from()

    > 参数1: 可迭代对象或者类数组对象(伪数组)

        function translate() {
            return Array.from(arguments);
        }
        let numbers = translate(1, 2, 3);
        console.log(numbers)          [1,2,3]

    > 参数2: 传递一个映射用的函数

        function translate() {
            return Array.from(arguments, (value) => value + 1);
        }
        let numbers = translate(1, 2, 3);
        console.log(numbers); // 2,3,4

    > 参数3: 用于指定 this,映射函数内部的 this 值

        let helper = {
            diff: 1,
            add(value) {
                return value + this.diff;
            }
        };
        function translate() {
            return Array.from(arguments, helper.add, helper);
        }
        let numbers = translate(1, 2, 3);
        console.log(numbers); // 2,3,4

3. find()和findIndex()

       find() 方法会返回匹配的值
       findIndex() 方法则会返回匹配位置的索引
       let numbers = [25, 30, 35, 40, 45];
       console.log(numbers.find(n => n > 33)); // 35
       console.log(numbers.findIndex(n => n > 33)); // 2

## Promise

    Promise 具有三种状态：挂起、已完成、已拒绝。
            then()  允许你绑定完成处理函数与拒绝处理函数
            catch() 只允许你绑定拒绝处理函数。
            race()  任意一个任务被完成时响应 （先完成先响应）
            all()   任务都完成后才会被响应，若被拒绝，立即停止
            多个Promise串联
            let p1 = new Promise(function(resolve, reject) {
                resolve(42);
            });
            let p2 = new Promise(function(resolve, reject) {
                reject(43);
            });
            p1.then(function(value) {
                // 第一个完成处理函数
                console.log(value); // 42
                return p2;
            }).then(function(value) {
                // 第二个完成处理函数
                console.log(value); // 永不被调用
            });

## 模块化封装代码





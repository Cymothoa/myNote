# react

## 必要准备

> 1. **react** 是react核心库，只要使用react就必须要引入
>
>    -下载地址：https://unpkg.com/react@18.0.0/umd/react.development.js
>
> 2. **react-dom** 是react的dom包，使用react开发web应用时必须引入
>
>    -下载地址：https://unpkg.com/react-dom@18.0.0/umd/react-dom.development.jsbabel.min.js
>
> 3. 由于JSX最终需要转换为JS代码执行，所以浏览器并不能正常识别 JSX，所以当我们在浏览器中直接使用JSX时，还必须**引入babel**来完成对代码的编译。
>
>    -babel下载地址：https://unpkg.com/babel-standalone@6/babel.min.js
>
>    tips：
>
>    引入顺序为	babel.min.js -->  react.development.js  -->  react-dom.development.js
>
>    顺序不可弄错！！！

## 认识react

> React:用于构建web与原生交互界面的库

### react和vue的区别（一部分）

#### -偏向

> vue.js => 偏向于html扩展
>
> react.js => 偏向于javascript扩展

#### -引入方法

> vue: 
>
> ​	1.直接引入vue第三方库 
>
> ​	2.vue ui去创建 
>
> ​	3.vue create 项目名 
>
> react: 
>
> ​	1.通过第三方库引入

### 在jsx中将标签渲染到页面里

```html
    <body>
        <div id="root"></div>
        <!-- type="text/babel" 告诉babel库 将jsx转成js -->
        <script type="text/babel">
            // 需求：将标签渲染到页面中
            //1.创建标签 
          const snow = <h1>今天下大雪</h1>;
            // 2.获取渲染位置
          const getRoot = document.getElementById("root");
            // 3.将新标签渲染到页面上
            // ReactDOM.createRoot(指定渲染页面) 
            // render(渲染的内容)
            ReactDOM.createRoot(getRoot).render(snow);
        </script>

    </body>
```

> tips：
>
> 1.react中可以利用 type="text/babel" 将jsx转换为js（实际script中写的是jsx）
>
> 2.在jsx中标签可以自行创建（必须闭合 可以写成<tag/>或者 双标签<tag></tag>的形式）
>
> 3.标签渲染到页面A之前 要先获取A的位置（通过doucument.getElementById等方法 详见js）
>
> 4.渲染 ReactDOM.createRoot(指定渲染页面).render(渲染的内容);

## 数据渲染

> vue 动态渲染 {{}} 模板语法
>
> react 表达式 {} 可以做运算
>
> tips：
>
> react数据渲染与vue形式上的区别就是react只有一对花括号{}

```html
<body>
    <div id="root"></div>
    <script type="text/babel">
        let rain = '雨天';
        let userName = {
            fistName:'火',
            lastName:'锅'
        }

        // const snow = <h3>明天休息,但是有可能{false + 1 + 'hello' + userName.fistName}</h3>;
        // const snow = <h3>明天休息,但是有可能{rain}</h3>;
        function getName(userName) {
            return `${userName.fistName} ${userName.lastName}`
        }
        const snow = <h4>{getName(userName)}</h4>;
        const getRoot = document.querySelector("#root");
        ReactDOM.createRoot(getRoot).render(snow);
    </script>
</body>
```

## 绑定属性

> jsx中两个属性的写法发生了改变：           
>
> for => htmlFor （不是循环那个for）
>
> class => className
>
> tips：
>
> -label中的for的名称：与input框中的id名字相同 就可以实现点击label内容input实现聚焦
>
> -input中 tabIndex属性可以操控tab键下的顺序
>
> -jsx中的注释：{/\* 这里写注释内容 \*/}

```html
    <body>
        <div id="root"></div>
        <script type="text/babel">
            let element = (
                <div>
                    {/*今天天气真好*/}
                    <label htmlFor="same">姓名</label>
                    <input id="same" type="text" placeholder='请输入姓名' tabIndex='1' />
                    <br/>
                    <label htmlFor="age">年龄</label>
                    <input id="age" type="text" placeholder='请输入年龄' tabIndex='3' />
                    <br/>
                    <label htmlFor="address">地址</label>
                    <input id="address" type="text" placeholder='请输入地址' tabIndex='2' />
                    <br/>
                </div>
            )
            let getRoot = document.getElementById("root");
            ReactDOM.createRoot(getRoot).render(element);
        </script>

    </body>
```

## 绑定样式

> 动态渲染样式:
>
> jsx中 style样式是对象Object格式 不能是字符串格式
>
> let newBox = {
>                 width: '500px',
>                 height: '500px',
>                 border: '1px solid #f00',
>                 margin: '0 auto',
>                 display: 'flex',
>                 justifyContent: 'space-between',
>                 alignItem: 'center'
>             }
>
> <div style={newBox}>

```html
<html lang="en">
    <body>
        <div id="root"></div>
        <!-- 
            className:
                className= '类名'
                className = {'类名'}
         -->
        <script type="text/babel">
            // 动态渲染样式
            // jsx中 style样式是对象Object格式 不能是字符串格式
            let newBox = {
                width: '500px',
                height: '500px',
                border: '1px solid #f00',
                margin: '0 auto',
                display: 'flex',
                justifyContent: 'space-between',
                alignItem: 'center'
            }
            let left = {
                width: '200px',
                height: '200px',
                // jsx中动态渲染样式 样式属性若是多单词组成则需要变成驼峰命名法
                backgroundColor: 'purple',
                color: "#fff"
            }
            // let box = <div className={'box'}>我的名字叫图图</div>;
            // 需求：盒子样式： 大盒子居中 小盒子通过弹性盒分别居左居右
            let box = (
                <div style={newBox}>
                    <div style={left}>左侧盒子</div>
                    <div style={{
                        width:'200px',
                        height:'200px',
                        backgroundColor:'#ff0',
                        color:'#f00'
                    }}>右侧盒子</div>
                </div>
            )
            let showPage = document.querySelector("#root");
            ReactDOM.createRoot(showPage).render(box);
        </script>
    </body>
</html>
```

## 事件处理

> 格式：onXXX 驼峰命名法

#### -点击事件 onClick

#### -改变事件 onChange

#### -提交事件 onSubmit

> 例子：

```jsx
        <script type="text/babel">
            function handleClick() {
                console.log("今天天气真好")
            }
            function handleChange(e) {
                console.log("发生更改了",e.target.value)
            }
            function handleSubmit() {
                console.log("提交了")
            }
            let element  = (
                <div>
                    <button onClick={handleClick}>点击按钮</button>
                    {/** <div class="btn" >点击事件</div>*/}
                    <br/>
                    <input type="text" onChange={handleChange} />
                    <form onSubmit={handleSubmit}>
                        <button>提交</button>
                    </form>
                </div>               
            )
            ReactDOM.createRoot(document.querySelector("#root")).render(element)
        </script>
```

### -阻止冒泡事件

> *e.stopPropagation();*

### -阻止默认事件

> *e.preventDefault();*

```jsx
function handleSubmit(e) {
	e.preventDefault();
	console.log("提交了")
}
```

### -this指向

> 方法中 this指向当前标签 

#### -改变this指向的方法

##### 1.call bind apply

> let element = <div onClick={onClick.bind(aaaa)}>这是第二个按钮</div>

```jsx
        <script type="text/babel">
            function onClick(){
                console.log(this)
            }
            function handleClick3(e){
                console.log(e)
                // console.log(id)
            }
    		var aaaa = {name:"My name is Tutu"};
            let element = <div onClick={onClick.bind(aaaa)}>这是第二个按钮</div>
            let element = (
                <div>
                  <p onClick={handleClick1.bind(aaaa)}>事件1</p>             
                </div>
            )
    		<p onClick={handleClick3.bind(null,44,55)}>事件3</p>
            {/* null不占位 */}
            let newPage = ReactDOM.createRoot(document.querySelector("#root"));
            newPage.render(element)
        </script>
```

##### 2.箭头函数 ()=>{}

> *<p onClick={(e)=>{*
>
> ​	*handleClick2(e,3,444,5555)*
>
> *}}>事件2</p>*

```jsx
        <script type="text/babel">
            function handleClick2(e,...user){
                console.log(e.target)
                console.log(...user)
            }
            // 第二种
            let element = (
                <div>
                    {/*套壳*/}
                    <p onClick={(e)=>{
                        handleClick2(e,3,444,5555)
                    }}>事件2</p>
                    {/* 传递多个参数时 接收参数需要解构 */}
                </div>
            )
            let newPage = ReactDOM.createRoot(document.querySelector("#root"));
            newPage.render(element)
        </script>
```

###### -传递多个参数时 接收参数需要结构

##### tips：

> 默认传递事件对象
>
> bind虽然可以改变this指向 但是位置固定并不灵活
>
> 箭头函数 可以套壳比较灵活 

## 组件

> 组件：类组件 函数组件

### 函数组件的创建

> 创建函数组件时：函数名的 首字母要大写
>
> tips：
>
> null undefined boolean Object无法渲染

```jsx
<body>
    <div id="root"></div>
    <script type="text/babel">
        function New() {
          return (
            <div>
                <h3>一会考你俩面试题</h3>
                {[1,2,3,4,5]}
                {null}//无法渲染
                {undefined}
                {'helloWorld'}
                {false}
                {true}
                {13456}
                {/**
                    {{aaa:"哈哈哈"}} 无法渲染 报错
                */}
            </div>
          )
        }
        let element = <New/>
        ReactDOM.createRoot(document.querySelector("#root")).render(element);
    </script>
</body>
```

### 组件通信：props

> 单项数据流 props 
>
> 推荐父级向子级传递 
>
> 只读
>
> - 父级引用子级函数标签<Day name='图图' age={4}></Day>
> - 子级通过props.xxx承接父级的传参<p>我的名字叫{props.name}</p>

```jsx
<body>
    <div id="root"></div>
    <script type="text/babel">
        function Good(props) {
            console.log(props,'父级的内容')
            return (
                <div style={{border:"2px solid #f00",padding:"10px"}}>
                    <p>这是一个父级标签</p>
                    <Day name='图图' age={4}></Day>
                </div>
            )
        }
        function Day(props) {
            console.log(props,'子级的内容')
            return (
                <div style={{border:"2px solid #00f",padding:"10px"}}>
                    <p>这是一个子级标签</p>
                    <p>我的名字叫{props.name}</p>
                    <p>我今年{props.age}岁了</p>
                    <button onClick={()=>{
                        handelClick(props)
                    }}>获取内容</button>
                </div>
            )
        }
        function handelClick(props) {
            console.log(props,'内容')
        }
        let element = <Good/>
        ReactDOM.createRoot(document.querySelector("#root")).render(element);
    </script>
</body>
```

### 类组件的创建

> 格式：
>
> class 类组件名 extends React.Component
>
> 遵从es6规范 可以修改=>state

```jsx
import { Component } from "react";
class Moon extends Component{
    render(){
        return(
            <div>timer</div>
        )
    }
}
export default Moon;
```

```jsx
  <body>
    <div id="root"></div>
    <script type="text/babel">
      // 类组件 遵从es6规范 可以修改=>state
      class Vase extends React.Component {
        render() {
          return (
            <div style={{ border: "2px solid #f00", padding: "10px" }}>
              <p>这是一个父级标签</p>
            </div>
          );
        }
      }
      let element = <Vase/>
      ReactDOM.createRoot(document.querySelector("#root")).render(element);
    </script>
  </body>
```

#### state

> 可以修改数据
>
> 数据更新视图未变
>
> - vue解决方案：Vue.set() this.$set
> - react解决方案: state
>
>           this.setState({
>             count: this.state.count + 1,
>           });

```jsx
  <body>
    <div id="root"></div>
    <script type="text/babel">
      // 类组件 state 可以修改数据
      // 计数器
      class White extends React.Component {
        // 定义初始数值
        state = {
          title: "计数器",
          count: 0,
        };
        // 数据更新视图未变
        // vue解决方案：Vue.set() this.$set
        // react解决方案:
        handleAdd() {
          this.setState({
            count: this.state.count + 1,
          });
          console.log(this.state, "加法");
        }
        handleReduce = () => {
            console.log(this)
          this.setState({
            count: this.state.count - 1,
          });
        };
        render() {
          return (
            <div>
              <h2>{this.state.title}</h2>
              <p>当前数值:{this.state.count}</p>
              <button onClick={this.handleAdd.bind(this)}>+</button>
              <button onClick={this.handleReduce}>-</button>
            </div>
          );
        }
      }
      let element = <White />;
      ReactDOM.createRoot(document.querySelector("#root")).render(element);
    </script>
  </body>
```


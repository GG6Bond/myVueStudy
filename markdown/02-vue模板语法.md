### 1. mustache模板语法

```vue
<body>

    <div id="app"></div>

    <template id="my-app">
        <!-- mustache基本使用 -->
        <h2>{{message}}-{{message}}</h2>
        <!-- 是一个表达式 -->
        <h2>{{num*10}}</h2>
        <h2>{{message.split("").reverse().join(" ")}}</h2>
        <!-- 也可以调用函数 -->
        <h2>{{getReverse()}}</h2>
        <!-- 也可以使用三元运算符 -->
        <h2>{{flag===true? "是":"不是"}}</h2>
        <button @click="change">切换</button>


    </template>

    <script src="../../js/vue.js"></script>

    <script>

        const App = {
            template: '#my-app',
            data() {
                return {
                    message: "hello word",
                    num: 100,
                    flag: false
                }
            },
            methods: {
                getReverse() {
                    return this.message.split(" ").reverse().join("");
                },
                change() {
                    return this.flag = !this.flag;
                }
            }

        }

        Vue.createApp(App).mount('#app');

    </script>

</body>
```



### 2. v-once基本指令

```vue
    <template id="my-app">
        <h2>{{num}}</h2>
        <!-- 下面不会重新渲染 -->
        <h2 v-once>{{num}}</h2>
        <!-- div中的所有子组件都不会重新渲染 -->
        <div v-once>
            <!--  -->
            <!--  -->
            <!--  -->
        </div>

        <button @click="add">+1</button>
    </template>
```



### 3. v-text基本指令

```vue
    <template id="my-app">
        <!-- 以下两种办法等价 -->
        <h2 v-text="message"></h2>
        <h2>{{message}}</h2>
    </template>
```



### 4. v-html基本指令

```vue
    <template id="my-app">
        <!-- 下面这样 只会把message中的东西展示出来 -->
        <div>{{message}}</div>
        <!-- 下面这样 会把html页面解析出来 -->
        <div v-html='message'></div>
    </template>
```



### 5. v-pre基本指令

```vue
    <template id="my-app">
        <h2>{{message}}</h2>
        <!-- 加上v-pre，不会解析mustache，会以最原始的方式显示 -->
        <h2 v-pre>{{message}}</h2>
    </template>
```



## 一 、v-bind的使用

### 6. v-bind的绑定属性

基本使用：

```vue
<body>

    <div id="app"></div>

    <!-- 在vue2中，template模板中只能有一个根元素 -->
    <!-- vue3中允许有多个根元素 -->
    <template id="my-app">
        <!-- 使用v-bind进行动态绑定 -->
        <img v-bind:src="imageUrl" alt="" srcset="">
        <!-- v-bind 提供的一个语法糖，直接用冒号代替一大串 -->
        <a :href="link">百度一下</a>
    </template>

    <script src="../../js/vue.js"></script>

    <script>

        const App = {
            template: '#my-app',
            data() {
                return {
                    imageUrl: " https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png",
                    link: 'https://www.baidu.com'
                }
            },

        }

        Vue.createApp(App).mount('#app');

    </script>

</body>
```



### 7. v-bind绑定class-对象语法

```vue
<template id="my-app">
        <div :class="classNmae">哈哈哈</div>
        <!-- 对象语法：{active,boolen} -->
        <!-- 当后面的值为true时，前面的类会被绑定；否则不会被绑定 -->
        <div :class="{active:flag}">呵呵呵</div>
        <button @click="toggle">切换</button>

        <!-- 也可以有多个键值对 -->
        <div :class="{active:flag,title:true}">呵呵呵</div>

        <!-- 默认的class和动态的class结合-->
        <div class="aaa bbb" :class="{active:flag,title:true}">呵呵呵</div>

        <!-- 也可以将对象放到一个单独的属性中 -->
        <div class="aaa bbb" :class="classObj">呵呵呵</div>


    </template>
```





### 8. v-bind绑定class-数组语法

```vue
    <template id="my-app">
        <!-- 数组语法 -->
        <div :class="['abc',title]">哈哈哈</div>
        <!-- 支持三元运算符 -->
        <div :class="['abc',title,isActive?'active':'']">哈哈哈</div>
        <!-- 允许嵌套对象语法 -->
        <div :class="['abc',title,{active:isActive}]">哈哈哈</div>
    </template>
```



### 9. v-bind绑定style-对象语法

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>

    <div id="app"></div>

    <template id="my-app">
        <!-- 用-连接 -->
        <div :style="{color:finalColor,'font-size':'30px'}">哈哈哈</div>
        <!-- 驼峰式 -->
        <div :style="{color:finalColor,'fontSize':'30px'}">哈哈哈</div>
        <!-- 字符串拼接 -->
        <div :style="{color:finalColor,'font-size':finalFontSize+'px'}">哈哈哈</div>
        <!-- 对象 -->
        <div :style="finalStyleObj">哈哈哈</div>
        <!-- 调用方法 -->
        <div :style="getFinalStyleObj()">哈哈哈</div>
    </template>

    <script src="../../js/vue.js"></script>

    <script>

        const App = {
            template: '#my-app',
            data() {
                return {
                    message: "hello word",
                    finalColor: 'red',
                    finalFontSize: 50,
                    finalStyleObj: {
                        fontSize: '50px',
                        fontWeight: 700,
                        backgroundColor: 'red'
                    }
                }
            },
            methods: {
                getFinalStyleObj() {
                    return {
                        fontSize: '50px',
                        fontWeight: 700,
                        backgroundColor: 'red'
                    }
                }
            }

        }

        Vue.createApp(App).mount('#app');

    </script>
</body>

</html>
```





### 10. v-bind绑定style-数组语法

```vue
    <template id="my-app">
        <!-- 将两个对象的属性合并 -->
        <div :style="[style1Obj,style2Obj]">哈哈哈</div>
    </template>
```



```vue
    <script>

        const App = {
            template: '#my-app',
            data() {
                return {
                    style1Obj: {
                        color: 'red',
                        fontSize: '50px'
                    },
                    style2Obj: {
                        textDecoration: "underline"
                    }
                }
            },

        }

        Vue.createApp(App).mount('#app');

    </script>
```



### 11. v-bind动态绑定属性名称

```vue
<body>

    <div id="app"></div>

    <template id="my-app">
        <div :[name]="value">哈哈哈</div>
    </template>

    <script src="../../js/vue.js"></script>

    <script>

        const App = {
            template: '#my-app',
            data() {
                return {
                    name: "aaa",
                    value: 'kkk'
                }
            },

        }

        Vue.createApp(App).mount('#app');

    </script>

</body>

```

### 12. v-bind属性直接绑定一个对象

```vue
    <template id="my-app">
        <!-- 将info的全部属性给div -->
        <div v-bind="info">哈哈哈</div>
    </template>
```



## 二、 v-on的使用

### 1. v-on的基本使用

```js
    <template id="my-app">
        <button @click="btn1Click">btn1</button>
        <!-- 完整写法如下所示 -->
        <button v-on:click="btn2Click">btn2</button>
        <div v-on:mousemove="mouseMove">哈哈哈</div>
        <!-- 绑定一个表达式 -->
        <button @click="num++">{{num}}</button>
        <!-- 绑定一个对象 -->
        <div class="area" v-on="{click:btn1Click,mousemove:mouseMove}"></div>
    </template>
```



### 2. v-on的参数传递

```js
<body>

    <div id="app"></div>

    <template id="my-app">
        <!-- 默认传入event对象,可以在方法中获取 -->
        <!-- 如果不需要额外的参数,方法后面的()可以不加 -->
        <button @click="btn1Click">btn1</button>
        <!-- $event可以获取到事件发生的事件对象 -->
        <button @click="btn2Click($event,'lpz',18)">btn2</button>
    </template>

    <script src="../../js/vue.js"></script>

    <script>

        const App = {
            template: '#my-app',
            data() {
                return {
                    message: "hello word"
                }
            },
            methods: {
                btn1Click(event) {
                    console.log(event);
                },
                btn2Click(event, name, age) {
                    console.log(event, name, age);
                }
            }

        }

        Vue.createApp(App).mount('#app');

    </script>

</body>
```



### 3. v-on的修饰符

```vue
<body>

    <div id="app"></div>

    <template id="my-app">
        <!-- 会有冒泡 -->
        <div @click="divClick">
            <button @click="btnClick">btn1</button>
        </div>
        <p></p>
        <!-- 去除冒泡 -->
        <div @click="divClick">
            <button @click.stop="btnClick">btn1</button>
        </div>

        <!-- {.keyAlise}仅当事件是从特定键触发时才触发回调 -->
        <input type="text" @keyup.enter="enterKeyUp">
    </template>

    <script src="../../js/vue.js"></script>

    <script>

        const App = {
            template: '#my-app',
            data() {
                return {
                    message: "hello word"
                }
            },
            methods: {
                btnClick() {
                    console.log('btn clicked');
                },
                divClick() {
                    console.log('div clicked');
                },
                // 获取输入的数据,按下回车显示
                enterKeyUp(event) {
                    console.log('enter up', event.target.value);
                }
            }

        }

        Vue.createApp(App).mount('#app');

    </script>

</body>
```


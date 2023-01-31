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


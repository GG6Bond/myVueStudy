### 1. 引入

### 2. 快速上手
```html
<body>

<div id="app"></div>

<script src="../js/vue.js"></script>
<script>
    Vue.createApp({
        template: '<h2>你好啊</h2>'
    }).mount("#app");

</script>
</body>

```



### 3. 计数器案例

```html
<body>
<!--用原生JavaScript实现-->

<h2 id="text">0</h2>
<button id="add">+1</button>
<button id="sub">-1</button>

<script>
    let text = document.querySelector('#text');
    const addBtn = document.querySelector('#add');
    const subBtn = document.querySelector('#sub');

    addBtn.addEventListener("click",()=>{
        text.innerHTML = Number(text.innerHTML)+1;
        console.log(text.innerHTML);
    });

    subBtn.addEventListener("click",()=>{
        text.innerHTML = Number(text.innerHTML)-1;
        console.log(text.innerHTML);
    })


</script>
```





```vue
<!--使用vue实现-->
<div id="app">0</div>

<script src="../js/vue.js"></script>
<script>
    Vue.createApp({
        template: `
          <div>
          <h2>{{ mes }}</h2>
          <h2>{{ num }}</h2>
          <button @click='add'>+1</button>
          <button @click='sub'>-1</button>
          </div>
        `,
        data: function () {
            return {
                mes: 'Hello World',
                num: 100
            }
        },
        methods: {
            add() {
                this.num++;
                console.log('点击了+1');
            },
            sub() {
                this.num--;
                console.log('点击了-1');
            }
        }
        
    }).mount('#app');
</script>

</body>
```



### 4. 声明式编程vs命令式编程





### 5. template,data,methods属性

```vue
Vue.createApp({
    // temeplate 属性： 表示的是vue需要帮助我们渲染的模板信息
    // 里面有很多html标签，这些标签会替换掉我们挂载到的innerHTML
    template: `
      <div>
      <h2>{{ mes }}</h2>
      <h2>{{ num }}</h2>
      <button @click='add'>+1</button>
      <button @click='sub'>-1</button>
      </div>
    `,
    // data属性是传入一个函数，并且该函数需要返回一个对象
    data: function () {
        return {
            mes: 'Hello World',
            num: 100
        }
    },
    // 定义各种方法
    // 内部不能使用箭头函数
    methods: {
        add() {
            this.num++;
            console.log('点击了+1');
        },
        sub() {
            this.num--;
            console.log('点击了-1');
        }
    }

}).mount('#app');
```



### 6. template的两种写法


### 前言
>这文章主要介绍了，组件的基础原理。 由于刚刚接触组件，先不把它写成.vue的文件。各位像我一样的新人，一起学习，一起加油啊！
### 组件（带有名字的Vue实例）

- 模块化
- 复用，重用

### 组件作用范围

1. 全局 (Vue.componet())
2. 局部

```js
Vue.componet(id,{});
// id 为组件的名字
// {} 为组件的配置项
```

### 组件的属性 data必须为 function且返回对象？??-- 深层次
```js
data(){
    return {
        // 为组件编写数据   
    }
}
```
1. 组件复用，每个实例都将有一份返回对象的独立拷贝

### 组件的内容只能有一个根元素, template算不算？
```html
<template>
    <div class="root-element">
        <!-- write your component code -->
        <div>
        </div>
    </div>
</template>
```

### 使用组件的步骤
1. 定义组件
2. 在使用的地方注册该组件（你总得告诉人家吧！！）
3. 用就是了！（自定义元素的来用）


### 组件的命名方式: kebab-case 就是一个单词加一个横线然后再加个单词这样的组成(单词之间用横线隔开)
**浏览器解析不支持大写字母，解析的时候全部会转为小写**
```js
像这样的会不会？
my-counter
my-list
your-list-item
```
> kebab-case: 单词中间横线合开
> PascalCase: 单词首字母大写
**别玩花样，就用横线隔开那种命名方式！**
**建议：没有内容的组件作为闭合元素来使用**
```js
<my-button />
```
```js
vue.js:634 [Vue warn]: Unknown custom element: <button-counter> - did you register the component correctly? For recursive components, make sure to provide the "name" option.

(found in <Root>)
```
### 对于 components来说，每个属性的名字就是自定义元素的名字
### Vue.extend()函数u？？？？？



### 组件的通信
1. 使用props向子组件传递数据
> - 组件当做自定义元素使用 => 借用元素的属性来通信()。
>
> - 在**组件**中定义props数组： <code style="padding:10px 10px; background:#000;color:#fff;">props:['postTitle']</code>
>
> - 要想传递多个值就定义多个prop, 或者传递对象将要传递的值封装咋对象中
```js
<body>
    <div id="app">
        <post-item post-title="Vue.js很强！" />
    </div>
    <script src="../node_modules/vue/dist/vue.js"></script>
    <script>
        // 定义全局组件
        Vue.component('post-item', {
            // 使用props属性数组来接受父组件传递的值
            props: ['postTitle'],
            template: `<h3>{{postTitle}}</h3>`
        });
        const app = new Vue({
            el: "#app"
        });
    </script>
</body>
```
### 实际业务开发中，子组件通常是以对象来接受数据
```html
<body>
    <div id="app">
        <post-list />
    </div>
    <script src="../node_modules/vue/dist/vue.js"></script>
    <script>
        Vue.component('post-item', {
            props: ['post'],
            template: `
                <div>
                    <h3>{{post.title}}</h3>
                    <p>{{post.author}}</p>
                    <p>{{post.content}}</p>
                </div>
            `
        });
        Vue.component('post-list', {
            data() {
                return {
                    // 将多个值封装在对象post中
                    post: {
                        author: "刘博文",
                        title: "Vue.js深入浅出",
                        content: "这本书很牛逼！"
                    }
                }
            },
            template: `<div><post-item :post='post'/></div>`
        })
        const app = new Vue({
            el: "#app",
        });
    </script>
</body>
```

### props传递值的特点
1. 单向传递数据，只能向被引用的一方传递数据。
2. 数组和对象传递引用，子组件去更改数据会影响父组件的状态


### 组件的验证机制（就是可以来验证传递过来的数据是否符合要求,而这个要求可以你来定义！）
```js
Vue.component({

});
```

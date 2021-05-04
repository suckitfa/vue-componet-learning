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
1. 使用props想子组件传递数据
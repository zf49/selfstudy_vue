

# Vue_Self Study

## 绑定+判断
### v-bind
   现在数据和DOM已经被建立了关联，所有的东西都是响应式的。我们在控制台操作对象的属性，界面可以实时更新。
  
   我们可以使用v-bind来绑定元素属性！
  
  ```html
     <!DOCTYPE html>
     <html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml">
     <head>
         <meta charset="UTF-8">
         <title>Title</title>
     
     </head>
     <body>
     
     <div id="app1">
         <h1> {{message}}</h1>
     </div>
     
     
     <div id="app2">
         <span v-bind:title="message">
             悬停在此处
         </span>
     </div>
     
 
     
     <!--    导入vue.js-->
     <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
     <script>
         var vm1 = new Vue({
            el : "#app1",
             data: {
                 message: "hello , vue!"
             }
         });
         var vm2 = new Vue({
             el : "#app2",
             data: {
                 message: "v-bind"
             }
         });
     </script>
     
     
     
     </body>
     </html>
```       

 ## v-if v-for
   if见demo2
   ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
          <h1 v-if="type==='a'">a</h1>
          <h1 v-else-if="type==='b'">b</h1>
          <h1 v-else >啥也不是</h1>
  
  </div>
  
  
  <!--    导入vue.js-->
  <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
  <script>
      var vm = new Vue({
          el : "#app",
          data: {
              type:'a',
  
          }
      });
  </script>
  
  </body>
  </html>
```
for 见demo3
```html
        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <title>Title</title>
        </head>
        <body>
        <div id="app">
        
                <li v-for="item in items">
                    {{item.message}}
                </li>
        
            <li v-for="(item,index) in items">
                
                {{item.message}}----{{index}}
        <!--  item--每个元素
              index--每个下角标-->
            </li>
        
            
        </div>
        
        
        <!--    导入vue.js-->
        <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
        <script>
            var vm = new Vue({
                el : "#app",
                data: {
                   items: [
                       {message: 'chris study vue'},
                       {message: 'chris study front-end'},
                       {message: 'chris study back-end'}
                   ]
                }
            });
        </script>
        
        </body>
        </html>
```

## 事件
 在tag中使用v-on进行事件绑定，vue所有方法均定义在methods中
 ```html
     <!DOCTYPE html>
     <html lang="en">
     <head>
         <meta charset="UTF-8">
         <title>Title</title>
     </head>
     <body>
     
     <div id="app">
         <button v-on:click="sayHi">click</button>
     </div>
     
     
     
     <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
     <script>
         var vm = new Vue({
             el : "#app",
             data: {
                 message: 'I get new coding skill'
             } ,
             methods: {   // 方法要定义在vue method对象中
                         // 
                sayHi: function () {
                    alert(this.message);
                }
             }
         });
     </script>
     </body>
     </html>
```

## 双向绑定   v-model 
   
  
```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
      gender：
      <input type="radio" name="sex" value="male" v-model="chris" > 男
      <input type="radio" name="sex" value="female" v-model="chris"> 女
  
     <h1>选中了谁： {{chris}}</h1>
      
  
      输入<input type="text" v-model="message">同步 输出{{message}}
      <br/>
      <br/>
      <br/>
      <hr>
      <div>
          <select v-model="chris">
              <option value="" disabled>--please select--</option>
              <option>a</option>
              <option>b</option>
              <option>c</option>
              <option>d</option>
          </select>
          <h1>下来菜单默认选中：{{chris}}</h1>
      </div>
  </div>
  
  <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
  <script>
      var vm = new Vue({
          el : "#app",
          data: {
              message:'',
             chris:''
          } ,
          methods: {
          }
      });   


  </script>
  </body>
  </html>
``` 
1. 什么是双向绑定
​ Vue.js是一个MVVM框架，即数据双向绑定,即当数据发生变化的时候,视图也就发生变化，当视图发生变化的时候，数据也会跟着同步变化。这也算是Vue.js的精髓之处了。

​ 值得注意的是，我们所说的数据双向绑定，一定是对于UI控件来说的，非UI控件不会涉及到数据双向绑定。单向数据绑定是使用状态管理工具的前提。如果我们使用vuex，那么数据流也是单项的，这时就会和双向数据绑定有冲突。

2. 为什么要实现数据的双向绑定
在Vue.js 中，如果使用vuex ，实际上数据还是单向的，之所以说是数据双向绑定，这是用的UI控件来说，对于我们处理表单，Vue.js的双向数据绑定用起来就特别舒服了。即两者并不互斥，在全局性数据流使用单项,方便跟踪;局部性数据流使用双向，简单易操作。

3. 在表单中使用双向数据绑定
你可以用v-model指令在表单 ```<input>```、```<textarea>``` 及```<select>``` 元素上创建双向数据绑定。它会根据控件类型自动选取正确的方法来更新元素。尽管有些神奇，但v-model本质上不过是语法糖。它负责监听户的输入事件以更新数据，并对一些极端场景进行一些特殊处理。

​ 注意：```v-model```会忽略所有元素的value、checked、selected特性的初始值而总是将Vue实例的数据作为数据来源，你应该通过JavaScript在组件的data选项中声明。


## VUE组件
```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
  
      <chris v-for="item in items" v-bind:chris="item"></chris>
  
  </div>
  
  
  <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
  <script>
  
      Vue.component("chris",{
          props:['chris'],
            template: '<li>{{chris}}</li>'
      });
  
      var vm = new Vue({
          el : "#app",
          data:{
              items:["java","linux","front-end"]
          }
      });
  </script>
  </body>
  </html>
```

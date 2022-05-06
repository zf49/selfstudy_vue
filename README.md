# Vue_Self Study


## v-bind
  ​ 现在数据和DOM已经被建立了关联，所有的东西都是响应式的。我们在控制台操作对象的属性，界面可以实时更新。
  
  ​ 我们可以使用v-bind来绑定元素属性！
  
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

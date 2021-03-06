# AJAX页面自动加载、懒加载

## 自动加载

### 原理

将更多需要显示的内容或分页通过DOM来动态生成，内容由AJAX请求。

### 效果

页面向下滚的过程中，不断自动加载新的页面内容。

### 实现方式

1. 声明一个AJAX请求，请求对应页面url的json格式数据；
2. 将请求到的json数据进行处理，使用for循环对HTML页面进行DOM操作，动态生成图片及内容；
3. 判断触发条件，通过BOM调取用户在使用中的页面下滚距离，到预定位置则触发加载；
4. 优化
   - 判断数据是否有下一页，如果没有，不再请求；
   - 判断数据是否正在请求，如果正在请求，不要重复请求（针对网速慢的情况）；

### 预览地址
https://greygao.github.io/AJAX-autoLoad-demo/index1.html




## 懒加载

### 原理

在自动加载概念的基础上，将每页请求好的图片内容分批次显示在页面上。

### 效果

当图片进入用户浏览的范围内后，才会加载图片内容，否则只预加载一个loading图片。这样可能最大程度的节省流量。

### 实现方式

1. 在上述自动加载的代码基础上进行优化，先将DOM生成的图片的src设为一个预加载的loading图片，再预留一个data属性保存图片的真实地址；
2. 判断图片进入了用户的页面范围，则获取到对应的图片并将src内容替换为data中的地址，删除data属性；
3. 这样当用户滚动到对应的位置才会开始请求出现在页面里的图片内容。

### 预览地址 (可使用限制网速来模拟效果)

https://greygao.github.io/AJAX-autoLoad-demo/index2.html

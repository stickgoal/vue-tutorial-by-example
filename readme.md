# Vue入门课程

1. Vue概述 [官网介绍](https://cn.vuejs.org/v2/guide/index.html)

   - 要明确的是Vue是个构建用户界面的框架，重点是在用户界面和交互层。所以基本上围绕如何组织和渲染页面，比如解决如何实现数据加载，页面间跳转，用户界面组件复用等等。

   - Vue跟jQuery、Bootstrap之类的我们称为库或者脚手架用户界面框架大有不同，Vue是用正儿八经的js语言开发的一个完整框架，本身是一个复杂的系统，使用方式不是简单地引入或者添加class，而是使用Vue提供的各种机制来创建加载渲染各个页面组件。Vue不是你可以使用的工具，而是为你提供了一套开发平台。

   - Vue将页面看作由一个又一个**组件**组合而成的。所以Vue提供了完善的组件机制，可以将界面拆分为独立组件，组件内部管理自己的状态，便于复用和管理。当然，由此也带来了组件的挂载销毁等生命周期管理，组件嵌套后的通信之类的问题，Vue也提供了相应的机制。

     ![components](.\res\components.png)

   - Vue受MVVM模式启发，将数据和视图拆分并由Vue本身负责监听数据的变动而自动渲染页面，进而实现了业务逻辑和页面逻辑的拆分。因此，Vue提供了一整套模板语法来实现。

   - 进一步发展的过程中，Vue的技术生态很自然（而且快速的）往不同的方向延展

     - [规模化](https://cn.vuejs.org/v2/guide/routing.html)
       - 单页面应用的趋势,导致Vue需要在各个组件之间提供统一的路由支持，即如何从一个组件跳转到另一个组件的方式。官方提供了vue-router
       - 随着项目越来越大，应用复杂度也成倍提高，数据状态管理愈发复杂，Vue提供了vuex实现统一的状态管理
       - Vue的组件开发模式完全改变以往的开发方式，但是也带来了一些问题，用户打开一个单页面应用需要加载各种资源花费很长时间，加之客户端渲染对搜索引擎不友好，因此引入服务端渲染。
     - 工程化
       - Vue背后站了一群各种各样的JS库，种类繁多，依赖繁琐，加上Vue本身定位而需要处理各种用户资源，因此Vue提供了vue-cli以支持创建vue项目，又提供了vue-loader来加载vue解析专有的组件等工具。为了方便开发也提供dev-tools等。
       - Vue本身基于js生态，因此依赖管理工具npm(yarn)，打包工具webpack自然也是必不可少

   - Vue是渐进式的，这是vue区别于React主要特性。也就意味着，我们可以将vue当做纯粹的模板或者UI框架来使用

2. [基础实例](01-basic/helloworld.html)

   - [vue实例](https://cn.vuejs.org/v2/guide/instance.html)
   - Vue 实例的[API](https://cn.vuejs.org/v2/api/#%E9%80%89%E9%A1%B9-%E6%95%B0%E6%8D%AE)  主要有 
     - el :  挂载到的DOM元素
     - data  :  数据
     - methods ： 方法
     - template ： 组件模板

3. [模板语法](02-template/template.html)（类似jsp+jstl 或者thymeleaf之类的模板语法）

   - 插值   :   取值或者代值

   - 指令  ： 读取数据，据此来渲染模板

     - 常用

       - v-if/v-else 条件判断
       - v-for          循环
       - v-on           根据数据动态绑定事件 v-on:click     =缩写=>  @click
       - v-bind       根据数据动态绑定HTML属性 v-bind:href   =缩写=>  :href
       - v-show

     - 修饰符，添加一些额外功能 v-on:submit.prevent="onSubmit"  其中的.prevent能够防止默认行为

       - `.stop`  阻止事件继续传播 

       - `.prevent `  提交事件不再重载页面

       - `.capture`   添加事件监听器时使用事件捕获模式,即元素自身触发的事件先在此处理，然后才交由内部元素进行处理

       - `.self`   只当在 event.target 是当前元素自身时触发处理函数,即事件不是从内部元素触发的

       - `.once`

       - `.passive`

       - 按键修饰符 

         ```html
         <!-- 只有在 `key` 是 `Enter` 时调用 `vm.submit()` -->
         <input v-on:keyup.enter="submit">
         ```

   - 计算属性

4. 组件

   - 组件基础
   - 单文件组件	

5. vue实战
  - npm / yarn
  - webpack
  - vue-router及SPA
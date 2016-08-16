#vue学习笔记
-Vue.js（读音 /vjuː/, 类似于 view）是一个构建数据驱动的 web 界面的库。Vue.js 的目标是通过尽可能简单的 API 实现响应的数据绑定和组合的视图组件。
-Vue.js结合了react和angularjs的优势，是一个轻量级框架,采用MVVM模式
-参考网站：http://cn.vuejs.org/guide/index.html

##1.Vue实例
-[vue生命周期示意图](http://cn.vuejs.org/images/lifecycle.png)

##2.双向数据绑定
-单词处理插值：{{*msg}}
-输出真的HTML字符串：{{{}}}
-有些指令可以在其名称后面带有一个参数，中间放一个冒号隔开：eg:v-on:click="doSomethingj"
-缩写：v-bind:href 缩写为    :href   v-on:click  缩写为  @click

##3.Class和Style绑定
-尽量不要将v-bind和Mustache混用
-v-bind用于class和style是，表达式的结果类型除了字符串之外，还可以说是对象和数组
-当v-bind：style使用需要厂商前缀的CSS属性时，Vue.js会自动侦测并添加相应的前缀

##4.条件渲染 v-if v-show v-else
-v-if支持template语法，v-show不支持，v-else不可单独使用
-v-if 有更高的切换消耗而 v-show 有更高的初始渲染消耗。
   因此，如果需要频繁切换 v-show 较好，如果在运行时条件不大可能改变 v-if 较好。
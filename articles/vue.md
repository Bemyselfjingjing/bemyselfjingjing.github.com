#vue学习笔记
- Vue.js（读音 /vjuː/, 类似于 view）是一个构建数据驱动的 web 界面的库。Vue.js 的目标是通过尽可能简单的 API 实现响应的数据绑定和组合的视图组件。
- Vue.js结合了react和angularjs的优势，是一个轻量级框架,采用MVVM模式
- 参考网站：http://cn.vuejs.org/guide/index.html

##1.Vue实例

- [vue生命周期示意图](http://cn.vuejs.org/images/lifecycle.png)

##2.双向数据绑定
- 单词处理插值：{{*msg}}
- 输出真的HTML字符串：{{{}}}
- 有些指令可以在其名称后面带有一个参数，中间放一个冒号隔开：eg:v-on:click="doSomethingj"
- 缩写：v-bind:href 缩写为    :href   v-on:click  缩写为  @click

##3.Class和Style绑定
- 尽量不要将v-bind和Mustache混用
- v-bind用于class和style是，表达式的结果类型除了字符串之外，还可以说是对象和数组
- 当v-bind：style使用需要厂商前缀的CSS属性时，Vue.js会自动侦测并添加相应的前缀

##4.条件渲染 v-if v-show v-else
<<<<<<< HEAD
- v-if支持template语法，v-show不支持，v-else不可单独使用
- v-if 有更高的切换消耗而 v-show 有更高的初始渲染消耗。
   因此，如果需要频繁切换 v-show 较好，如果在运行时条件不大可能改变 v-if 较好。
   
##5.方法与事件处理器
- 在事件处理器中经常需要调用 event.preventDefault()(该方法将通知 Web 浏览器不要执行与事件关联的默认动作（如果存在这样的动作）。
-- 例如，如果 type 属性是 "submit"，在事件传播的任意阶段可以调用任意的事件句柄，通过调用该方法，可以阻止提交表单。注意，如果 Event 对象的 cancelable 属性是 fasle，那么就没有默认动作，或者不能阻止默认动作。无论哪种情况，调用该方法都没有作用。)
-- 或 event.stopPropagation()(不再派发事件。终止事件在传播过程的捕获、目标处理或起泡阶段进一步传播。调用该方法后，该节点上处理该事件的处理程序将被调用，事件不再被分派到其他节点。)。
- Vue.js 为 v-on 提供两个 事件修饰符：.prevent 与 .stop,1.0.16 添加了两个额外的修饰符：.capture和.self
- 使用v-on,当一个 ViewModel 被销毁时，所有的事件处理器都会自动被删除。你无须担心如何自己清理它们。

##6.表单控件绑定
- 参数属性 debounce 设置一个最小的延时，在每次敲击之后延时同步输入框的值与数据。如果每次更新都要进行高耗操作（例如在输入提示中 Ajax 请求），它较为有用。
-- debounce 参数不会延迟 input 事件：它延迟“写入”底层数据。因此在使用 debounce 时应当用 vm.$watch() 响应数据的变化。若想延迟 DOM 事件，应当使用 debounce 过滤器。

##7.过渡 
-- 通过 Vue.js 的过渡系统，可以在元素从 DOM 中插入或移除时自动应用过渡效果。Vue.js 会在适当的时机为你触发 CSS 过渡或动画，你也可以提供相应的 JavaScript 钩子函数在过渡过程中执行自定义的 DOM 操作。
- (1)为了应用过渡效果，需要在目标元素上使用 transition 特性
- (2)类名的添加和切换取决于 transition 特性的值。如果 transition 特性没有值，类名默认是 .v-transition, .v-enter 和 .v-leave。
- (3)当多个元素一起过渡时，Vue.js会批量处理，只强制一次布局
- (4)当只使用 JavaScript 过渡时，enter 和 leave 钩子需要调用 done 回调，否则它们将被同步调用，过渡将立即结束。
-- 为 JavaScript 过渡显式声明 css: false 是个好主意，Vue.js 将跳过 CSS 检测。这样也会阻止无意间让 CSS 规则干扰过渡。

##8.组件 ---组件（Component）是 Vue.js 最强大的功能之一
- 每个 Vue 实例都是一个事件触发器
-- 使用 $on() 监听事件；
-- 使用 $emit() 在它上面触发事件；
-- 使用 $dispatch() 派发事件，事件沿着父链冒泡；
-- 使用 $broadcast() 广播事件，事件向下传导给所有的后代。

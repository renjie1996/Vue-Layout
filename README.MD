
![banner][1]

Vue-Layout
==

基于UI组件的Vue可视化布局、生成.vue代码的工具。https://jaweii.github.io/Vue-Layout/dist/  

----------

演示
--

使用

![demo1][2]

效果


![demo2][3]

上图的后台布局例子，你可以进入这个页面访问其布局：https://jaweii.github.io/Vue-Layout/dist/#/share/5993d3b05c497d0057c6f2da  
也可以进入这个页面体验其布局效果：https://jaweii.github.io/Vue-Layout/dist/#/preview/pc/5993d3b05c497d0057c6f2da

如何拓展UI可视化组件？
==

 1. 如果是新增的UI，先在main.js中引入，然后在`./src/components/template`路径下，创建对应的UI的文件夹（如果没有）；
 2. copy已有的类似组件。假设你要拓展mint-ui的导航栏组件，你可以直接复制muse-ui的导航栏（`./src/components/template/Muse-UI/App Bar.js`）到Mint-UI目录中，修改文件名为Header.js、以及修改其中的部分代码即可：  
 ![此处输入图片的描述][4]

  主要就是修改红框部分的内容，attributes和slots参照UI文档的API，template改成对应组件的标签名，当然每个UI、每个组件都不同，有的只需要稍作修改，有的则需要改很多。
每次属性视图上触发的属性更新，都会让handle函数执行一遍，并传入新的属性、嵌套以及组件的信息，然后返回拼凑的新模板，重新挂载到预览视图。**属性可视化编辑的功能就是这么实现的。**
 
 3. Header.js完成后，在`./src/components/template/Mint-UI/index.js`中引入，
![此处输入图片的描述][5]  
图中的键名的写法，是因为有的键名包含空格，比如"App Bar"。为了直观和便于维护，命名都是与UI官方文档相同。
 
 4. 再将添加的Header组件添加到组件列表视图即可。

> 
                <li draggable="true" @dragstart="dragStart" data-name="Header">
                    <mt-header fixed title="Header"></mt-header>
                </li>


li标签包裹的元素，就是显示在组件列表视图的元素，其中li的data-name的值必须与上一步骤中保存的键名相同。

到此，一个mint-ui导航栏组件的可视化就拓展完成了。

完结，撒花。

 


最后
--

项目没有使用eslint，使用的格式化插件：https://packagecontrol.io/packages/HTML-CSS-JS%20Prettify  
（默认配置，仅在配置项的格式化文件类型中增加了.vue格式）。

欢迎道友们一起来让Vue-Layout支持跟多UI~

  [1]: https://raw.githubusercontent.com/jaweii/Vue-Layout/master/static/banner.JPG
  [2]: https://raw.githubusercontent.com/jaweii/Vue-Layout/master/static/demo1.gif
  [3]: https://raw.githubusercontent.com/jaweii/Vue-Layout/master/static/demo2.gif

  [4]: https://raw.githubusercontent.com/jaweii/Vue-Layout/master/docs/images/App%20Bar1.png
  [5]:  https://raw.githubusercontent.com/jaweii/Vue-Layout/master/docs/images/Header%201.png
 
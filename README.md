# cjj
#一个仿jq 的通用框架
使用原生js编写了一个仿JQ框架Cjj.js，使用全局变量C调用,可使用链式编程<br>
框架内容：<br>
###0.基本框架<br>
#####1.去除空格  
C.trim(字符串,l(左)/r(右)/默认为左右都去除)，返回处理后的字符串
#####2. 随机数
C.random(最小数，最大数),返回随机数
#####3.ajax
C.ajax({type:get/post/jsonp,url:地址,data:{},dateType:返回数据类型默认str/json,fn：回调函数/jsonp函数名}),返回this
C.load(url:地址，fn:回调函数)，返回this
#####4.获取地址参数
C.getserch(),无参数则返回一个对象{参数名：参数值}，有参数则直接返回该参数对应的值
#####5.拷贝对象
C.copy(目标对象)，返回目标对象副本
###1.数据类型检测框架<br>
C.type(obj),返回数据了类型eg:[object Object]   <br>
C.isnum(obj),判断是否是数值型，返回true/false  <br>
isBool,isStr,isUn,isNull,isObj,isArray,isDom
###2.选择框架<br>
#####1.基本选择器
C("选择器","父级",flag)，父级默认为document,flag:是否使用h5选择器默认关闭，querySelectorAll    <br>
.parent(slect) 参数：选择器，没有参数直接返回父一级  <br>
.child(slect)   参数：选择器，没有参数直接返所有子一级元素，<br>
    暂不支持迭代查询字元素 可使用C(选择器,父级)代替 <br>
.firstChild()  第一个子元素  <br>
.lastChild()   最后一个子元素 <br>
.next()   下一个元素 <br>
.prev()   上一个元素 <br>
.sibl(slect)   参数：选择器，没有参数返回所有兄弟元素 <br>
.get(num)  C()转化dom元素  <br>
.leng()    返回当前C()获取到的dom个数   <br>
###3.css属性框架<br>
.css(k,v)属性名，属性值，一个参数为获取    <br>
.attr(k,v)属性名，属性值，一个参数为获取  <br>
.html(h)无参数则获取当前元素html，有参数则设置html    <br>
.txt(h)无参数则获取当前元素text，有参数则设置text    <br>
.val(v)无参数则获取当前元素value，有参数则设置value   <br>
   设置/添加/移除/判断class
.setClass(class)/.addClass(class)/.remClass(class)/.hasClass(class) 
.show  显示元素  <br>
.hide   隐藏元素 <br>
.toggle  显隐切换  <br>
.testCss(prop)  判断是否支持目标属性  <br>
###4.文档框架<br>
C.windowH/C.windowW 返回当前浏览器内容宽高
C.scrollTop/scrollLeft  返回document滚动的上左距离
C.getSelectText 返回用户选择的文本
以下属性请使用原生语法，更简单
offsetWidth/Height/Left/Top/Parent <br>
window.scrreen.width/height/X/Y/ <br>
clientWidth/Height/X/Y/ <br>
###5.动画框架<br>
.animate(targent:{},time10,step:10,avg:false,infi:false,start,fn:fun})  <br>
targent:{属性名：属性值}，要做动画的属性，透明度请使用0-100 <br>
time:10，动画每一步执行事件，定时器时间，为单位，毫秒数 默认10 <br>
avg:false，是否做匀速运动，默认减速/缓动 <br>
infi:false，是否循环动画，默认不循环 <br>
start:{属性名：属性值}，开启循环运动，则需要传入动画初始值 <br>
fn,动画执行完毕时候的回调函数<br>
.stop(flag) //flag：true 动画立即执行完毕，flase 动画暂停：默认flase <br>
.star//重启动画，仅在暂停后可以使用   <br>
###6.事件框架<br>
.on(type,fn,flag),事件绑定(事件，函数，冒泡方式)<br>
.un(type,fn)，事件解绑定(事件，函数)<br>
.click(fn,flag)，(函数，冒泡方式)<br>
.mEnter(fn,flag)，(函数，冒泡方式）<br>
.mLeave(fn,flag)，(函数，冒泡方式）<br>
.hover(overfn,outfn,flag)，(鼠标进入函数，鼠标移出函数，冒泡方式<br>
.drag({box:,x:,y:}),box:拖拽对象,x,y方向是否可动，默认xy都可以拖动<br>
C.event(event),事件对象 <br>
C.target(event),事件目标    <br>
C.prevDef(event),阻止默认行为 <br>
C.stopProp(event),阻止冒泡  <br>
###7.cookie框架<br>
C.setCookie({name:,vales:,days:,path:})
C.getCookie(d)
C.delCookie({name:,path:}),path 默认为'/'
###8.数据绑定框架<br>
C.tempStr(str,data);使用#{k} ，data可以是对象也可以是字符串
.bindHtml(item,data),   给目标对象绑定html，item数据模版，data数据
####/**
#### * @描述: cjj通用框架
#### * @作者: chenjiujiu
#### * @创建日期: 2018/4/13
#### */
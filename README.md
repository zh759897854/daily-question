# 问题汇总
### 1. 动态添加元素，用attr绑定click事件，当append到页面后绑定的click事件会自执行，暂时没找到原因
### 解决方案：只能通过on事件去绑定click事件
***
### 2. outerHTML会返回包括自身在内的所有节点
***
### 3. html标签里面的role属性是语意增强的意思，比如\<div role='button'>button\</div> 意思是这个div现在作为一个按钮button 辅助识别工具就会自动识别为button
***
### 4. 拼接字符串路面不能再传对象，否则接受到的参数打印出来会是'[object,object]'
***
### 5. xmpp登录流程[这里](https://www.jianshu.com/p/2b0de683cce9)
***
### 6. 作用域链问题： 当在for循环里面执行函数，当调取变量时总会掉取到最后一次执行的变量，因为在你循环过程中变量是变化的但是函数没执行，也没添加闭包，所以当函数执行时找到的是最后一次的变量。
> ### 解决方案:1.可以用将变量存到固定值里面（重新赋予新变量）；2.直接执行函数
***
### 7. 正则匹配头尾 reg=/^a.*b&/  a开头b结尾的跑匹配项   匹配包含类的reg=/a.*b/
>> runoo+b，可以匹配 runoob、runooob、runoooooob 等，+ 号代表前面的字符必须至少出现一次（1次或多次）。

>> runoo*b，可以匹配 runob、runoob、runoooooob 等，* 号代表字符可以不出现，也可以出现一次或者多次（0次、或1次、或多次）。

>> colou?r 可以匹配 color 或者 colour，? 问号代表前面的字符最多只可以出现一次（0次、或1次）。
***
### 8. 通过call或apply方法调用函数，this指向方法调用的第一个参数。
var obj = {name:'test'};
function foo(){
    console.log(this);
}
foo.call(obj);//输出obj
foo.apply(obj);//输出obj
***
### 9. \<meta name="renderer" content="webkit|ie-comp|ie-stand">强行设置360浏览器为急速模式

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

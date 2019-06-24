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
***
### 10. vue项目中引用文件 @ 的作用是在你引入模块时，可以使用 @ 代替 /src 目录，避免书写麻烦又易错的相对路径。
***
### 11. vue使用from提交形式上传文件的时候只能用get，而且需要在上传参数里面添加属性
                let config = {
                    headers: {
                        'Content-Type': 'multipart/form-data'
                    }
                };
                Axios.post(that.uploadSingleURL, params, config).then(function (res) {} })
***
### 12. axios取消请求 
                import request from '../utils/request'  // 配置过的Axios 对象
                import axios from 'axios' 

                export function getLatenessDetailSize(params, that) { 
                    return request({
                        url: '/api/v1/behaviour/latenessDetailSize', 
                        method: 'post',
                        params: params,
                        cancelToken: new axios.CancelToken(function executor(c) { // 设置 cancel token
                            that.source = c;
                        })
                    })
                }
                #### 具体业务逻辑中
                import { getLatenessDetail } from "../api";
                export default {
                        data() {
                            return {
                                tableData: [],
                                total: 0,
                                page: 1,
                                loadTable: false,
                                params: { },
                                source: null
                            }
                        },
                        methods: {
                            cancelQuest() {
                                if (typeof this.source === 'function') {
                                    this.source('终止请求'); //取消请求
                                }
                            },
                            getTableData(val) {
                                this.cancelQuest() // 请求发送前调用
                                this.page = val
                                this.loadTable = true
                                getLatenessDetail(this.params, (val - 1) * 10, this)
                                    .then(
                                        res => {
                                            this.loadTable = false
                                            this.tableData = res.data
                                        }
                                )
                        }
                }
***
### 13. vue项目中，require文件到main.js后，在组件引入时还需要去import，无需再实例化
***
### 14.vue引入后为什么有的需要use有的不需要？比如axios可以直接使用 不需要vue.sue 那是因为在插件封装时有的插件没有install这一步。 转载至[vue.use源码解读](https://segmentfault.com/a/1190000012296163)

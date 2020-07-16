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
***
### 15. vue数组变异，导致页面数据不更新
***
### 16. @key.enter.native
***
### 17. 使用route跳转本页时页面是不会刷新的，需要请求数据时需要watch route变化然后去请求数据达到刷新效果
***
### 18. vue中加载图片失败显示默认图片 <img :src="logoSrc"  @error="defaultImgs()"> 亲测有效

### 19.new RegExp(curCookie.key.toString(),'g') 当里面包含特殊字符会报错
### 20.$.parents('ele') 获取到的知识dom 需要转为jq对象
### 21.replace(x , string)
### 22.数组插入特定位置数据可以用 splice(index, 0, 'xxx')
### 23.将this.CliEngine = require(this.basicPath + "lib/cli-engine"); 更改为 this.CliEngine = require(this.basicPath + "lib/cli-engine").CLIEngine;
### 24.webstrom 激活码
### 25.netstat -aon|findstr "8080"， 找到占用端口号的PID 查询完基本就是node taskkill /f /t /im node.exe 直接杀死
### 26.computed 属性被mounted的setAttrbulite('style')覆盖  解决方式是全部在mounted 里面设置
### 27.当vue的watch监听一组对象，对象某个属性值发生变化但是并未触发watch的检测，这时候需要添加deep: true 属性进行深度监听
### 29
### 28.git拉取远程分支更新失败 git branch --set-upstream-to origin/master
### 29.问题：Failed to execute 'appendChild' on 'Node': parameter 1 is not of type 'Node'

    原因：appendChild的参数为node节点，导致这样的问题说明当前的参数不是node，有可能是字符串。

    这时dom是字符串

    解决方法：
    var dom=document.createElement('p');
    dom.className='book';
    dom.innerHTML='hello world';
    document.body.appendChild(dom);
    此时dom为node。

    如果添加的元素是字符串，使用document.createTextNode()创建节点。

    var dom=document.createTextNode('hello world');

***
### 30.window.open 跳转时带有本地前缀， 补全地址 http:// https：//
### 31. 数组获得重复数据
        function GetRepeatFwxmmc(ary1){
        var ary = ary1.sort(function(a,b) {
            return a - b
        });//数组排序
        var cffwxmsAry = new Array();
        //所有重复元素添加进新数组内
        for(var i=0;i<ary.length;i++){
            if (ary[i]==ary[i+1]){
                cffwxmsAry.push(ary[i]);
            }
        }
        var result = [], isRepeated;

        //对重复元素数组进行元素去重
        for (var k = 0; k < cffwxmsAry.length; k++) {
            isRepeated = false;
            for (var j = 0;j < result.length; j++) {
                if (cffwxmsAry[k] == result[j]) {
                    isRepeated = true; break;
                }
            }
            if (!isRepeated) {
                result.push(cffwxmsAry[k]);
            }
        }
        return result;
    }
    
### 32. uni.createSelectorQuery().select('#board')
### 33. uniapp 组件接收属性必须是严格模式  否则属性设置会失效  
### 34. uniApp 组件多次传参导致对象里的方法丢失 父子组件通信去调用   
### 35. [zrender](https://ecomfe.github.io/zrender-doc/public/api.html#zrendergroupsilent)
### 36.getCanvasImg() {
                let canvas = document.querySelector("#zrender-canvas canvas");
                if (canvas) {
                    let strDataURI = canvas.toDataURL("image/jpeg");
                    let a = document.createElement("a");
                    a.download = 'canvasImg';　　//下载的文件名，
                    a.href =strDataURI;
                    document.body.appendChild(a);
                    a.click();
                    a.remove();
                }
            } canvas 保存为图片
### 37. uniapp 弹窗在ios平台穿透导致body滑动， 直接替换为view-scroll 然后添加阻止默认事件就可以了
### 38. vue对象检测属性值变了但是view没刷新 证明添加的属性没有set get 属性 用this.$set(obj, key, value) 的形式就可以了

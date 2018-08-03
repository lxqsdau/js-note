# js-note
js相关

## 事件循环
先执行宏任务：包括整体代码script setTimeout setInterval
再执行微任务：Promise.then process.nextTick

Promise 是同步执行，then是异步微任务
发现setTimeout是宏任务，放在队列中，
宏任务执行完，发现有微任务，执行微任务，到此本轮事件循环结束

下一次事件循环，开始执行宏任务，发现setTimeout 到期了，则执行

## window.open('/test.html') 自带跟路径，打开新页面

## 正则
var reg=/cat/g;
var str='this a cat,this a dog'; 
document.write(reg.test(s)); 
document.write(reg.test(str)); 
按道理两次打印出来都应该是true,true,而最终结果为true,false。
此时我们需要注意啦，在我们定义的正则表达式中后面加上了搜索的方式，g表示全文查找。而且在正则表达式内部有一个lastIndex来记录匹配的位置，第一次调用test()后，那么lastIndex就不再等于0，而是10，当下次在调用该方法的时候，字符串的匹配会从lastIndex位置进行匹配，故最终返回false.所以不要随意添加g.
遇到此种情况后的解决方法：
1.去除g;
2.在第二次使用前，设置reg.lastIndex=0即可。

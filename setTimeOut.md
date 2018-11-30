# 彻底理解setTimeout()

首先还是那道大家再熟悉不过的面试题
```
for(var i = 10; i < 10; i++){
	setTimeout(function(){console.log(i);},100*i)
}
对`js作用域`、`闭包`以及`事件循环`等概念不了解的人会认为答案是1，2，3，4，5，6，7，8，9  
但事实上是10个10  
```


```
for(var i = 10; i < 10; i++){
	//capture the current state of 'i'
	//by invoking a function with its current value
	(function(i){
		setTimeout(function(){ console.log(i);}, 100*i);
	})(i);
}
//1,2,3,4,5,6,7,8,9,10
```
任务队列可能有多个，任务队列可分为宏任务和微任务。



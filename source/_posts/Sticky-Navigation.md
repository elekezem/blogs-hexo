---
title: Sticky Navigation
date: 2016-02-20 16:59:17
tags:
---
# Sticky Navigation

###### *"这也是一个markdown的测试"* 

### 为什么要改造Hype 3？

1. Hype 3可以让只会做PPT的新手快速搭建一个交互原型或者静态站点，当然也可以让我这样的杂食性前端用Hype来做PPT.
2. Hype竟然是一个优秀的项目文件管理系统，用他来做项目，几乎不用考虑备份与打包.
3. 做原型或者静态站快！快！快！

### Sticky Navigation

放一个图来解释

![](http://gangdesign.io/wp-content/uploads/2016/01/507x400_sticky_nav.gif)


###### *Sticky Navigation* 

Sticky Navigation这样的应用在原型制作与响应式页面应用中很常见，

但是，Hype 3却没有这样的相关设置，除非你是制作的Animation，向上图那样.
##### （关于Animation的黑科技放在后面的章节）

**所以我们就很有必要来改造Hype 3**


### Hype Function
可能是Hype知道自己先天的不足，所以制作了详尽的API，可以让用户自定义JS Function

![](http://gangdesign.io/wp-content/uploads/2016/01/Screenshot-2016-01-22-06.40.21.png)
 

```js
//Function sticky()
// element - DOMHTMLElement that triggered this function being called
// event - event that triggered this function being called
function sticky(hypeDocument, element, event) {
lastPos = {
y1 : 0,
y2 : 0
}

el = hypeDocument.getElementById('menu');
sPos = el.getBoundingClientRect().top;

window.onscroll=function(){
wY = window.pageYOffset || (document.body.scrollTop || document.documentElement.scrollTop) ;
lastPos.y1 = lastPos.y2; lastPos.y2 = wY;

if(wY >= sPos){
el.style.top = '0px';
el.setAttribute("class","sticky");
}
if (lastPos.y2 < lastPos.y1 && wY <= sPos){
el.style.top = sPos + 'px';
el.setAttribute("class","");
}

};	

}
```

#### 函数简析



![](http://gangdesign.io/wp-content/uploads/2016/01/Screenshot-2016-01-22-07.15.53.png)
1. 函数名称为sticky()
2. 需要给相应的对象定义元素名称，我将导航栏定义为menu
3. el.style.top为运动终止绝对坐标



### **效果如下**

![](http://gangdesign.io/wp-content/uploads/2016/01/sticky.gif)


#数组
## 创建数组
```javascirpt
var daysOfWeek = new Array(); //传统的新建数组
var daysOfWeek = new Array(7); //定长数组，通常不这么干
var daysOfWeek = new Array('Sunday', 'Monday', 'Tuesday', 'Wednesday','Thursday', 'Friday', 'Saturday'); //附带内容的新建
var daysOfWeek = ['Sunday', 'Monday', 'Tuesday', 'Wednesday','Thursday', 'Friday', 'Saturday'];//附带内容的新建
var daysOfWeek = [];//最常用
```
## 添加和删除元素
```javascript
var nums = [1,2,3,4,5,6,7];
numbers.push(11);//尾部添加
numbers.push(12, 13);//值得一提的是 js里面的数组 可以往里面push任何数据类型
numbers.unshift(20);
numbers.unshift(20,666);//从头部添加
```


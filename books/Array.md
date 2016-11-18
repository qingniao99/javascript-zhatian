# 数组
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
var numbers = [1,2,3,4,5,6,7];
numbers.push(11);//尾部添加
numbers.push(12, 13);//值得一提的是 js里面的数组 可以往里面push任何数据类型
numbers.unshift(20);
numbers.unshift(20,666);//从头部添加

numbers.pop();//尾部删除
numbers.shift();//t头部删除
/*删除方法和添加方法还有一点不同，删除每次只删除一个，添加一次可以添加多个*/
```
## 任意位置上删除或添加元素
```javascript
var numbers = [1,2,3,4,5,6,7]
numbers.splice(2,3);//[1,2,6,7]
numbers.splice(2,0,34,5);//[1,2,3,34,5,4,5,6,7]

//splice方法接收的第一个参数，表示想要删除或插入的元素的索引值。第二个参数是删除元素的个数（这个例子里，我们的目的不是删除元素，所以传入0）。第三个参数往后，就是要添加到数组里的值（元素2、3、4）。输出会发现值又变成了从-3到12。
```
## 二维和多维数组
```javascript
//javascript不支持矩阵，所以通常用一维数组套数组这种多层嵌套的方式去模拟。
var averageTemp = [];
averageTemp[0] = [72,75,79,79,81,81];
averageTemp[1] = [81,79,75,75,73,72];

//假如我们要创建一个3×3的矩阵，每一格里包含矩阵的i（行）、j（列）及z（深度）之和：

var matrix3x3x3 = [];
for (var i=0; i<3; i++){
    matrix3x3x3[i] = [];
    for (var j=0; j<3; j++){
        matrix3x3x3[i][j] = [];
        for (var z=0; z<3; z++){
            matrix3x3x3[i][j][z] = i+j+z;
        }
    }
}
//log

for (var i=0; i<matrix3x3x3.length; i++){
    for (var j=0; j<matrix3x3x3[i].length; j++){
        for (var z=0; z<matrix3x3x3[i][j].length; z++){
            console.log(matrix3x3x3[i][j][z]);
        }
    }
}

```
## 数组常用方法
```javascript
数组合并concat
concat方法可以向一个数组传递数组、对象或是元素。数组会按照该方法传入的参数顺序连接指定数组。
var a = [1,2,3]
var b={a:1}
var c=9
var d=[9,8,7]
a.concat(b)
[1,2,3,{a:1}]
a.concat(c)
[1, 2, 3, 9]
a.concat(d)
[1, 2, 3, 9, 8, 7]
===============================
迭代器函数
var numbers=[1,2,3,1,2,3];
function func(a){
    return (a%2==0);
}
every方法会迭代数组中的每个元素，直到返回false
和every的行为类似，不过some方法会迭代数组的每个元素，直到函数返回true;
numbers.every(func);
numbers.some(func);
如果要迭代整个数组，可以用forEach方法。它和使用for循环的结果相同
numbers.forEach(function(a){
    console.log(a);
});
JavaScript还有两个会返回新数组的遍历方法。map和filter：
调用map遍历结束后，会返回由调用函数return结果组成的新数组
var a=[8,9,10];
var s = a.map(function(x){
    return x-1;
});
s的值是[7,8,9];
filter方法。它返回的新数组由使函数返回true的元素组成：
var a=[8,9,10];
var s = a.filter(function(x){
    return (x%2==0);
});
s的值是[8,10];
reduce方法接收一个函数作为参数，这个函数有四个参数：previousValue、currentValue、index和array。这个函数会返回一个将被叠加到累加器的值，reduce方法停止执行后会返回这个累加器。
var a=[8,"9",10];
var s = a.reduce(function(previous, current, index){console.log(previous+":"+current)
    return previous+current;
});
8:9
89:10
s的值是27
```
## 搜索和排序
```javascript
reverse()方法可以将数组反序。
var a=[1,2,3]
a.reverse();//[3,2,1]
sort()方法可以将数组排序。sort方法在对数组做排序时，把元素默认成字符串进行相互比较。
var a=[1,2,3,14,15,22]
a.sort();//[1, 14, 15, 2, 22, 3]
sort()方法可以接受一个比较函数作为参数。
function compare(a, b) {
    if (a < b) {
        return -1;//a比b小
    }
    if (a > b) {
        return 1;//a比b大
    }
    return 0;
}
a.sort(compare);//[1, 2, 3, 14, 15, 22]

var friends = [
    {name: 'John', age: 30},
    {name: 'Ana', age: 20},
    {name: 'Chris', age: 25}
];

function comparePerson(a, b){
    if (a.age < b.age){
        return -1
    }
    if (a.age > b.age){
        return 1
    }
    return 0;
}

console.log(friends.sort(comparePerson));
//Ana(20), Chris(25), John(30);
var names =['Ana', 'ana', 'john', 'John'];
console.log(names.sort());
//["Ana", "John", "ana", "john"]
JavaScript在做字符比较的时候，是根据字符对应的ASCII值来比较的。例如，A、J、a、j对应的ASCII值分别是65、75、97、106。
虽然在字母表里a是最靠前的，但J的ASCII值比a的小，所以排在a前面。

假如对带有重音符号的字符做排序的话，我们可以用localCompare来实现：
var names2 = ['Maève', 'Maeve'];
console.log(names2.sort(function(a, b){
    return a.localeCompare(b);
}));
//["Maeve", "Maève"]

搜索有两个方法：indexOf方法返回与参数匹配的第一个元素的索引，lastIndexOf返回与参数匹配的最后一个元素的索引。不存在的时候会返回-1.

join()方法接受一个符号，默认为“，”会将数组拼接成字符串。
```




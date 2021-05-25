# 数据结构与算法 JavaScript



## 书本组织结构

- 这本书的编程风格
- 常见数据结构：数组，数组是js原生的数据类型
- 列表
- 栈
- 讨论队列，处理数据之前，先把数据按顺序排成一列的模拟
- 链表 对列表的修改。 当程序需要插入和删除多个元素时，使用链表非常搞笑
- 实现和使用字典，字典是数据存储为键值对的数据结构
- 散列表、散列算法
- 集合，当数据集不允许有重复元素出现时，使用集合是一个很好的选择。
- 二叉树、儿叉查找树---存储有序元素的极佳选择
- 图和图的算法、图用来表示计算机网络节点或者地图上的城市等数据。
- 算法、查找算法：线性查找和二分查找
- 完结：动态规划和贪心算法

## 使用代码示例

> https://github.com/oreillymedia/data_structures_and_algorithms_using_javascript





## 第一章 js的编程环境和模型

### 随录笔记



- BST 二叉查找树

- js中，函数的参数传递方式都是按值传递，没有按引用传递的参数。但是js中有保存引用的对象，数组。代码2中是按引用传递的.

- 变量作用域 --- 指一个变量在程序中哪些地方可以访问。js变量作用域被定义为函数作用域。 -- 代码3

- 递归 ---  代码4 

  ```
  当一个函数被递归调用时，在递归没有完成时，函数的计算结果暂时被挂起。为了说明这个过程。
  5 * factorial(4) 
  5 * 4 * factorial(3) 
  5 * 4 * 3 * factorial(2) 
  5 * 4 * 3 * 2 * factorial(1) 
  5 * 4 * 3 * 2 * 1 
  5 * 4 * 3 * 2 
  5 * 4 * 6 
  5 * 24 
  120
  ```

- 本书的数据结构都被实现为对象 ， js提供多种方式来创建和使用对象。

### 出现过的代码

1. 阶乘

   ```js
   function factorial(number) {
       var product = 1;
       for(var i = number; i >= 1; --i) {
           product *= i;
       }
       return product;
   }
   
   factorial(4) // 24
   ```

2. 

   ```js
   function curve(arr, amount) {
       for(var i = 0; i< arr.length; ++i) {
           arr[i] += amount;
       }
   }
   
   var grades = [77, 73, 74, 81, 90];
   curve(grades, 5); // undefined
   console.log(curve(grades, 5)); // undefined
   ```

3. 滥用全局变量的恶果

   ```js
   function showScope() {
       scope = "local";
       return scope;
   }
   
   scope = "global";
   scope; // "global"
   showScope(); // "local"
   scope; // "local"
   ```

4. 递归

   ```js
   function factorial(number) {
       if(number == 1) {
           return number;
       } else {
           return number * factorial(number - 1);
       }
   }
   factorial(5);
   ```

   





##  第二章 数组

> 数组是常见的数据结构
>
> 探索js数组的工作原理、以及它的使用场合。



### 随录笔记

- 数组的标准定义: 一个存储元素的线性集合(collection)，元素通过索引来任意存取， 索引index是数字，用来计算元素之间存储位置的偏移量。

- 在js中的数组，被称作为对象，特殊的js对象。内部归类为数组。

- 创建数组 --- []

  ```
  var numbers = [];
  
  还可以调用Array的构造函数创建数组
  var numbers = new Array();
  
  可以为构造函数创建数组
  var numbers = new Array(1, 2, 3, 4, 5);
  ```

- 数组中的元素不必是同一种数据类型

  ```
  var objects = [1, "Joe", true, null];
  ```

- 判断一个对象是否数组 `Array.isArray()`

  ```js
  var numbers = 3;
  var arr = [7, 4, 1776];
  Array.isArray(numbers); // false
  Array.isArray(arr); // true
  ```

- 字符串生成数组

  字符串对象的split()可以生成数组，常见的分隔符。如代码1

- 对数组的整体性操作 浅拷贝和深拷贝

  浅复制：新数组依然指向原来的数组

  深复制：将原数组中的而每一个元素都复制一份到新数组中

- 存取函数

  js提供一组用来访问数组元素的函数，叫做存取函数，这些函数返回目标数组的某种变体。

- 查找元素

  indexOf() 最常用的存取函数之一，用来查找传进来的参数在目标数组中是否存在。存在返回该元素的索引，不在返回-1 代码4 



​		indexOf()函数总是返回第一个与参数相同的元素的索引

​		lastIndexOf()函数返回相同元素中最后一个元素的索引，如果没找到相同元素，则返回-1。





### 出现过的代码

1. split()

   ```js
   var sentence = "the quick brown fox jumped over the lazy dog";
   var words = sentence.split(" ");
   for(var i = 0; i < words.length; ++i) {
       console.log("word" + i + ": " + words[i]);
   }
   ```

2. 浅拷贝

   ```js
   // 浅拷贝
   var nums = [];
   for(var i = 0; i < 100; ++i) {
       nums[i] = i + 1;
   }
   var samenums = nums;
   nums[0] = 400;
   console.log(samenums[0]); // 400
   ```

3. 深拷贝

   ```js
   function copy(arr1, arr2) { 
       for(var i = 0; i < arr1.length; ++i) { 				arr2[i] = arr1[i]; 
       } 
   }
   
   var nums = []; 
   for(var i = 0; i < 100; ++i) { 
       nums[i] = i+1; 
   }
   var samenums = []; 
   copy(nums, samenums); 
   nums[0] = 400; 
   console.log(samenums[0]); // 显示 1
   ```

4. indexOf()

   ```JS
   var names = ["David", "Cynthia", "Raymond", "Clayton", "Jennifer"];
   var name = "Raymond";
   var position = names.indexOf(name);
   if(position >= 0) {
   	console.log("Found" + name + " at position " + position);
   } else {
       console.log(name +"not found in array.")
   }
   ```

   

   
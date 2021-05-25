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

   

   


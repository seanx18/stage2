### 第三阶段，再次进行一人中文，一人英文的翻译练习。

- 这3个阶段可反复进行。

中文：然后在那个叫feature的分支上做些修改，这就是面试的开始。

英文：<font color="#ff0000">And then</font> make these changes in that feature branch. That was the start of the interview. （注意视频里这句有个语法错误，正确的应该是And then we made some changes in that feature branch. 这种情况在口语中很常见）。

中文：然后他问了我三个技术问题。第一个问题是编写一个函数，输入一个整数数组，返回数组中所有偶数的和。

英文：And then he asked me three technical questions. So the first one was to <font color="#ff0000">write a function that takes in an array of integers and returns</font> the sum of all even numbers in the array.

中文：典型的编程问题，基本上就是做了两个函数，一个是辅助函数。

英文：Classical code problem, basically, just made two functions, one would be the helper function.

中文：第二个问题是编写一个函数，将一个整数数组按升序排序。他说这是最难的，是大多数人最挣扎的。

英文：Second question was to write a function<font color="#ff0000"> to sort an array of integers in ascending order</font>. That one, he said was the most difficult one that people struggle with the most.

中文：对我来说似乎没那么糟糕，但我实际上觉得第三个更难。

英文：It didn't seem that bad to me, <font color="#ff0000">but I actually found the third one harder</font>.

中文：第三个是编写一个函数，将一个对象数组转换成一个单一对象，其中键是对象的ID，值是对象本身。

英文：The third one was to write a function <font color="#ff0000">that</font> turns an array of objects into a single object where the keys are the IDs of the object, and the values are the objects （o是重要） themselves.

中文：所以输入是一个包含多个对象的数组。每个对象都有一个ID和名字，ID是一个数字，名字就是名字。

英文：<font color="#ff0000">So the input is like an array with multiple objects in the array</font>. Each object has an ID and name, the ID being a number and the name being a name.

---
### Q & A
**Q1: What does the == operator do when comparing variables of different types?**

  
A: When the == operator is used to compare two variables of different types, JavaScript performs type coercion, converting the variables to the same type before making the comparison.

**Q2: How does the == (double equal sign) operator handle null and undefined comparisons?  **

A: When comparing null and undefined, the == **(double equal sign)** operator considers them equal, returning true.

**Q3: What happens when comparing a string with a number using the == operator?  **

A: If a string is compared with a number, JavaScript converts the string to a number and then compares the values.

**Q4: How does the == operator handle comparisons involving booleans?  **

A: If either operand is a boolean, JavaScript converts the boolean to a number (true to 1, false to 0) before making the comparison.

**Q5: What is the rule when comparing an object with a string, number, or symbol?  **

A: If one operand is an object and the other is a string, number, or symbol, JavaScript attempts to convert the object to a primitive value (using the object's toString or valueOf methods) for comparison.

---

### == 操作符的强制类型转换规则？

What are the rules for type coercion of the == operator?

对于 `==` 来说，如果对比双方的类型**不一样**，就会进行**类型转换**。假如对比 `x` 和 `y` 是否相同，就会进行如下判断流程：

For the == operator,if the types of the two operands being compared are different, the type conversion is performed. If you compare whether x and y are the same, the following judgment process will be performed:

1. 首先会判断两者类型是否**相同**，相同的话就比较两者的大小；
 First, it will determine whether the two types are the same, and compare the size of the two if they are the same;
 
2. 类型不相同的话，就会进行类型转换；
If the types are not the same, type conversion will be performed;

3. 会先判断是否在对比 `null` 和 `undefined`，是的话就会返回 `true`
It will first determine whether it is comparing null and undefined, and if it is, it will return true

4. 判断两者类型是否为 `string` 和 `number`，是的话就会将字符串转换为 `number`
Check if the types of both are string and number, if so, the string will be converted to number.

```
1 == '1'
      ↓
1 ==  1
```

5. 判断其中一方是否为 `boolean`，是的话就会把 `boolean` 转为 `number` 再进行判断
To determine whether one of the parties is a boolean, if so, it will change the boolean to number and then make a judgment
```
'1' == true
        ↓
'1' ==  1
        ↓
 1  ==  1
```


6. 判断其中一方是否为 `object` 且另一方为 `string`、`number` 或者 `symbol`，是的话就会把 `object` 转为原始类型再进行判断
Determine if one of the elements is an object and the other is a string, number, or symbol. If so, the object will be converted to its primitive type before the comparison.

```
'1' == { name: 'js' }
        ↓
'1' == '[object Object]'
```

其流程图如下：

The flow chart is as follows:
![[Pasted image 20241211120548.png]]
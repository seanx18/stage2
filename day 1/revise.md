
> [!NOTE] 搭配
> ace your interview  
A complex react application  
Improve/optimize the performance  
The difference between  A and B
Frameworks or libraries  
What measures do you take  
Manage and track  
Version management  
Stay updated with  
  

> [!NOTE] Vocabulary
> 
immutable: can not be changed  
compiler 编译器  
interpreter 解释器  
a priority queue  
be specified by size  
allocate / allocation 分配  
be reclaimed by the garbage collection mechanism  
Arbitrary precision 任意精度


---
数组转对象 ...
```
const arr = [1,2,3]
const obj = {...arr} 

```
js性能追踪 performance
```
let start = performance.now();
let sum = 0;
for (let i = 0; i < 100000; i++) {
  sum += 1;
}
let end = performance.now();
console.log(start);
console.log(end);

```
合并对象 ...
```
console.log(Object.assign(obj1, obj2))
or
const combinObj = { ...obj1, ...obj2 }
```
求幂运算 **
```
console.log(Math.pow(2, 10));

console.log(2 ** 10); // 输出1024
```

浮点数取整 也就是使用`~`, `>>`, `<<`, `>>>`, `|`这些位运算符来实现取整
```
console.log(~~6.95); // 6 
console.log(6.95 >> 0); // 6 
console.log(6.95 << 0); // 6 
console.log(6.95 | 0); // 6 
// >>>不可对负数取整 
console.log(6.95 >>> 0); // 6
```
截断数组
```
let array = [0, 1, 2, 3, 4, 5]; 
array.length = 3;
Output: [0, 1, 2];

arr.slice(0, 3)
```
数组最后一项
```
let arr = [0, 1, 2, 3, 4, 5]; 
const last = arr[arr.length - 1];
const last = arr.slice(-1)[0];
```
拷贝数组 复制数组
```
const arr = [1, 2, 3, 4, 5]; 
const copyArr = arr.slice();
const copyArr = [...arr]
const copyArr = new Array(...arr)
const copyArr = arr.concat();
```
`Object.freeze()` 可以用于冻结对象, 提高性能, 屏蔽对象的 setter, getter 方法
[此处为语雀卡片，点击链接查看](https://www.yuque.com/docs/220813377#VpcmL)

Document link：[https://bigfrontend.dev/problem/improve-a-function](https://bigfrontend.dev/problem/improve-a-function)

```javascript
// Given an input of array,
// which is made of items with >= 3 properties
let items = [
  {color: 'red', type: 'tv', age: 18},
  {color: 'silver', type: 'phone', age: 20},
  {color: 'blue', type: 'book', age: 17}
]
// an exclude array made of key value pair
const excludes = [
  {k: 'color', v: 'silver'},
  {k: 'type', v: 'tv'},
  ...
]
function excludeItems(items, excludes) {
  excludes.forEach( pair => {
    items = items.filter(item => item[pair.k] === item[pair.v])
  })

  return items
}
```

:::color5

1. <font style="color:rgb(51, 51, 51);">What does this function </font>`<font style="color:rgb(51, 51, 51);">excludeItems</font>`<font style="color:rgb(51, 51, 51);"> do?</font>
2. <font style="color:rgb(51, 51, 51);">Is this function working as expected ?</font>
3. <font style="color:rgb(51, 51, 51);">What is the time complexity of this function?</font>
4. <font style="color:rgb(51, 51, 51);">How would you optimize it ?</font>

:::

<h3 id="jkcD4">Function Behavior Analysis</h3>
```javascript
function excludeItems(items, excludes) { 
  excludes.forEach(pair => { 
    items = items.filter(item => item[pair.k] === item[pair.v])
  })
  return items;
}
```

<h4 id="Luxwg">What does this function do?</h4>
The function is **intended** to exclude items from `items` that match any `key:value` pair in `excludes`. However, **it actually retains** only the items that **match all** the specified key-value pairs, which is the **opposite** of the intended behavior.

<h4 id="DESc7">Is the function working as expected?</h4>
**No.**

- The name `excludeItems` and the structure of the `excludes` array imply we should **remove** any item that matches **any** of the key-value pairs in `excludes`.
- But this function **keeps only** those items that match **all** key-value pairs due to repeated `filter()` with `===` condition (logical AND behavior across filters).

<h4 id="dVFXU">❗ Example:</h4>
```javascript
items = [
  {color: 'red', type: 'tv', age: 18}, 
  {color: 'silver', type: 'phone', age: 20},
  {color: 'blue', type: 'book', age: 17}
];

excludes = [
{k: 'color', v: 'silver'},
{k: 'type', v: 'tv'}
];

````

Expected behavior: remove any item with color `silver` OR type `tv`.

Current behavior: keeps only items where `color === 'silver'` **AND** `type === 'tv'` — none in this case → `[]`.

---

<h3 id="q9O1l">Time Complexity</h3>
For `n = items.length`, `m = excludes.length`:

```javascript
excludes.forEach -> O(m)
  items.filter -> O(n)
````

➡️ **Total: O(m × n)**  
Each `filter()` scans the whole `items` array → inefficient if both are large.

---

<h3 id="wndn1">✅ Corrected + Optimized Function (Expected Behavior)</h3>
<h4 id="lMQ1h">Goal: Remove any item that matches **any** key-value pair in `excludes`.</h4>
```javascript
function excludeItems(items, excludes) {
  // Convert excludes to a Set of stringified keys for fast lookup
  const excludeSet = new Set(excludes.map(e => `${e.k}:${e.v}`));

return items.filter(item => {
// Exclude if any (k,v) matches
return !Object.entries(item).some(([key, val]) => excludeSet.has(`${key}:${val}`));
});
}

```

<h4 id="QzAde">✅ Explanation</h4>
+ We use a `Set` to allow O(1) lookup for key-value exclusion conditions.
+ For each item, we check if **any** of its property matches an exclude pair.
+ We exclude the item if **any match** is found (`some` + `!`).

<h4 id="C6xXc">⏱ Time Complexity (Optimized)</h4>
+ `Set` construction: O(m)
+ `filter` over `n` items × `p` properties (typically 3–5): O(n × p)
+ `Set.has()` lookup: O(1)

➡️ **Total: O(m + n × p)** — efficient and correct.

---

<h3 id="maK3k">✅ Final Answer Summary</h3>
| Question | Answer |
| --- | --- |
| **What does the function do?** | Retains only items matching **all** exclude key-value pairs (wrong) |
| **Is it working as expected?** | ❌ No — logic is incorrect (AND instead of OR, and retain instead of exclude) |
| **Time complexity** | `O(m × n)` — for `m` excludes and `n` items |
| **Optimized solution** | Use `Set` for exclusion matching and `filter` + `some` for correctness |


```

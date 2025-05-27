[此处为语雀卡片，点击链接查看](https://www.yuque.com/docs/175003190#P2zsa)

文档地址：[https://bigfrontend.dev/problem/virtual-dom-II-createElement](https://bigfrontend.dev/problem/virtual-dom-II-createElement)

### Solution Explanation
We create a simple custom representation for elements and text nodes using JavaScript objects. The structure will contain:

+ **type**: The HTML tag name (e.g., `'div'`, `'span'`).
+ **props**: The HTML attributes as key-value pairs.
+ **children**: An array containing either text nodes or other elements.

The `render()` function will recursively process the representation, creating real DOM nodes.

---

### ✅ Code Implementation
```javascript
// createElement function similar to React.createElement
function createElement(type, props, ...children) {
  return {
    type,
    props: props || {},
    children: children.flat()
  }
}

// render function converts virtual DOM elements to real DOM
function render(vNode) {
  // If vNode is a string, create a text node
  if (typeof vNode === 'string') {
    return document.createTextNode(vNode)
  }

  // Create an element
  const $el = document.createElement(vNode.type)

  // Set props
  for (const [key, value] of Object.entries(vNode.props)) {
    // Handle special cases like className
    if (key === 'className') {
      $el.setAttribute('class', value)
    } else {
      $el.setAttribute(key, value)
    }
  }

  // Append children recursively
  vNode.children.map(render).forEach(child => $el.appendChild(child))

  return $el
}

// Usage example provided
const h = createElement

document.body.appendChild(render(
  h('div', {},
    h('h1', {}, ' this is '),
    h('p', { className: 'paragraph' },
      ' a ',
      h('button', {}, ' button '),
      ' from ',
      h('a', { href: 'https://bfe.dev' }, 
        h('b', {}, 'BFE'),
        '.dev'
      )
    )
  )
))
```

---

###  Explanation of Key Parts:
+ **createElement()**
    - Receives a `type`, `props`, and multiple children (`...children`).
    - Returns a simplified virtual DOM object representation.
+ **render()**
    - If the node is a text node (string), it creates a `TextNode`.
    - If the node is an element, it creates an `HTMLElement`.
    - Recursively handles children.

---

### Example Result (HTML):
The provided example would produce this exact HTML structure:

```html
<div>
  <h1> this is </h1>
  <p class="paragraph">
    a <button> button </button> from 
    <a href="https://bfe.dev">
      <b>BFE</b>.dev
    </a>
  </p>
</div>

```

---

### 🚀 Complexity Analysis
+ **Time Complexity:** `O(n)` (linear with total nodes)
+ **Space Complexity:** `O(n)` (linear, due to recursion stack and created DOM elements)


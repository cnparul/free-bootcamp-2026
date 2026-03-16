<p align="center">
  <img src="https://ik.imagekit.io/codingnest/codingnestfinal_bg.svg?updatedAt=1714659978004" alt="CodingNest Logo" width="300"/>
</p>

Welcome to CodingNest's beginner-friendly guide to DOM Traversal! This guide will help you learn how to move around and explore the structure of a web page using JavaScript.

# 🌳 DOM Traversal in JavaScript

## 1. parentNode

### 🧠 Theory
- Returns the parent node of the current element
- Can be used to move up the DOM tree
- Returns null for root elements
- Includes all node types (elements, text, comments)

### 🛠️ Sample Code
```html
<div id="parent">
    <p id="child">Child element</p>
</div>
<script>
    const child = document.getElementById('child');
    const parent = child.parentNode;
    console.log(parent.id); // "parent"
</script>
```

### 🔍 Explanation
- Use to access parent elements
- Can be chained to move up multiple levels
- Useful for finding container elements
- Common in event handling

### 🔁 Practical Examples
```javascript
// Example 1: Find parent with specific class
function findParentWithClass(element, className) {
    while (element && !element.classList.contains(className)) {
        element = element.parentNode;
    }
    return element;
}

// Example 2: Remove parent if empty
function removeEmptyParent(element) {
    const parent = element.parentNode;
    if (parent.children.length === 1) {
        parent.parentNode.removeChild(parent);
    }
}

// Example 3: Get all parent elements
function getAllParents(element) {
    const parents = [];
    while (element.parentNode) {
        parents.push(element.parentNode);
        element = element.parentNode;
    }
    return parents;
}
```

### 🧪 Practice Questions
1. Create a function that finds the closest parent with a specific attribute
2. Implement a function that counts the number of parent elements
3. Create a function that removes a parent element if it meets certain conditions

## 2. childNodes

### 🧠 Theory
- Returns a NodeList of all child nodes
- Includes elements, text nodes, and comments
- Live collection (updates automatically)
- Can be used to iterate through children

### 🛠️ Sample Code
```html
<div id="parent">
    <p>First child</p>
    Text node
    <!-- Comment node -->
    <p>Last child</p>
</div>
<script>
    const parent = document.getElementById('parent');
    console.log(parent.childNodes.length); // 5 (including text and comment nodes)
</script>
```

### 🔍 Explanation
- Use to access all child nodes
- Includes whitespace text nodes
- Can be converted to array for easier manipulation
- Useful for complex DOM traversal

### 🔁 Practical Examples
```javascript
// Example 1: Count different node types
function countNodeTypes(element) {
    const counts = { element: 0, text: 0, comment: 0 };
    Array.from(element.childNodes).forEach(node => {
        counts[node.nodeType === 1 ? 'element' : 
               node.nodeType === 3 ? 'text' : 'comment']++;
    });
    return counts;
}

// Example 2: Remove text nodes
function removeTextNodes(element) {
    Array.from(element.childNodes).forEach(node => {
        if (node.nodeType === 3) {
            element.removeChild(node);
        }
    });
}

// Example 3: Get node by index
function getNodeByIndex(element, index) {
    return element.childNodes[index];
}
```

### 🧪 Practice Questions
1. Create a function that finds all text nodes in an element
2. Implement a function that removes all comment nodes
3. Create a function that counts specific types of child nodes

## 3. firstChild/lastChild

### 🧠 Theory
- firstChild: returns the first child node
- lastChild: returns the last child node
- Can be text nodes or elements
- Returns null if no children exist

### 🛠️ Sample Code
```html
<div id="container">
    <p>First paragraph</p>
    <p>Middle paragraph</p>
    <p>Last paragraph</p>
</div>
<script>
    const container = document.getElementById('container');
    console.log(container.firstChild); // Text node (whitespace)
    console.log(container.lastChild); // Text node (whitespace)
</script>
```

### 🔍 Explanation
- Use to access first/last child nodes
- Includes all node types
- Often used with firstElementChild/lastElementChild
- Common in DOM manipulation

### 🔁 Practical Examples
```javascript
// Example 1: Get first element child
function getFirstElementChild(element) {
    return element.firstElementChild;
}

// Example 2: Remove first and last children
function removeFirstAndLast(element) {
    if (element.firstChild) {
        element.removeChild(element.firstChild);
    }
    if (element.lastChild) {
        element.removeChild(element.lastChild);
    }
}

// Example 3: Swap first and last children
function swapFirstAndLast(element) {
    if (element.firstChild && element.lastChild) {
        const first = element.firstChild;
        const last = element.lastChild;
        element.insertBefore(last, first);
        element.appendChild(first);
    }
}
```

### 🧪 Practice Questions
1. Create a function that finds the first element with a specific class
2. Implement a function that removes the first and last elements
3. Create a function that moves the first child to the end

## 4. nextSibling/previousSibling

### 🧠 Theory
- nextSibling: returns the next node at the same level
- previousSibling: returns the previous node at the same level
- Can be any node type
- Returns null if no sibling exists

### 🛠️ Sample Code
```html
<div>
    <p id="first">First paragraph</p>
    Text node
    <p id="second">Second paragraph</p>
</div>
<script>
    const first = document.getElementById('first');
    console.log(first.nextSibling); // Text node
    console.log(first.nextSibling.nextSibling); // Second paragraph
</script>
```

### 🔍 Explanation
- Use to navigate between siblings
- Includes all node types
- Often used with nextElementSibling
- Useful for horizontal traversal

### 🔁 Practical Examples
```javascript
// Example 1: Find next element sibling
function findNextElement(element) {
    return element.nextElementSibling;
}

// Example 2: Get all siblings
function getAllSiblings(element) {
    const siblings = [];
    let current = element.previousSibling;
    while (current) {
        if (current.nodeType === 1) {
            siblings.unshift(current);
        }
        current = current.previousSibling;
    }
    current = element.nextSibling;
    while (current) {
        if (current.nodeType === 1) {
            siblings.push(current);
        }
        current = current.nextSibling;
    }
    return siblings;
}

// Example 3: Insert after element
function insertAfter(newElement, referenceElement) {
    referenceElement.parentNode.insertBefore(
        newElement,
        referenceElement.nextSibling
    );
}
```

### 🧪 Practice Questions
1. Create a function that finds the next element with a specific class
2. Implement a function that counts the number of siblings
3. Create a function that moves an element after its next sibling

## 5. children

### 🧠 Theory
- Returns a live HTMLCollection of child elements
- Only includes element nodes
- Excludes text and comment nodes
- Can be converted to array for easier manipulation

### 🛠️ Sample Code
```html
<div id="parent">
    <p>First child</p>
    <span>Second child</span>
    <div>Third child</div>
</div>
<script>
    const parent = document.getElementById('parent');
    console.log(parent.children.length); // 3
    console.log(parent.children[0].tagName); // "P"
</script>
```

### 🔍 Explanation
- Use to access child elements only
- More convenient than childNodes
- Live collection (updates automatically)
- Common in DOM manipulation

### 🔁 Practical Examples
```javascript
// Example 1: Get all child elements
function getAllChildElements(element) {
    return Array.from(element.children);
}

// Example 2: Find child by index
function getChildByIndex(element, index) {
    return element.children[index];
}

// Example 3: Filter children by type
function getChildrenByTagName(element, tagName) {
    return Array.from(element.children)
        .filter(child => child.tagName.toLowerCase() === tagName.toLowerCase());
}
```

### 🧪 Practice Questions
1. Create a function that finds all children with a specific class
2. Implement a function that counts children by tag name
3. Create a function that removes all children except the first one 

---
*© 2025 CodingNest. All rights reserved.* 
<p align="center">
  <img src="https://ik.imagekit.io/codingnest/codingnestfinal_bg.svg?updatedAt=1714659978004" alt="CodingNest Logo" width="300"/>
</p>

# 🛠️ DOM Manipulation Methods in JavaScript - CodingNest

Welcome to CodingNest's guide on DOM Manipulation Methods! This guide will teach you how to create, modify, and remove elements on a webpage.

## 🧠 What are Manipulation Methods?

Manipulation methods are like different ways to change your house:
- Adding new furniture (createElement)
- Moving furniture around (appendChild)
- Removing old furniture (removeChild)
- Changing how furniture looks (setAttribute)

## 1. createElement()

### 🧠 Theory
- Creates a new HTML element
- Element is not visible until added to the page
- Can create any HTML element
- Returns the new element

### 🛠️ Sample Code
```html
<div id="container"></div>
<script>
    // Create a new paragraph
    const newParagraph = document.createElement('p');
    newParagraph.textContent = 'This is a new paragraph!';
    
    // Add it to the container
    document.getElementById('container').appendChild(newParagraph);
</script>
```

### 🔍 Explanation
- Use when you want to add new elements
- Element exists in memory but not on page
- Need to add content and attributes
- Need to add to page to see it

### 🔁 Practical Examples
```javascript
// Example 1: Create a button
function createButton() {
    const button = document.createElement('button');
    button.textContent = 'Click me!';
    button.onclick = () => alert('Button clicked!');
    document.body.appendChild(button);
}

// Example 2: Create a list item
function createListItem() {
    const li = document.createElement('li');
    li.textContent = 'New item';
    li.style.color = 'blue';
    document.querySelector('ul').appendChild(li);
}

// Example 3: Create a div with content
function createDiv() {
    const div = document.createElement('div');
    div.innerHTML = '<h2>Title</h2><p>Content</p>';
    div.className = 'box';
    document.body.appendChild(div);
}
```

### 🧪 Practice Questions
1. Create a function that adds a new paragraph to a div
2. Create a function that adds a new button with custom text
3. Create a function that adds a new div with multiple elements inside

## 2. appendChild()

### 🧠 Theory
- Adds an element as the last child
- Can add any node (element, text, etc.)
- Returns the added node
- Can move existing elements

### 🛠️ Sample Code
```html
<div id="parent">
    <p>First child</p>
</div>
<script>
    // Create and add new element
    const newElement = document.createElement('p');
    newElement.textContent = 'Second child';
    document.getElementById('parent').appendChild(newElement);
</script>
```

### 🔍 Explanation
- Use to add elements to the page
- Adds at the end of parent
- Can move existing elements
- Returns the added element

### 🔁 Practical Examples
```javascript
// Example 1: Add multiple elements
function addElements() {
    const parent = document.getElementById('container');
    for (let i = 1; i <= 3; i++) {
        const div = document.createElement('div');
        div.textContent = `Item ${i}`;
        parent.appendChild(div);
    }
}

// Example 2: Move element
function moveElement() {
    const element = document.querySelector('.item');
    const newParent = document.getElementById('new-container');
    newParent.appendChild(element);
}

// Example 3: Add with content
function addWithContent() {
    const div = document.createElement('div');
    div.innerHTML = '<h3>Title</h3><p>Content</p>';
    document.body.appendChild(div);
}
```

### 🧪 Practice Questions
1. Create a function that adds three new paragraphs to a div
2. Create a function that moves an element to a new parent
3. Create a function that adds a new div with multiple children

## 3. removeChild()

### 🧠 Theory
- Removes a child element from its parent
- Returns the removed element
- Element still exists in memory
- Can be added back later

### 🛠️ Sample Code
```html
<div id="parent">
    <p>First child</p>
    <p>Second child</p>
</div>
<script>
    // Remove second paragraph
    const parent = document.getElementById('parent');
    const child = parent.querySelector('p:last-child');
    parent.removeChild(child);
</script>
```

### 🔍 Explanation
- Use to remove elements from page
- Need parent element reference
- Element can be reused
- Returns removed element

### 🔁 Practical Examples
```javascript
// Example 1: Remove last child
function removeLastChild() {
    const parent = document.getElementById('container');
    if (parent.lastChild) {
        parent.removeChild(parent.lastChild);
    }
}

// Example 2: Remove specific element
function removeElement() {
    const element = document.querySelector('.item');
    if (element && element.parentNode) {
        element.parentNode.removeChild(element);
    }
}

// Example 3: Remove all children
function removeAllChildren() {
    const parent = document.getElementById('container');
    while (parent.firstChild) {
        parent.removeChild(parent.firstChild);
    }
}
```

### 🧪 Practice Questions
1. Create a function that removes the last element from a container
2. Create a function that removes all elements with a specific class
3. Create a function that removes an element and adds it to a different container

## 4. setAttribute()

### 🧠 Theory
- Sets or updates an attribute
- Can add any valid HTML attribute
- Works with custom attributes
- Can set multiple attributes

### 🛠️ Sample Code
```html
<div id="box"></div>
<script>
    // Add attributes to div
    const box = document.getElementById('box');
    box.setAttribute('class', 'highlight');
    box.setAttribute('data-type', 'special');
</script>
```

### 🔍 Explanation
- Use to add/modify attributes
- Can set any HTML attribute
- Works with data attributes
- Can set multiple attributes

### 🔁 Practical Examples
```javascript
// Example 1: Set multiple attributes
function setAttributes() {
    const element = document.createElement('img');
    element.setAttribute('src', 'image.jpg');
    element.setAttribute('alt', 'Description');
    element.setAttribute('class', 'thumbnail');
    document.body.appendChild(element);
}

// Example 2: Update attribute
function updateAttribute() {
    const input = document.querySelector('input');
    input.setAttribute('placeholder', 'Enter your name');
    input.setAttribute('required', '');
}

// Example 3: Add data attributes
function addDataAttributes() {
    const element = document.querySelector('.item');
    element.setAttribute('data-id', '123');
    element.setAttribute('data-type', 'special');
}
```

### 🧪 Practice Questions
1. Create a function that adds multiple attributes to an element
2. Create a function that updates an input's placeholder and required status
3. Create a function that adds data attributes to multiple elements

## 5. getAttribute()

### 🧠 Theory
- Gets the value of an attribute
- Returns null if attribute doesn't exist
- Works with any HTML attribute
- Can get custom attributes

### 🛠️ Sample Code
```html
<div id="box" class="highlight" data-type="special"></div>
<script>
    // Get attributes
    const box = document.getElementById('box');
    const className = box.getAttribute('class');
    const dataType = box.getAttribute('data-type');
    console.log(className, dataType);
</script>
```

### 🔍 Explanation
- Use to read attribute values
- Returns null if not found
- Works with any attribute
- Case sensitive

### 🔁 Practical Examples
```javascript
// Example 1: Check attribute
function checkAttribute() {
    const element = document.querySelector('.item');
    const type = element.getAttribute('data-type');
    if (type === 'special') {
        element.style.backgroundColor = 'yellow';
    }
}

// Example 2: Get multiple attributes
function getAttributes() {
    const img = document.querySelector('img');
    const src = img.getAttribute('src');
    const alt = img.getAttribute('alt');
    console.log(`Image: ${alt} (${src})`);
}

// Example 3: Check required fields
function checkRequired() {
    const inputs = document.querySelectorAll('input');
    inputs.forEach(input => {
        if (input.getAttribute('required')) {
            input.style.borderColor = 'red';
        }
    });
}
```

### 🧪 Practice Questions
1. Create a function that checks if an element has a specific class
2. Create a function that gets all data attributes from an element
3. Create a function that checks if all required fields are filled

## 📝 Quick Reference

Common manipulation methods:
- `createElement()` - Create new element
- `appendChild()` - Add element to page
- `removeChild()` - Remove element
- `setAttribute()` - Add/modify attribute
- `getAttribute()` - Get attribute value

## 🎯 Next Steps
- Practice creating and modifying elements
- Learn about event handling
- Try combining different methods

Remember: The best way to learn is to experiment! Try different manipulation methods and see what you can create.

---
*© 2025 CodingNest. All rights reserved.* 
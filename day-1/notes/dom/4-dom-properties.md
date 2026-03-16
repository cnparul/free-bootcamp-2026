<p align="center">
  <img src="https://ik.imagekit.io/codingnest/codingnestfinal_bg.svg?updatedAt=1714659978004" alt="CodingNest Logo" width="300"/>
</p>

# 🎨 DOM Properties in JavaScript - CodingNest

Welcome to CodingNest's guide on DOM Properties! This guide will teach you how to work with different properties of HTML elements.

## 🧠 What are DOM Properties?

DOM properties are like different ways to describe and change elements:
- What's inside an element (innerHTML)
- The text content (textContent)
- How it looks (style)
- What classes it has (className)
- Its unique name (id)

## 1. innerHTML

### 🧠 Theory
- Gets or sets the HTML content inside an element
- Can include HTML tags
- Can add new elements
- Can replace existing content

### 🛠️ Sample Code
```html
<div id="container">
    <p>Original content</p>
</div>
<script>
    // Change content with HTML
    const container = document.getElementById('container');
    container.innerHTML = '<h2>New Title</h2><p>New content</p>';
</script>
```

### 🔍 Explanation
- Use to change element content
- Can include HTML tags
- Replaces all existing content
- Be careful with user input

### 🔁 Practical Examples
```javascript
// Example 1: Add HTML content
function addContent() {
    const div = document.getElementById('box');
    div.innerHTML = '<h3>Welcome!</h3><p>This is new content.</p>';
}

// Example 2: Append HTML
function appendContent() {
    const div = document.getElementById('box');
    div.innerHTML += '<p>This is added content.</p>';
}

// Example 3: Create list
function createList() {
    const ul = document.getElementById('list');
    ul.innerHTML = `
        <li>First item</li>
        <li>Second item</li>
        <li>Third item</li>
    `;
}
```

### 🧪 Practice Questions
1. Create a function that adds a new paragraph with HTML content
2. Create a function that creates a list of items from an array
3. Create a function that adds a button with an icon

## 2. textContent

### 🧠 Theory
- Gets or sets the text content of an element
- Ignores HTML tags
- Safer than innerHTML
- Preserves whitespace

### 🛠️ Sample Code
```html
<div id="message">
    <p>Hello <strong>World</strong>!</p>
</div>
<script>
    // Get and set text content
    const message = document.getElementById('message');
    console.log(message.textContent); // "Hello World!"
    message.textContent = 'New message';
</script>
```

### 🔍 Explanation
- Use for plain text
- Ignores HTML tags
- Safer than innerHTML
- Preserves formatting

### 🔁 Practical Examples
```javascript
// Example 1: Change text
function changeText() {
    const element = document.querySelector('.message');
    element.textContent = 'This is new text';
}

// Example 2: Get text
function getText() {
    const element = document.querySelector('.content');
    console.log(element.textContent);
}

// Example 3: Add text
function addText() {
    const element = document.querySelector('.box');
    element.textContent += ' (Updated)';
}
```

### 🧪 Practice Questions
1. Create a function that changes the text of a heading
2. Create a function that gets the text from multiple paragraphs
3. Create a function that adds text to an existing element

## 3. style

### 🧠 Theory
- Gets or sets CSS styles
- Properties use camelCase
- Changes apply immediately
- Can set multiple styles

### 🛠️ Sample Code
```html
<div id="box">Hello</div>
<script>
    // Change styles
    const box = document.getElementById('box');
    box.style.backgroundColor = 'blue';
    box.style.color = 'white';
    box.style.padding = '10px';
</script>
```

### 🔍 Explanation
- Use to change appearance
- Properties use camelCase
- Changes apply instantly
- Can set multiple styles

### 🔁 Practical Examples
```javascript
// Example 1: Change color
function changeColor() {
    const element = document.querySelector('.item');
    element.style.color = 'red';
    element.style.backgroundColor = 'yellow';
}

// Example 2: Toggle visibility
function toggleVisibility() {
    const element = document.querySelector('.box');
    element.style.display = 
        element.style.display === 'none' ? 'block' : 'none';
}

// Example 3: Set multiple styles
function setStyles() {
    const element = document.querySelector('.card');
    element.style.border = '1px solid black';
    element.style.padding = '10px';
    element.style.margin = '5px';
}
```

### 🧪 Practice Questions
1. Create a function that changes the background color of an element
2. Create a function that toggles the visibility of an element
3. Create a function that adds a border and padding to an element

## 4. className

### 🧠 Theory
- Gets or sets the class attribute
- Can have multiple classes
- Space-separated list
- Can add/remove classes

### 🛠️ Sample Code
```html
<div id="box" class="container">Content</div>
<script>
    // Change class
    const box = document.getElementById('box');
    box.className = 'container highlight';
</script>
```

### 🔍 Explanation
- Use to change classes
- Can have multiple classes
- Space-separated list
- Replaces all classes

### 🔁 Practical Examples
```javascript
// Example 1: Add class
function addClass() {
    const element = document.querySelector('.item');
    element.className = 'item active';
}

// Example 2: Remove class
function removeClass() {
    const element = document.querySelector('.item');
    element.className = 'item';
}

// Example 3: Toggle class
function toggleClass() {
    const element = document.querySelector('.item');
    element.className = element.className.includes('active') 
        ? 'item' 
        : 'item active';
}
```

### 🧪 Practice Questions
1. Create a function that adds a class to an element
2. Create a function that removes a class from an element
3. Create a function that toggles a class on an element

## 5. id

### 🧠 Theory
- Gets or sets the id attribute
- Must be unique
- Used for identification
- Case sensitive

### 🛠️ Sample Code
```html
<div id="header">Header</div>
<script>
    // Change id
    const element = document.getElementById('header');
    element.id = 'main-header';
</script>
```

### 🔍 Explanation
- Use for unique identification
- Must be unique in page
- Case sensitive
- Used for selection

### 🔁 Practical Examples
```javascript
// Example 1: Change id
function changeId() {
    const element = document.querySelector('.box');
    element.id = 'new-box';
}

// Example 2: Check id
function checkId() {
    const element = document.querySelector('.item');
    if (element.id === 'special') {
        element.style.color = 'red';
    }
}

// Example 3: Set id
function setId() {
    const element = document.createElement('div');
    element.id = 'new-element';
    document.body.appendChild(element);
}
```

### 🧪 Practice Questions
1. Create a function that changes the id of an element
2. Create a function that checks if an element has a specific id
3. Create a function that creates a new element with a specific id

## 📝 Quick Reference

Common DOM properties:
- `innerHTML` - Get/set HTML content
- `textContent` - Get/set text content
- `style` - Change CSS styles
- `className` - Get/set classes
- `id` - Get/set unique identifier

## 🎯 Next Steps
- Practice changing element properties
- Learn about event handling
- Try combining different properties

Remember: The best way to learn is to experiment! Try different properties and see what you can create.

---
*© 2025 CodingNest. All rights reserved.* 
<p align="center">
  <img src="https://ik.imagekit.io/codingnest/codingnestfinal_bg.svg?updatedAt=1714659978004" alt="CodingNest Logo" width="300"/>
</p>

# 🎯 DOM Selection Methods in JavaScript - CodingNest

Welcome to CodingNest's guide on DOM Selection Methods! This guide will teach you different ways to find and select elements on a webpage.

## 🧠 What are Selection Methods?

Selection methods are like different ways to find things in your house:
- Finding something by its unique name (ID)
- Finding things that look similar (Class)
- Finding things of the same type (Tag)
- Finding things by their description (Selector)

## 1. getElementById()

### 🧠 Theory
- Finds an element by its unique ID
- Fastest selection method
- Returns a single element
- Returns null if not found

### 🛠️ Sample Code
```html
<div id="header">Welcome!</div>
<script>
    // Find element with ID "header"
    const header = document.getElementById('header');
    header.style.color = 'blue';
</script>
```

### 🔍 Explanation
- Use when you need to find one specific element
- ID must be unique in the page
- Case sensitive
- Returns null if element not found

### 🔁 Practical Examples
```javascript
// Example 1: Change content
function changeHeader() {
    const header = document.getElementById('header');
    header.textContent = 'New Header!';
}

// Example 2: Toggle visibility
function toggleElement() {
    const element = document.getElementById('myElement');
    element.style.display = element.style.display === 'none' ? 'block' : 'none';
}

// Example 3: Add event listener
function setupButton() {
    const button = document.getElementById('myButton');
    button.addEventListener('click', () => {
        alert('Button clicked!');
    });
}
```

### 🧪 Practice Questions
1. Create a function that changes the background color of an element by ID
2. Create a function that toggles a class on an element by ID
3. Create a counter that updates a span element's content

## 2. getElementsByClassName()

### 🧠 Theory
- Finds elements by their class name
- Returns a collection of elements
- Live collection (updates automatically)
- Returns empty collection if none found

### 🛠️ Sample Code
```html
<p class="highlight">First paragraph</p>
<p class="highlight">Second paragraph</p>
<script>
    // Find all elements with class "highlight"
    const highlights = document.getElementsByClassName('highlight');
    for (let element of highlights) {
        element.style.color = 'red';
    }
</script>
```

### 🔍 Explanation
- Use when you need to find multiple elements
- Can have multiple classes
- Returns HTMLCollection
- Live collection updates automatically

### 🔁 Practical Examples
```javascript
// Example 1: Change all elements
function changeAllHighlights() {
    const highlights = document.getElementsByClassName('highlight');
    for (let element of highlights) {
        element.style.backgroundColor = 'yellow';
    }
}

// Example 2: Count elements
function countElements() {
    const elements = document.getElementsByClassName('item');
    console.log(`Found ${elements.length} items`);
}

// Example 3: Add class to all
function addClassToAll() {
    const elements = document.getElementsByClassName('box');
    for (let element of elements) {
        element.classList.add('active');
    }
}
```

### 🧪 Practice Questions
1. Create a function that changes the font size of all elements with a specific class
2. Create a function that counts and displays the number of elements with a class
3. Create a function that adds a border to all elements with a class

## 3. getElementsByTagName()

### 🧠 Theory
- Finds elements by their tag name
- Returns a collection of elements
- Live collection
- Returns empty collection if none found

### 🛠️ Sample Code
```html
<p>First paragraph</p>
<p>Second paragraph</p>
<script>
    // Find all paragraph elements
    const paragraphs = document.getElementsByTagName('p');
    for (let p of paragraphs) {
        p.style.color = 'green';
    }
</script>
```

### 🔍 Explanation
- Use when you need to find all elements of a type
- Returns HTMLCollection
- Live collection updates automatically
- Case insensitive for HTML elements

### 🔁 Practical Examples
```javascript
// Example 1: Style all paragraphs
function styleAllParagraphs() {
    const paragraphs = document.getElementsByTagName('p');
    for (let p of paragraphs) {
        p.style.fontSize = '18px';
        p.style.lineHeight = '1.5';
    }
}

// Example 2: Count images
function countImages() {
    const images = document.getElementsByTagName('img');
    console.log(`Page has ${images.length} images`);
}

// Example 3: Add class to all links
function styleAllLinks() {
    const links = document.getElementsByTagName('a');
    for (let link of links) {
        link.classList.add('styled-link');
    }
}
```

### 🧪 Practice Questions
1. Create a function that changes the color of all links
2. Create a function that counts and displays the number of images
3. Create a function that adds a border to all paragraphs

## 4. querySelector()

### 🧠 Theory
- Finds first element matching CSS selector
- More flexible than other methods
- Returns single element
- Returns null if not found

### 🛠️ Sample Code
```html
<div class="box">
    <p class="highlight">First paragraph</p>
    <p>Second paragraph</p>
</div>
<script>
    // Find first paragraph with class "highlight"
    const element = document.querySelector('.box .highlight');
    element.style.color = 'purple';
</script>
```

### 🔍 Explanation
- Use when you need complex selection
- Can use any CSS selector
- Returns first matching element
- More flexible but slower than getElementById

### 🔁 Practical Examples
```javascript
// Example 1: Find specific element
function findElement() {
    const element = document.querySelector('.box .highlight');
    if (element) {
        element.style.backgroundColor = 'yellow';
    }
}

// Example 2: Find by attribute
function findByAttribute() {
    const element = document.querySelector('[data-type="special"]');
    if (element) {
        element.classList.add('active');
    }
}

// Example 3: Find by multiple classes
function findByClasses() {
    const element = document.querySelector('.box.highlight.active');
    if (element) {
        element.style.border = '2px solid red';
    }
}
```

### 🧪 Practice Questions
1. Create a function that finds and styles the first element with a specific class
2. Create a function that finds an element by its data attribute
3. Create a function that finds and modifies the first element matching multiple conditions

## 5. querySelectorAll()

### 🧠 Theory
- Finds all elements matching CSS selector
- Returns static NodeList
- More flexible than other methods
- Returns empty NodeList if none found

### 🛠️ Sample Code
```html
<div class="box">
    <p class="highlight">First paragraph</p>
    <p class="highlight">Second paragraph</p>
</div>
<script>
    // Find all paragraphs with class "highlight"
    const elements = document.querySelectorAll('.box .highlight');
    elements.forEach(element => {
        element.style.color = 'orange';
    });
</script>
```

### 🔍 Explanation
- Use when you need multiple elements
- Can use any CSS selector
- Returns static NodeList
- More flexible but slower than getElementsByClassName

### 🔁 Practical Examples
```javascript
// Example 1: Style all matching elements
function styleAllMatching() {
    const elements = document.querySelectorAll('.box .highlight');
    elements.forEach(element => {
        element.style.backgroundColor = 'lightblue';
    });
}

// Example 2: Count specific elements
function countMatching() {
    const elements = document.querySelectorAll('.box .highlight');
    console.log(`Found ${elements.length} matching elements`);
}

// Example 3: Add class to all matching
function addClassToMatching() {
    const elements = document.querySelectorAll('.box .highlight');
    elements.forEach(element => {
        element.classList.add('active');
    });
}
```

### 🧪 Practice Questions
1. Create a function that changes the style of all elements matching a selector
2. Create a function that counts and displays the number of matching elements
3. Create a function that adds a class to all matching elements

## 📝 Quick Reference

Common selection methods:
- `getElementById()` - Find by unique ID
- `getElementsByClassName()` - Find by class name
- `getElementsByTagName()` - Find by tag name
- `querySelector()` - Find first matching element
- `querySelectorAll()` - Find all matching elements

## 🎯 Next Steps
- Practice using different selection methods
- Learn about DOM manipulation
- Try combining selection methods

Remember: The best way to learn is to experiment! Try different selection methods and see what works best for your needs.

---
*© 2025 CodingNest. All rights reserved.* 
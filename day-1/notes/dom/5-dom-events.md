<p align="center">
  <img src="https://ik.imagekit.io/codingnest/codingnestfinal_bg.svg?updatedAt=1714659978004" alt="CodingNest Logo" width="300"/>
</p>

# 🎯 DOM Events in JavaScript - CodingNest

Welcome to CodingNest's guide on DOM Events! This guide will teach you how to make your web pages interactive by responding to user actions.

## 🧠 What are DOM Events?

DOM events are like different ways users can interact with your webpage:
- Clicking a button (click)
- Typing in a text box (input)
- Moving the mouse (mouseover)
- Pressing a key (keydown)
- Loading the page (load)

## 1. Event Types

### 🧠 Theory
- Mouse events (click, mouseover, mouseout)
- Keyboard events (keydown, keyup, keypress)
- Form events (submit, change, input)
- Document events (load, DOMContentLoaded)
- Window events (resize, scroll)

### 🛠️ Sample Code
```html
<button id="myButton">Click Me!</button>
<script>
    // Add click event
    const button = document.getElementById('myButton');
    button.addEventListener('click', () => {
        alert('Button clicked!');
    });
</script>
```

### 🔍 Explanation
- Events happen when users interact
- Many types of events available
- Can respond to any event
- Events trigger functions

### 🔁 Practical Examples
```javascript
// Example 1: Click event
function setupClick() {
    const button = document.querySelector('.btn');
    button.addEventListener('click', () => {
        console.log('Button clicked!');
    });
}

// Example 2: Mouse over event
function setupHover() {
    const box = document.querySelector('.box');
    box.addEventListener('mouseover', () => {
        box.style.backgroundColor = 'yellow';
    });
}

// Example 3: Key press event
function setupKeyPress() {
    document.addEventListener('keydown', (event) => {
        if (event.key === 'Enter') {
            console.log('Enter key pressed!');
        }
    });
}
```

### 🧪 Practice Questions
1. Create a function that changes color when mouse hovers over an element
2. Create a function that shows an alert when a key is pressed
3. Create a function that changes text when a button is clicked

## 2. Event Handling

### 🧠 Theory
- Use addEventListener to handle events
- Can add multiple handlers
- Can remove handlers
- Event object contains information

### 🛠️ Sample Code
```html
<div id="box">Hover over me</div>
<script>
    // Add and remove event handler
    const box = document.getElementById('box');
    
    function handleHover() {
        box.style.backgroundColor = 'blue';
    }
    
    box.addEventListener('mouseover', handleHover);
    // Later: box.removeEventListener('mouseover', handleHover);
</script>
```

### 🔍 Explanation
- Use addEventListener to handle events
- Can add multiple handlers
- Can remove handlers
- Event object has info

### 🔁 Practical Examples
```javascript
// Example 1: Add event handler
function addHandler() {
    const button = document.querySelector('.btn');
    button.addEventListener('click', () => {
        console.log('Button clicked!');
    });
}

// Example 2: Remove event handler
function removeHandler() {
    const button = document.querySelector('.btn');
    const handler = () => console.log('Clicked!');
    button.addEventListener('click', handler);
    // Later: button.removeEventListener('click', handler);
}

// Example 3: Multiple handlers
function addMultipleHandlers() {
    const box = document.querySelector('.box');
    box.addEventListener('mouseover', () => {
        box.style.backgroundColor = 'yellow';
    });
    box.addEventListener('mouseout', () => {
        box.style.backgroundColor = 'white';
    });
}
```

### 🧪 Practice Questions
1. Create a function that adds a click handler to a button
2. Create a function that removes an event handler
3. Create a function that adds multiple handlers to an element

## 3. Event Propagation

### 🧠 Theory
- Events bubble up through elements
- Can stop propagation
- Can capture events
- Three phases: capture, target, bubble

### 🛠️ Sample Code
```html
<div id="parent">
    <button id="child">Click Me</button>
</div>
<script>
    // Show event propagation
    const parent = document.getElementById('parent');
    const child = document.getElementById('child');
    
    parent.addEventListener('click', () => {
        console.log('Parent clicked');
    });
    
    child.addEventListener('click', (event) => {
        console.log('Child clicked');
        // event.stopPropagation();
    });
</script>
```

### 🔍 Explanation
- Events bubble up through elements
- Can stop event bubbling
- Can capture events
- Three phases of events

### 🔁 Practical Examples
```javascript
// Example 1: Stop propagation
function stopPropagation() {
    const button = document.querySelector('.btn');
    button.addEventListener('click', (event) => {
        event.stopPropagation();
        console.log('Button clicked!');
    });
}

// Example 2: Capture phase
function useCapture() {
    const parent = document.querySelector('.parent');
    parent.addEventListener('click', () => {
        console.log('Parent clicked!');
    }, true);
}

// Example 3: Check phase
function checkPhase(event) {
    if (event.eventPhase === Event.CAPTURING_PHASE) {
        console.log('Capture phase');
    } else if (event.eventPhase === Event.BUBBLING_PHASE) {
        console.log('Bubble phase');
    }
}
```

### 🧪 Practice Questions
1. Create a function that stops event propagation
2. Create a function that uses event capture
3. Create a function that checks event phase

## 4. Event Delegation

### 🧠 Theory
- Handle events on parent element
- Use event.target to find source
- More efficient than many handlers
- Works with dynamic content

### 🛠️ Sample Code
```html
<ul id="list">
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
<script>
    // Use event delegation
    const list = document.getElementById('list');
    list.addEventListener('click', (event) => {
        if (event.target.tagName === 'LI') {
            event.target.style.color = 'red';
        }
    });
</script>
```

### 🔍 Explanation
- Handle events on parent
- Use event.target
- More efficient
- Works with dynamic content

### 🔁 Practical Examples
```javascript
// Example 1: List item clicks
function handleListClicks() {
    const list = document.querySelector('.list');
    list.addEventListener('click', (event) => {
        if (event.target.tagName === 'LI') {
            event.target.classList.toggle('selected');
        }
    });
}

// Example 2: Button clicks
function handleButtonClicks() {
    const container = document.querySelector('.container');
    container.addEventListener('click', (event) => {
        if (event.target.classList.contains('btn')) {
            console.log('Button clicked:', event.target.textContent);
        }
    });
}

// Example 3: Form inputs
function handleFormInputs() {
    const form = document.querySelector('.form');
    form.addEventListener('change', (event) => {
        if (event.target.tagName === 'INPUT') {
            console.log('Input changed:', event.target.value);
        }
    });
}
```

### 🧪 Practice Questions
1. Create a function that handles clicks on list items
2. Create a function that handles clicks on buttons in a container
3. Create a function that handles changes to form inputs

## 📝 Quick Reference

Common event types:
- `click` - Mouse click
- `mouseover` - Mouse hover
- `keydown` - Key press
- `submit` - Form submission
- `load` - Page load

## 🎯 Next Steps
- Practice handling different events
- Learn about event delegation
- Try combining different events

Remember: The best way to learn is to experiment! Try different events and see what you can create.

---
*© 2025 CodingNest. All rights reserved.* 
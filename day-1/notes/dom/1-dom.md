<p align="center">
  <img src="https://ik.imagekit.io/codingnest/codingnestfinal_bg.svg?updatedAt=1714659978004" alt="CodingNest Logo" width="300"/>
</p>

# 🌳 Introduction to DOM (Document Object Model) in JavaScript - CodingNest

Welcome to CodingNest's beginner-friendly guide to the Document Object Model (DOM). This guide will help you understand how to interact with web pages using JavaScript.

## 🎯 What is DOM?

Imagine you have a webpage. The DOM is like a family tree of everything on that webpage. Just like how you can point to different members in a family tree, you can point to different parts of a webpage using the DOM.

### Simple Example:
Think of a webpage like a house:
- The `document` is like the entire house
- `html` is like the foundation
- `body` is like the main room
- Other elements like `div`, `p`, `h1` are like furniture in the room

## 🧠 Basic Concepts

### 1. What is a Node?
- Everything in the DOM is called a "node"
- There are different types of nodes:
  - Element nodes (like `<div>`, `<p>`, `<h1>`)
  - Text nodes (the actual text inside elements)
  - Attribute nodes (like `class`, `id`)

### 2. The Document Object
- `document` is like a special key that lets you access everything on the webpage
- It's always available in your JavaScript code
- Think of it as your way to talk to the webpage

## 🛠️ Your First DOM Code

Let's start with a very simple example:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My First DOM Page</title>
</head>
<body>
    <h1>Hello!</h1>
    <p>This is my first paragraph.</p>
    
    <script>
        // This is how we can change text using DOM
        const heading = document.querySelector('h1');
        heading.textContent = 'Hello, DOM!';
        
        // This is how we can change style
        heading.style.color = 'blue';
    </script>
</body>
</html>
```

## 🔍 Understanding the Code

Let's break down what we did:

1. `document.querySelector('h1')`
   - This finds the first `<h1>` on the page
   - It's like saying "find the heading"

2. `heading.textContent = 'Hello, DOM!'`
   - This changes the text inside the heading
   - It's like changing what's written on a sign

3. `heading.style.color = 'blue'`
   - This changes the color of the text
   - It's like changing the color of a marker

## 🔁 Simple Examples

### Example 1: Changing Text
```javascript
// Find a paragraph and change its text
const paragraph = document.querySelector('p');
paragraph.textContent = 'This is new text!';
```

### Example 2: Adding a New Element
```javascript
// Create a new paragraph
const newParagraph = document.createElement('p');
newParagraph.textContent = 'This is a new paragraph!';

// Add it to the page
document.body.appendChild(newParagraph);
```

### Example 3: Changing Colors
```javascript
// Find an element and change its color
const element = document.querySelector('.my-element');
element.style.backgroundColor = 'yellow';
```

## 🧪 Practice Exercises (Do it after completing all notes)

Try these simple exercises:

1. **Basic Text Change**
   - Create a webpage with a heading
   - Write JavaScript to change the heading text
   - Change the heading color to red

2. **Adding Elements**
   - Create a webpage with a div
   - Add a new paragraph inside the div
   - Add a button that changes the paragraph text

3. **Simple Styling**
   - Create a webpage with a paragraph
   - Add a button that changes the paragraph's background color
   - Add a button that changes the text color

## 📝 Quick Reference

Common things you can do with DOM:
- `document.querySelector()` - Find an element
- `element.textContent` - Change text
- `element.style` - Change style
- `document.createElement()` - Create new element
- `element.appendChild()` - Add element to page

## 🎯 Next Steps
- Learn about different ways to find elements
- Practice changing element styles
- Try creating and adding new elements

Remember: The best way to learn is to experiment! Try changing the examples and see what happens.

---
*© 2025 CodingNest. All rights reserved.*

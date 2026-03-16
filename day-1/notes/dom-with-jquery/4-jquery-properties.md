<p align="center">
  <img src="https://ik.imagekit.io/codingnest/codingnestfinal_bg.svg?updatedAt=1714659978004" alt="CodingNest Logo" width="300"/>
</p>

# 🎨 jQuery Properties - CodingNest

Welcome to CodingNest's guide on jQuery Properties! This guide will teach you how to work with different properties of HTML elements using jQuery's simple and powerful methods.

## 🧠 What are jQuery Properties?

jQuery properties are like different ways to describe and change elements, but much easier than vanilla JavaScript:
- What's inside an element (`html()`, `text()`)
- How it looks (`css()`)
- What classes it has (`addClass()`, `removeClass()`)
- Its attributes (`attr()`, `prop()`)
- Its dimensions (`width()`, `height()`)

## 1. html()

### 🧠 Theory
- Gets or sets the HTML content inside an element
- Can include HTML tags
- Equivalent to `innerHTML` in vanilla JavaScript
- Much cleaner syntax with jQuery

### 🛠️ Sample Code
```html
<div id="container">
    <p>Original content</p>
</div>
<script>
    // DOM Version
    const container = document.getElementById('container');
    container.innerHTML = '<h2>New Title</h2><p>New content</p>';
    
    // jQuery Version
    $('#container').html('<h2>New Title</h2><p>New content</p>');
</script>
```

### 🔍 Explanation
- `html()`: gets the HTML content
- `html(content)`: sets new HTML content
- Replaces all existing content
- Can include any valid HTML

### 🔁 Practical Examples
```javascript
// Example 1: Add HTML content
function addContent() {
    // DOM Version
    const div = document.getElementById('box');
    div.innerHTML = '<h3>Welcome!</h3><p>This is new content.</p>';
    
    // jQuery Version
    $('#box').html('<h3>Welcome!</h3><p>This is new content.</p>');
}

// Example 2: Get and modify content
function modifyContent() {
    // DOM Version
    const div = document.getElementById('box');
    const currentContent = div.innerHTML;
    div.innerHTML = currentContent + '<p>Added content.</p>';
    
    // jQuery Version
    const currentContent = $('#box').html();
    $('#box').html(currentContent + '<p>Added content.</p>');
}

// Example 3: Create list dynamically
function createList() {
    // DOM Version
    const ul = document.getElementById('list');
    ul.innerHTML = `
        <li>First item</li>
        <li>Second item</li>
        <li>Third item</li>
    `;
    
    // jQuery Version
    $('#list').html(`
        <li>First item</li>
        <li>Second item</li>
        <li>Third item</li>
    `);
}
```

### 🧪 Practice Questions
1. Create a function that adds a new paragraph with HTML content using jQuery
2. Create a function that creates a list of items from an array using jQuery
3. Create a function that adds a button with an icon using jQuery

## 2. text()

### 🧠 Theory
- Gets or sets the text content of an element
- Ignores HTML tags (treats them as plain text)
- Equivalent to `textContent` in vanilla JavaScript
- Safer than `html()` for user input

### 🛠️ Sample Code
```html
<div id="message">
    <p>Hello <strong>World</strong>!</p>
</div>
<script>
    // DOM Version
    const message = document.getElementById('message');
    console.log(message.textContent); // "Hello World!"
    message.textContent = 'New message';
    
    // jQuery Version
    console.log($('#message').text()); // "Hello World!"
    $('#message').text('New message');
</script>
```

### 🔍 Explanation
- `text()`: gets the plain text content
- `text(content)`: sets new text content
- HTML tags are treated as plain text
- Automatically escapes HTML characters

### 🔁 Practical Examples
```javascript
// Example 1: Change text safely
function changeText() {
    // DOM Version
    const element = document.querySelector('.message');
    element.textContent = 'This is new text';
    
    // jQuery Version
    $('.message').text('This is new text');
}

// Example 2: Get text from multiple elements
function getAllText() {
    // DOM Version
    const elements = document.querySelectorAll('.content');
    elements.forEach(element => {
        console.log(element.textContent);
    });
    
    // jQuery Version
    $('.content').each(function() {
        console.log($(this).text());
    });
}

// Example 3: Append text safely
function appendText() {
    // DOM Version
    const element = document.querySelector('.box');
    element.textContent += ' (Updated)';
    
    // jQuery Version
    const currentText = $('.box').text();
    $('.box').text(currentText + ' (Updated)');
}
```

### 🧪 Practice Questions
1. Create a function that changes the text of a heading using jQuery
2. Create a function that gets the text from multiple paragraphs using jQuery
3. Create a function that safely displays user input using jQuery

## 3. css()

### 🧠 Theory
- Gets or sets CSS styles
- Can set single or multiple properties
- Handles browser differences automatically
- Much easier than vanilla JavaScript styling

### 🛠️ Sample Code
```html
<div id="box">Hello</div>
<script>
    // DOM Version
    const box = document.getElementById('box');
    box.style.backgroundColor = 'blue';
    box.style.color = 'white';
    box.style.padding = '10px';
    
    // jQuery Version
    $('#box').css({
        'background-color': 'blue',
        'color': 'white',
        'padding': '10px'
    });
</script>
```

### 🔍 Explanation
- `css(property)`: gets CSS property value
- `css(property, value)`: sets single property
- `css(object)`: sets multiple properties
- Handles vendor prefixes automatically

### 🔁 Practical Examples
```javascript
// Example 1: Change single property
function changeColor() {
    // DOM Version
    const element = document.querySelector('.item');
    element.style.color = 'red';
    element.style.backgroundColor = 'yellow';
    
    // jQuery Version
    $('.item').css('color', 'red').css('background-color', 'yellow');
    // Or
    $('.item').css({
        'color': 'red',
        'background-color': 'yellow'
    });
}

// Example 2: Toggle visibility
function toggleVisibility() {
    // DOM Version
    const element = document.querySelector('.box');
    element.style.display = 
        element.style.display === 'none' ? 'block' : 'none';
    
    // jQuery Version
    $('.box').toggle(); // Built-in method
    // Or manual toggle
    const isVisible = $('.box').css('display') !== 'none';
    $('.box').css('display', isVisible ? 'none' : 'block');
}

// Example 3: Animate-like styling
function animateStyles() {
    // DOM Version
    const element = document.querySelector('.card');
    element.style.transform = 'scale(1.1)';
    element.style.transition = 'all 0.3s ease';
    element.style.boxShadow = '0 4px 8px rgba(0,0,0,0.2)';
    
    // jQuery Version
    $('.card').css({
        'transform': 'scale(1.1)',
        'transition': 'all 0.3s ease',
        'box-shadow': '0 4px 8px rgba(0,0,0,0.2)'
    });
}
```

### 🧪 Practice Questions
1. Create a function that changes the background color of an element using jQuery
2. Create a function that applies multiple styles to create a button effect
3. Create a function that gets and displays the computed styles of an element

## 4. addClass(), removeClass(), toggleClass()

### 🧠 Theory
- `addClass()`: adds CSS classes
- `removeClass()`: removes CSS classes
- `toggleClass()`: toggles CSS classes
- `hasClass()`: checks if class exists
- Much better than manipulating `className`

### 🛠️ Sample Code
```html
<div id="box" class="container">Content</div>
<script>
    // DOM Version
    const box = document.getElementById('box');
    box.classList.add('highlight');
    box.classList.remove('container');
    box.classList.toggle('active');
    
    // jQuery Version
    $('#box').addClass('highlight');
    $('#box').removeClass('container');
    $('#box').toggleClass('active');
</script>
```

### 🔍 Explanation
- Can add/remove multiple classes at once
- `toggleClass()` is very useful for state changes
- `hasClass()` for conditional logic
- Works with all selected elements

### 🔁 Practical Examples
```javascript
// Example 1: Interactive button
function createInteractiveButton() {
    // DOM Version
    const button = document.querySelector('.btn');
    button.addEventListener('mouseenter', () => {
        button.classList.add('hover');
    });
    button.addEventListener('mouseleave', () => {
        button.classList.remove('hover');
    });
    button.addEventListener('click', () => {
        button.classList.toggle('active');
    });
    
    // jQuery Version
    $('.btn')
        .on('mouseenter', function() {
            $(this).addClass('hover');
        })
        .on('mouseleave', function() {
            $(this).removeClass('hover');
        })
        .on('click', function() {
            $(this).toggleClass('active');
        });
}

// Example 2: Form validation styling
function styleFormValidation() {
    // DOM Version
    const inputs = document.querySelectorAll('input');
    inputs.forEach(input => {
        input.addEventListener('blur', () => {
            if (input.value.trim() === '') {
                input.classList.add('error');
                input.classList.remove('valid');
            } else {
                input.classList.add('valid');
                input.classList.remove('error');
            }
        });
    });
    
    // jQuery Version
    $('input').on('blur', function() {
        const $this = $(this);
        if ($this.val().trim() === '') {
            $this.addClass('error').removeClass('valid');
        } else {
            $this.addClass('valid').removeClass('error');
        }
    });
}

// Example 3: Navigation menu
function createNavMenu() {
    // jQuery Version
    $('.nav-item').on('click', function() {
        $('.nav-item').removeClass('active'); // Remove from all
        $(this).addClass('active');          // Add to clicked
    });
}
```

### 🧪 Practice Questions
1. Create a function that toggles a class on click using jQuery
2. Create a function that adds different classes based on conditions
3. Create a function that creates a tabbed interface using classes

## 5. val()

### 🧠 Theory
- Gets or sets the value of form elements
- Works with inputs, selects, textareas
- Equivalent to `value` property in vanilla JavaScript
- Handles different form element types automatically

### 🛠️ Sample Code
```html
<input type="text" id="name" placeholder="Enter name">
<select id="country">
    <option value="us">United States</option>
    <option value="uk">United Kingdom</option>
</select>
<script>
    // DOM Version
    const nameInput = document.getElementById('name');
    const countrySelect = document.getElementById('country');
    console.log(nameInput.value);
    nameInput.value = 'John Doe';
    countrySelect.value = 'uk';
    
    // jQuery Version
    console.log($('#name').val());
    $('#name').val('John Doe');
    $('#country').val('uk');
</script>
```

### 🔍 Explanation
- `val()`: gets the current value
- `val(value)`: sets new value
- Works with all form elements
- Handles multiple selections in select elements

### 🔁 Practical Examples
```javascript
// Example 1: Form data collection
function collectFormData() {
    // DOM Version
    const form = document.getElementById('myForm');
    const formData = new FormData(form);
    const data = {};
    for (let [key, value] of formData.entries()) {
        data[key] = value;
    }
    
    // jQuery Version
    const data = {};
    $('#myForm input, #myForm select, #myForm textarea').each(function() {
        const $this = $(this);
        data[$this.attr('name')] = $this.val();
    });
}

// Example 2: Real-time validation
function setupRealTimeValidation() {
    // jQuery Version
    $('#email').on('input', function() {
        const $this = $(this);
        const email = $this.val();
        const isValid = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
        
        $this.toggleClass('valid', isValid);
        $this.toggleClass('invalid', !isValid);
    });
}

// Example 3: Form reset
function resetForm() {
    // DOM Version
    const inputs = document.querySelectorAll('input, select, textarea');
    inputs.forEach(input => {
        input.value = '';
    });
    
    // jQuery Version
    $('input, select, textarea').val('');
}
```

### 🧪 Practice Questions
1. Create a function that validates form inputs using jQuery
2. Create a function that calculates totals from numeric inputs
3. Create a function that saves form data to localStorage using jQuery

## 6. Dimension Methods

### 🧠 Theory
- `width()`, `height()`: content dimensions
- `innerWidth()`, `innerHeight()`: including padding
- `outerWidth()`, `outerHeight()`: including border
- Much easier than calculating dimensions manually

### 🛠️ Sample Code
```html
<div id="box" style="width: 200px; height: 100px; padding: 10px; border: 2px solid black;">Content</div>
<script>
    // DOM Version
    const box = document.getElementById('box');
    console.log(box.offsetWidth);  // Total width
    console.log(box.clientWidth);  // Width + padding
    
    // jQuery Version
    console.log($('#box').width());      // 200px (content only)
    console.log($('#box').innerWidth()); // 220px (content + padding)
    console.log($('#box').outerWidth()); // 224px (content + padding + border)
</script>
```

### 🔍 Explanation
- Different methods for different dimension needs
- Can get or set dimensions
- Handles box model calculations automatically
- Much cleaner than vanilla JavaScript

### 🔁 Practical Examples
```javascript
// Example 1: Responsive layout
function makeResponsive() {
    // jQuery Version
    $(window).on('resize', function() {
        const windowWidth = $(window).width();
        if (windowWidth < 768) {
            $('.sidebar').hide();
            $('.content').css('width', '100%');
        } else {
            $('.sidebar').show();
            $('.content').css('width', '70%');
        }
    });
}

// Example 2: Center element
function centerElement() {
    // jQuery Version
    const $element = $('.modal');
    const windowWidth = $(window).width();
    const windowHeight = $(window).height();
    const elementWidth = $element.outerWidth();
    const elementHeight = $element.outerHeight();
    
    $element.css({
        'position': 'fixed',
        'left': (windowWidth - elementWidth) / 2,
        'top': (windowHeight - elementHeight) / 2
    });
}
```

### 🧪 Practice Questions
1. Create a function that makes elements equal height using jQuery
2. Create a function that creates a responsive grid system
3. Create a function that centers elements dynamically

## 🎯 Comparison Summary

| Task | DOM | jQuery |
|------|-----|--------|
| Set HTML | `element.innerHTML = 'html'` | `element.html('html')` |
| Set text | `element.textContent = 'text'` | `element.text('text')` |
| Set style | `element.style.color = 'red'` | `element.css('color', 'red')` |
| Add class | `element.classList.add('class')` | `element.addClass('class')` |
| Remove class | `element.classList.remove('class')` | `element.removeClass('class')` |
| Toggle class | `element.classList.toggle('class')` | `element.toggleClass('class')` |
| Get value | `element.value` | `element.val()` |
| Set value | `element.value = 'value'` | `element.val('value')` |

## 🎯 Next Steps
- Learn about jQuery events
- Practice chaining multiple property changes
- Try creating interactive interfaces
- Learn about jQuery animations

Remember: jQuery properties make everything much more intuitive and require less code than vanilla JavaScript!

---
*© 2025 CodingNest. All rights reserved.* 
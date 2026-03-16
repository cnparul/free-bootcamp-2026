<p align="center">
  <img src="https://ik.imagekit.io/codingnest/codingnestfinal_bg.svg?updatedAt=1714659978004" alt="CodingNest Logo" width="300"/>
</p>

Welcome to CodingNest's beginner-friendly guide to DOM Forms! This guide will help you understand how to work with forms and user input on web pages using JavaScript.

# 📝 DOM Forms in JavaScript

## 1. Form Elements

### 🧠 Theory
- Forms are used to collect user input
- Common form elements: input, select, textarea
- Form elements can be accessed using DOM methods
- Form data can be validated and processed

### 🛠️ Sample Code
```html
<form id="myForm">
    <input type="text" id="username" name="username">
    <select id="country" name="country">
        <option value="us">United States</option>
        <option value="uk">United Kingdom</option>
    </select>
    <textarea id="message" name="message"></textarea>
    <button type="submit">Submit</button>
</form>
<script>
    const form = document.getElementById('myForm');
    const username = document.getElementById('username');
    const country = document.getElementById('country');
    const message = document.getElementById('message');
</script>
```

### 🔍 Explanation
- Form elements can be accessed by ID or name
- Each element has specific properties and methods
- Form data can be collected using FormData API
- Form submission can be handled with JavaScript

### 🔁 Practical Examples
```javascript
// Example 1: Get form data
function getFormData(form) {
    const formData = new FormData(form);
    const data = {};
    for (let [key, value] of formData.entries()) {
        data[key] = value;
    }
    return data;
}

// Example 2: Form validation
function validateForm(form) {
    const inputs = form.querySelectorAll('input[required]');
    let isValid = true;
    inputs.forEach(input => {
        if (!input.value.trim()) {
            isValid = false;
            input.classList.add('error');
        } else {
            input.classList.remove('error');
        }
    });
    return isValid;
}

// Example 3: Dynamic form field
function addFormField(form, type, name) {
    const input = document.createElement('input');
    input.type = type;
    input.name = name;
    form.appendChild(input);
}
```

### 🧪 Practice Questions
1. Create a function that validates email format
2. Implement a function that adds/removes form fields dynamically
3. Create a function that saves form data to localStorage

## 2. Form Events

### 🧠 Theory
- Forms have specific events: submit, change, input
- Events can be used to validate and process data
- Form submission can be prevented
- Events can be used to provide real-time feedback

### 🛠️ Sample Code
```html
<form id="myForm">
    <input type="text" id="name" required>
    <input type="email" id="email" required>
    <button type="submit">Submit</button>
</form>
<script>
    const form = document.getElementById('myForm');
    form.addEventListener('submit', (e) => {
        e.preventDefault();
        // Handle form submission
    });
</script>
```

### 🔍 Explanation
- submit: triggered when form is submitted
- change: triggered when input value changes
- input: triggered on every input change
- Events can be used for validation

### 🔁 Practical Examples
```javascript
// Example 1: Form submission handler
function handleSubmit(event) {
    event.preventDefault();
    const formData = new FormData(event.target);
    console.log('Form submitted:', Object.fromEntries(formData));
}

// Example 2: Real-time validation
function setupRealTimeValidation(input) {
    input.addEventListener('input', (e) => {
        const value = e.target.value;
        if (value.length < 3) {
            e.target.classList.add('error');
        } else {
            e.target.classList.remove('error');
        }
    });
}

// Example 3: Form reset handler
function handleFormReset(form) {
    form.addEventListener('reset', () => {
        form.querySelectorAll('.error').forEach(el => {
            el.classList.remove('error');
        });
    });
}
```

### 🧪 Practice Questions
1. Create a function that validates form fields on input
2. Implement a function that shows password strength
3. Create a function that handles form reset

## 3. Form Validation

### 🧠 Theory
- Form validation ensures data quality
- Can be done on client and server side
- HTML5 provides built-in validation
- Custom validation can be added

### 🛠️ Sample Code
```html
<form id="myForm">
    <input type="text" required minlength="3">
    <input type="email" required pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$">
    <input type="number" min="0" max="100">
    <button type="submit">Submit</button>
</form>
```

### 🔍 Explanation
- required: field must be filled
- pattern: field must match regex
- min/max: numeric limits
- Custom validation with JavaScript

### 🔁 Practical Examples
```javascript
// Example 1: Custom validation
function validateField(field) {
    const value = field.value;
    const type = field.type;
    let isValid = true;
    
    switch(type) {
        case 'email':
            isValid = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value);
            break;
        case 'number':
            isValid = !isNaN(value) && value >= 0 && value <= 100;
            break;
        case 'text':
            isValid = value.length >= 3;
            break;
    }
    
    return isValid;
}

// Example 2: Form validation with custom messages
function validateFormWithMessages(form) {
    const errors = [];
    form.querySelectorAll('input').forEach(input => {
        if (!validateField(input)) {
            errors.push(`${input.name} is invalid`);
        }
    });
    return errors;
}

// Example 3: Password strength validation
function validatePassword(password) {
    const hasUpperCase = /[A-Z]/.test(password);
    const hasLowerCase = /[a-z]/.test(password);
    const hasNumbers = /\d/.test(password);
    const hasSpecialChar = /[!@#$%^&*]/.test(password);
    
    return {
        isValid: hasUpperCase && hasLowerCase && hasNumbers && hasSpecialChar,
        strength: [hasUpperCase, hasLowerCase, hasNumbers, hasSpecialChar]
            .filter(Boolean).length
    };
}
```

### 🧪 Practice Questions
1. Create a function that validates phone numbers
2. Implement a function that checks password strength
3. Create a function that validates date inputs

## 4. Form Data Handling

### 🧠 Theory
- FormData API for handling form data
- Can be used to send data to server
- Supports file uploads
- Can be used with AJAX

### 🛠️ Sample Code
```html
<form id="myForm">
    <input type="text" name="username">
    <input type="file" name="avatar">
    <button type="submit">Submit</button>
</form>
<script>
    const form = document.getElementById('myForm');
    form.addEventListener('submit', async (e) => {
        e.preventDefault();
        const formData = new FormData(form);
        await fetch('/api/submit', {
            method: 'POST',
            body: formData
        });
    });
</script>
```

### 🔍 Explanation
- FormData constructor takes form element
- Can append additional data
- Supports file uploads
- Can be used with fetch API

### 🔁 Practical Examples
```javascript
// Example 1: Form data to JSON
function formDataToJSON(form) {
    const formData = new FormData(form);
    const data = {};
    for (let [key, value] of formData.entries()) {
        data[key] = value;
    }
    return JSON.stringify(data);
}

// Example 2: File upload handling
async function handleFileUpload(form) {
    const formData = new FormData(form);
    const file = formData.get('file');
    
    if (file.size > 5 * 1024 * 1024) {
        throw new Error('File too large');
    }
    
    await fetch('/api/upload', {
        method: 'POST',
        body: formData
    });
}

// Example 3: Form data with progress
function uploadWithProgress(form) {
    const formData = new FormData(form);
    const xhr = new XMLHttpRequest();
    
    xhr.upload.addEventListener('progress', (e) => {
        const percent = (e.loaded / e.total) * 100;
        console.log(`Upload: ${percent}%`);
    });
    
    xhr.open('POST', '/api/upload');
    xhr.send(formData);
}
```

### 🧪 Practice Questions
1. Create a function that handles multiple file uploads
2. Implement a function that shows upload progress
3. Create a function that validates file types

## 5. Form Styling and UX

### 🧠 Theory
- Forms should be user-friendly
- Visual feedback is important
- Accessibility should be considered
- Responsive design is essential

### 🛠️ Sample Code
```html
<form id="myForm" class="form">
    <div class="form-group">
        <label for="name">Name</label>
        <input type="text" id="name" class="form-control">
        <span class="error-message"></span>
    </div>
    <button type="submit" class="btn">Submit</button>
</form>
```

### 🔍 Explanation
- Use semantic HTML
- Add proper labels
- Show validation feedback
- Style for different states

### 🔁 Practical Examples
```javascript
// Example 1: Form field styling
function styleFormField(field) {
    field.addEventListener('focus', () => {
        field.parentElement.classList.add('focused');
    });
    
    field.addEventListener('blur', () => {
        field.parentElement.classList.remove('focused');
        if (!field.value) {
            field.parentElement.classList.add('error');
        }
    });
}

// Example 2: Form accessibility
function makeFormAccessible(form) {
    form.querySelectorAll('input').forEach(input => {
        if (!input.id) {
            input.id = `input-${Math.random().toString(36).substr(2, 9)}`;
        }
        if (!input.getAttribute('aria-label')) {
            const label = input.previousElementSibling;
            if (label && label.tagName === 'LABEL') {
                input.setAttribute('aria-label', label.textContent);
            }
        }
    });
}

// Example 3: Form responsive design
function makeFormResponsive(form) {
    const mediaQuery = window.matchMedia('(max-width: 768px)');
    
    function handleResize(e) {
        if (e.matches) {
            form.classList.add('mobile');
        } else {
            form.classList.remove('mobile');
        }
    }
    
    mediaQuery.addListener(handleResize);
    handleResize(mediaQuery);
}
```

### 🧪 Practice Questions
1. Create a function that adds loading states to form buttons
2. Implement a function that shows success/error messages
3. Create a function that makes forms keyboard accessible 

---
*© 2025 CodingNest. All rights reserved.* 
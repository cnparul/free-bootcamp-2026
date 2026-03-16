<p align="center">
  <img src="https://ik.imagekit.io/codingnest/codingnestfinal_bg.svg?updatedAt=1714659978004" alt="CodingNest Logo" width="300"/>
</p>

Welcome to CodingNest's beginner-friendly guide to DOM Animation! This guide will help you learn how to make your web pages come alive with movement and effects using JavaScript and CSS.

# 🎬 DOM Animation in JavaScript

## 1. CSS Transitions

### 🧠 Theory
- CSS transitions provide smooth property changes
- Properties can be animated over time
- Multiple properties can be transitioned
- Timing functions control animation speed

### 🛠️ Sample Code
```html
<div id="box" class="box">Hover me</div>
<style>
.box {
    width: 100px;
    height: 100px;
    background: blue;
    transition: all 0.3s ease;
}
.box:hover {
    background: red;
    transform: scale(1.2);
}
</style>
```

### 🔍 Explanation
- transition-property: which properties to animate
- transition-duration: how long animation takes
- transition-timing-function: speed curve
- transition-delay: when to start

### 🔁 Practical Examples
```javascript
// Example 1: Add transition
function addTransition(element, properties) {
    element.style.transition = properties
        .map(prop => `${prop} 0.3s ease`)
        .join(', ');
}

// Example 2: Remove transition
function removeTransition(element) {
    element.style.transition = 'none';
}

// Example 3: Toggle transition
function toggleTransition(element, enabled) {
    element.style.transition = enabled ? 'all 0.3s ease' : 'none';
}
```

### 🧪 Practice Questions
1. Create a function that adds transitions to multiple elements
2. Implement a function that changes transition timing
3. Create a function that animates color changes

## 2. CSS Animations

### 🧠 Theory
- CSS animations are more complex than transitions
- Keyframes define animation steps
- Animations can be repeated
- Can be controlled with JavaScript

### 🛠️ Sample Code
```html
<div id="animated" class="animated">Animate me</div>
<style>
@keyframes slide {
    0% { transform: translateX(0); }
    50% { transform: translateX(100px); }
    100% { transform: translateX(0); }
}
.animated {
    animation: slide 2s infinite;
}
</style>
```

### 🔍 Explanation
- @keyframes: defines animation steps
- animation-name: which keyframes to use
- animation-duration: how long it takes
- animation-iteration-count: how many times to repeat

### 🔁 Practical Examples
```javascript
// Example 1: Add animation
function addAnimation(element, name, duration) {
    element.style.animation = `${name} ${duration}s infinite`;
}

// Example 2: Pause animation
function pauseAnimation(element) {
    element.style.animationPlayState = 'paused';
}

// Example 3: Custom keyframes
function createKeyframes(name, steps) {
    const style = document.createElement('style');
    style.textContent = `
        @keyframes ${name} {
            ${steps.map((step, i) => 
                `${i * (100 / (steps.length - 1))}% { ${step} }`
            ).join('\n')}
        }
    `;
    document.head.appendChild(style);
}
```

### 🧪 Practice Questions
1. Create a function that generates keyframes dynamically
2. Implement a function that controls animation speed
3. Create a function that combines multiple animations

## 3. requestAnimationFrame

### 🧠 Theory
- Provides smooth animations
- Syncs with browser's refresh rate
- Better performance than setInterval
- Can be used for complex animations

### 🛠️ Sample Code
```javascript
function animate() {
    const element = document.getElementById('animated');
    let position = 0;
    
    function update() {
        position += 1;
        element.style.transform = `translateX(${position}px)`;
        requestAnimationFrame(update);
    }
    
    requestAnimationFrame(update);
}
```

### 🔍 Explanation
- Called before next repaint
- Returns a timestamp
- Can be cancelled
- Better for performance

### 🔁 Practical Examples
```javascript
// Example 1: Smooth animation
function smoothAnimate(element, property, start, end, duration) {
    const startTime = performance.now();
    
    function update(currentTime) {
        const elapsed = currentTime - startTime;
        const progress = Math.min(elapsed / duration, 1);
        
        const current = start + (end - start) * progress;
        element.style[property] = current;
        
        if (progress < 1) {
            requestAnimationFrame(update);
        }
    }
    
    requestAnimationFrame(update);
}

// Example 2: Parallax effect
function createParallax(element, speed) {
    let lastScroll = window.scrollY;
    
    function update() {
        const currentScroll = window.scrollY;
        const delta = currentScroll - lastScroll;
        element.style.transform = `translateY(${delta * speed}px)`;
        lastScroll = currentScroll;
        requestAnimationFrame(update);
    }
    
    requestAnimationFrame(update);
}

// Example 3: FPS counter
function createFPSCounter() {
    let frameCount = 0;
    let lastTime = performance.now();
    let fps = 0;
    
    function update() {
        frameCount++;
        const currentTime = performance.now();
        
        if (currentTime - lastTime >= 1000) {
            fps = frameCount;
            frameCount = 0;
            lastTime = currentTime;
            console.log(`FPS: ${fps}`);
        }
        
        requestAnimationFrame(update);
    }
    
    requestAnimationFrame(update);
}
```

### 🧪 Practice Questions
1. Create a function that animates multiple properties
2. Implement a function that creates a bouncing effect
3. Create a function that animates along a path

## 4. Web Animations API

### 🧠 Theory
- Modern API for web animations
- More powerful than CSS animations
- Can be controlled with JavaScript
- Better performance

### 🛠️ Sample Code
```javascript
const element = document.getElementById('animated');
const animation = element.animate([
    { transform: 'translateX(0)' },
    { transform: 'translateX(100px)' }
], {
    duration: 1000,
    iterations: Infinity,
    direction: 'alternate'
});
```

### 🔍 Explanation
- KeyframeEffect: defines animation steps
- Animation: controls the animation
- Can be paused, reversed, cancelled
- Supports complex timing

### 🔁 Practical Examples
```javascript
// Example 1: Create animation
function createAnimation(element, keyframes, options) {
    return element.animate(keyframes, {
        duration: 1000,
        iterations: 1,
        ...options
    });
}

// Example 2: Chain animations
function chainAnimations(element, animations) {
    let current = 0;
    
    function playNext() {
        if (current < animations.length) {
            const animation = element.animate(
                animations[current].keyframes,
                animations[current].options
            );
            animation.onfinish = () => {
                current++;
                playNext();
            };
        }
    }
    
    playNext();
}

// Example 3: Timeline
function createTimeline(element, timeline) {
    const animations = timeline.map(({ keyframes, options, delay }) => {
        return new Promise(resolve => {
            setTimeout(() => {
                const animation = element.animate(keyframes, options);
                animation.onfinish = resolve;
            }, delay);
        });
    });
    
    return Promise.all(animations);
}
```

### 🧪 Practice Questions
1. Create a function that combines multiple animations
2. Implement a function that creates a sequence of animations
3. Create a function that controls animation timing

## 5. Performance Optimization

### 🧠 Theory
- Animations can impact performance
- Use transform and opacity
- Avoid layout thrashing
- Use will-change property

### 🛠️ Sample Code
```html
<div id="optimized" class="optimized">Optimized</div>
<style>
.optimized {
    will-change: transform;
    transform: translateZ(0);
}
</style>
```

### 🔍 Explanation
- GPU acceleration
- Reduce repaints
- Batch DOM operations
- Use requestAnimationFrame

### 🔁 Practical Examples
```javascript
// Example 1: Optimize element
function optimizeElement(element) {
    element.style.willChange = 'transform';
    element.style.transform = 'translateZ(0)';
}

// Example 2: Batch updates
function batchUpdates(elements, updates) {
    requestAnimationFrame(() => {
        elements.forEach((element, index) => {
            Object.assign(element.style, updates[index]);
        });
    });
}

// Example 3: Performance monitor
function monitorPerformance(callback) {
    let lastTime = performance.now();
    let frames = 0;
    
    function check() {
        const currentTime = performance.now();
        frames++;
        
        if (currentTime - lastTime >= 1000) {
            const fps = Math.round(frames * 1000 / (currentTime - lastTime));
            callback(fps);
            frames = 0;
            lastTime = currentTime;
        }
        
        requestAnimationFrame(check);
    }
    
    requestAnimationFrame(check);
}
```

### 🧪 Practice Questions
1. Create a function that optimizes multiple animations
2. Implement a function that monitors animation performance
3. Create a function that batches DOM updates 

---
*© 2025 CodingNest. All rights reserved.* 
<p align="center">
  <img src="https://ik.imagekit.io/codingnest/codingnestfinal_bg.svg?updatedAt=1714659978004" alt="CodingNest Logo" width="300"/>
</p>

Welcome to CodingNest's beginner-friendly guide to DOM API Integration! This guide will help you learn how to connect your web pages to external data and services using JavaScript.

# 🔌 DOM API Integration in JavaScript

## 1. Fetch API

### 🧠 Theory
- Modern way to make HTTP requests
- Promise-based API
- Supports various data formats
- Handles CORS and authentication

### 🛠️ Sample Code
```javascript
// Basic fetch request
fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));

// POST request with options
fetch('https://api.example.com/data', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({
        name: 'John',
        age: 30
    })
});
```

### 🔍 Explanation
- fetch(): makes HTTP requests
- Response object methods
- Request options
- Error handling

### 🔁 Practical Examples
```javascript
// Example 1: GET request with error handling
async function fetchData(url) {
    try {
        const response = await fetch(url);
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        return await response.json();
    } catch (error) {
        console.error('Fetch failed:', error);
        throw error;
    }
}

// Example 2: POST request with timeout
async function postData(url, data, timeout = 5000) {
    const controller = new AbortController();
    const timeoutId = setTimeout(() => controller.abort(), timeout);
    
    try {
        const response = await fetch(url, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(data),
            signal: controller.signal
        });
        clearTimeout(timeoutId);
        return await response.json();
    } catch (error) {
        clearTimeout(timeoutId);
        throw error;
    }
}

// Example 3: File upload
async function uploadFile(url, file) {
    const formData = new FormData();
    formData.append('file', file);
    
    try {
        const response = await fetch(url, {
            method: 'POST',
            body: formData
        });
        return await response.json();
    } catch (error) {
        console.error('Upload failed:', error);
        throw error;
    }
}
```

### 🧪 Practice Questions
1. Create a function that handles multiple concurrent requests
2. Implement a function that retries failed requests
3. Create a function that uploads multiple files

## 2. XMLHttpRequest

### 🧠 Theory
- Legacy API for HTTP requests
- Event-based API
- Supports older browsers
- More complex than Fetch API

### 🛠️ Sample Code
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data');
xhr.onload = function() {
    if (xhr.status === 200) {
        console.log(xhr.responseText);
    }
};
xhr.send();
```

### 🔍 Explanation
- open(): configures request
- send(): sends request
- onload: handles response
- onerror: handles errors

### 🔁 Practical Examples
```javascript
// Example 1: GET request
function getData(url) {
    return new Promise((resolve, reject) => {
        const xhr = new XMLHttpRequest();
        xhr.open('GET', url);
        xhr.onload = () => {
            if (xhr.status === 200) {
                resolve(JSON.parse(xhr.responseText));
            } else {
                reject(new Error(`HTTP error! status: ${xhr.status}`));
            }
        };
        xhr.onerror = () => reject(new Error('Network error'));
        xhr.send();
    });
}

// Example 2: POST request
function postData(url, data) {
    return new Promise((resolve, reject) => {
        const xhr = new XMLHttpRequest();
        xhr.open('POST', url);
        xhr.setRequestHeader('Content-Type', 'application/json');
        xhr.onload = () => {
            if (xhr.status === 200) {
                resolve(JSON.parse(xhr.responseText));
            } else {
                reject(new Error(`HTTP error! status: ${xhr.status}`));
            }
        };
        xhr.onerror = () => reject(new Error('Network error'));
        xhr.send(JSON.stringify(data));
    });
}

// Example 3: Progress tracking
function uploadWithProgress(url, file) {
    return new Promise((resolve, reject) => {
        const xhr = new XMLHttpRequest();
        xhr.open('POST', url);
        
        xhr.upload.onprogress = (event) => {
            if (event.lengthComputable) {
                const percent = (event.loaded / event.total) * 100;
                console.log(`Upload: ${percent}%`);
            }
        };
        
        xhr.onload = () => {
            if (xhr.status === 200) {
                resolve(JSON.parse(xhr.responseText));
            } else {
                reject(new Error(`HTTP error! status: ${xhr.status}`));
            }
        };
        
        xhr.onerror = () => reject(new Error('Network error'));
        
        const formData = new FormData();
        formData.append('file', file);
        xhr.send(formData);
    });
}
```

### 🧪 Practice Questions
1. Create a function that handles multiple XHR requests
2. Implement a function that shows upload progress
3. Create a function that cancels ongoing requests

## 3. WebSocket API

### 🧠 Theory
- Real-time bidirectional communication
- Persistent connection
- Low latency
- Event-based API

### 🛠️ Sample Code
```javascript
const ws = new WebSocket('wss://api.example.com/ws');

ws.onopen = () => {
    console.log('Connected');
    ws.send('Hello Server!');
};

ws.onmessage = (event) => {
    console.log('Received:', event.data);
};

ws.onclose = () => {
    console.log('Disconnected');
};
```

### 🔍 Explanation
- WebSocket constructor
- Event handlers
- send() method
- Connection states

### 🔁 Practical Examples
```javascript
// Example 1: WebSocket connection
function createWebSocket(url) {
    return new Promise((resolve, reject) => {
        const ws = new WebSocket(url);
        
        ws.onopen = () => resolve(ws);
        ws.onerror = (error) => reject(error);
        
        return ws;
    });
}

// Example 2: Message handling
function setupWebSocket(url, handlers) {
    const ws = new WebSocket(url);
    
    ws.onopen = handlers.onOpen;
    ws.onmessage = (event) => {
        try {
            const data = JSON.parse(event.data);
            handlers.onMessage(data);
        } catch (error) {
            console.error('Message parsing failed:', error);
        }
    };
    ws.onerror = handlers.onError;
    ws.onclose = handlers.onClose;
    
    return ws;
}

// Example 3: Reconnection
function createReconnectingWebSocket(url, options = {}) {
    const {
        maxRetries = 5,
        retryInterval = 1000
    } = options;
    
    let ws = null;
    let retryCount = 0;
    
    function connect() {
        ws = new WebSocket(url);
        
        ws.onopen = () => {
            retryCount = 0;
            console.log('Connected');
        };
        
        ws.onclose = () => {
            if (retryCount < maxRetries) {
                retryCount++;
                setTimeout(connect, retryInterval);
            }
        };
    }
    
    connect();
    return ws;
}
```

### 🧪 Practice Questions
1. Create a function that handles WebSocket reconnection
2. Implement a function that manages multiple WebSocket connections
3. Create a function that handles WebSocket message queuing

## 4. Server-Sent Events

### 🧠 Theory
- One-way server to client communication
- Uses HTTP protocol
- Automatic reconnection
- Simple to implement

### 🛠️ Sample Code
```javascript
const evtSource = new EventSource('https://api.example.com/events');

evtSource.onmessage = (event) => {
    console.log('Received:', event.data);
};

evtSource.onerror = (error) => {
    console.error('EventSource failed:', error);
};
```

### 🔍 Explanation
- EventSource constructor
- Event types
- Connection handling
- Error handling

### 🔁 Practical Examples
```javascript
// Example 1: Basic SSE connection
function createEventSource(url) {
    return new Promise((resolve, reject) => {
        const evtSource = new EventSource(url);
        
        evtSource.onopen = () => resolve(evtSource);
        evtSource.onerror = (error) => reject(error);
        
        return evtSource;
    });
}

// Example 2: Custom event handling
function setupEventSource(url, handlers) {
    const evtSource = new EventSource(url);
    
    evtSource.onmessage = (event) => {
        try {
            const data = JSON.parse(event.data);
            handlers.onMessage(data);
        } catch (error) {
            console.error('Message parsing failed:', error);
        }
    };
    
    evtSource.onerror = handlers.onError;
    
    return evtSource;
}

// Example 3: Reconnection handling
function createReconnectingEventSource(url, options = {}) {
    const {
        maxRetries = 5,
        retryInterval = 1000
    } = options;
    
    let evtSource = null;
    let retryCount = 0;
    
    function connect() {
        evtSource = new EventSource(url);
        
        evtSource.onopen = () => {
            retryCount = 0;
            console.log('Connected');
        };
        
        evtSource.onerror = () => {
            if (retryCount < maxRetries) {
                retryCount++;
                setTimeout(connect, retryInterval);
            }
        };
    }
    
    connect();
    return evtSource;
}
```

### 🧪 Practice Questions
1. Create a function that handles SSE reconnection
2. Implement a function that processes different event types
3. Create a function that manages multiple SSE connections

## 5. API Integration Best Practices

### 🧠 Theory
- Error handling
- Security considerations
- Performance optimization
- Cross-browser compatibility

### 🛠️ Sample Code
```javascript
// API client with best practices
class APIClient {
    constructor(baseURL) {
        this.baseURL = baseURL;
        this.defaultHeaders = {
            'Content-Type': 'application/json'
        };
    }
    
    async request(endpoint, options = {}) {
        try {
            const response = await fetch(`${this.baseURL}${endpoint}`, {
                ...options,
                headers: {
                    ...this.defaultHeaders,
                    ...options.headers
                }
            });
            
            if (!response.ok) {
                throw new Error(`HTTP error! status: ${response.status}`);
            }
            
            return await response.json();
        } catch (error) {
            console.error('API request failed:', error);
            throw error;
        }
    }
}
```

### 🔍 Explanation
- Error handling patterns
- Security measures
- Performance tips
- Browser compatibility

### 🔁 Practical Examples
```javascript
// Example 1: API client with retry
class RetryAPIClient {
    constructor(baseURL, options = {}) {
        this.baseURL = baseURL;
        this.maxRetries = options.maxRetries || 3;
        this.retryDelay = options.retryDelay || 1000;
    }
    
    async request(endpoint, options = {}) {
        let lastError;
        
        for (let i = 0; i < this.maxRetries; i++) {
            try {
                const response = await fetch(`${this.baseURL}${endpoint}`, options);
                if (!response.ok) {
                    throw new Error(`HTTP error! status: ${response.status}`);
                }
                return await response.json();
            } catch (error) {
                lastError = error;
                if (i < this.maxRetries - 1) {
                    await new Promise(resolve => 
                        setTimeout(resolve, this.retryDelay * Math.pow(2, i))
                    );
                }
            }
        }
        
        throw lastError;
    }
}

// Example 2: API client with caching
class CachedAPIClient {
    constructor(baseURL) {
        this.baseURL = baseURL;
        this.cache = new Map();
    }
    
    async request(endpoint, options = {}) {
        const cacheKey = `${endpoint}-${JSON.stringify(options)}`;
        
        if (this.cache.has(cacheKey)) {
            const { data, timestamp } = this.cache.get(cacheKey);
            if (Date.now() - timestamp < 5 * 60 * 1000) { // 5 minutes
                return data;
            }
        }
        
        const response = await fetch(`${this.baseURL}${endpoint}`, options);
        const data = await response.json();
        
        this.cache.set(cacheKey, {
            data,
            timestamp: Date.now()
        });
        
        return data;
    }
}

// Example 3: API client with rate limiting
class RateLimitedAPIClient {
    constructor(baseURL, options = {}) {
        this.baseURL = baseURL;
        this.rateLimit = options.rateLimit || 100; // requests per minute
        this.queue = [];
        this.processing = false;
    }
    
    async request(endpoint, options = {}) {
        return new Promise((resolve, reject) => {
            this.queue.push({ endpoint, options, resolve, reject });
            this.processQueue();
        });
    }
    
    async processQueue() {
        if (this.processing) return;
        this.processing = true;
        
        while (this.queue.length > 0) {
            const { endpoint, options, resolve, reject } = this.queue.shift();
            
            try {
                const response = await fetch(`${this.baseURL}${endpoint}`, options);
                const data = await response.json();
                resolve(data);
            } catch (error) {
                reject(error);
            }
            
            await new Promise(resolve => 
                setTimeout(resolve, 60000 / this.rateLimit)
            );
        }
        
        this.processing = false;
    }
}
```

### 🧪 Practice Questions
1. Create a function that implements API request queuing
2. Implement a function that handles API rate limiting
3. Create a function that manages API response caching 

---
*© 2025 CodingNest. All rights reserved.* 
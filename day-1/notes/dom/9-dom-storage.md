<p align="center">
  <img src="https://ik.imagekit.io/codingnest/codingnestfinal_bg.svg?updatedAt=1714659978004" alt="CodingNest Logo" width="300"/>
</p>

Welcome to CodingNest's beginner-friendly guide to DOM Storage! This guide will help you learn how to save and manage data in the browser using JavaScript.

# 💾 DOM Storage in JavaScript

## 1. localStorage

### 🧠 Theory
- Persistent storage in the browser
- Data persists after browser restart
- Limited to 5-10 MB per domain
- Stores data as strings

### 🛠️ Sample Code
```javascript
// Store data
localStorage.setItem('user', JSON.stringify({
    name: 'John',
    age: 30
}));

// Retrieve data
const user = JSON.parse(localStorage.getItem('user'));
console.log(user.name); // "John"
```

### 🔍 Explanation
- setItem(): stores data
- getItem(): retrieves data
- removeItem(): removes data
- clear(): clears all data

### 🔁 Practical Examples
```javascript
// Example 1: Store object
function storeObject(key, value) {
    try {
        localStorage.setItem(key, JSON.stringify(value));
        return true;
    } catch (e) {
        console.error('Storage failed:', e);
        return false;
    }
}

// Example 2: Get object
function getObject(key) {
    try {
        const item = localStorage.getItem(key);
        return item ? JSON.parse(item) : null;
    } catch (e) {
        console.error('Retrieval failed:', e);
        return null;
    }
}

// Example 3: Remove object
function removeObject(key) {
    try {
        localStorage.removeItem(key);
        return true;
    } catch (e) {
        console.error('Removal failed:', e);
        return false;
    }
}
```

### 🧪 Practice Questions
1. Create a function that stores an array of objects
2. Implement a function that updates specific fields
3. Create a function that clears expired data

## 2. sessionStorage

### 🧠 Theory
- Temporary storage for session
- Data cleared when tab closes
- Similar API to localStorage
- Useful for temporary data

### 🛠️ Sample Code
```javascript
// Store session data
sessionStorage.setItem('tempData', JSON.stringify({
    page: 'home',
    timestamp: Date.now()
}));

// Get session data
const tempData = JSON.parse(sessionStorage.getItem('tempData'));
```

### 🔍 Explanation
- Same methods as localStorage
- Data is session-specific
- Cleared on tab close
- Useful for temporary state

### 🔁 Practical Examples
```javascript
// Example 1: Store session state
function storeSessionState(state) {
    try {
        sessionStorage.setItem('appState', JSON.stringify(state));
        return true;
    } catch (e) {
        console.error('Session storage failed:', e);
        return false;
    }
}

// Example 2: Get session state
function getSessionState() {
    try {
        const state = sessionStorage.getItem('appState');
        return state ? JSON.parse(state) : {};
    } catch (e) {
        console.error('Session retrieval failed:', e);
        return {};
    }
}

// Example 3: Clear session state
function clearSessionState() {
    try {
        sessionStorage.clear();
        return true;
    } catch (e) {
        console.error('Session clear failed:', e);
        return false;
    }
}
```

### 🧪 Practice Questions
1. Create a function that stores form data temporarily
2. Implement a function that tracks page views
3. Create a function that manages session timeouts

## 3. IndexedDB

### 🧠 Theory
- Advanced client-side storage
- Supports large amounts of data
- Asynchronous API
- Supports complex queries

### 🛠️ Sample Code
```javascript
const request = indexedDB.open('MyDatabase', 1);

request.onupgradeneeded = (event) => {
    const db = event.target.result;
    const store = db.createObjectStore('users', { keyPath: 'id' });
    store.createIndex('name', 'name', { unique: false });
};

request.onsuccess = (event) => {
    const db = event.target.result;
    const transaction = db.transaction(['users'], 'readwrite');
    const store = transaction.objectStore('users');
    store.add({ id: 1, name: 'John' });
};
```

### 🔍 Explanation
- Open database connection
- Create object stores
- Define indexes
- Handle transactions

### 🔁 Practical Examples
```javascript
// Example 1: Initialize database
function initDatabase(name, version, stores) {
    return new Promise((resolve, reject) => {
        const request = indexedDB.open(name, version);
        
        request.onerror = () => reject(request.error);
        request.onsuccess = () => resolve(request.result);
        
        request.onupgradeneeded = (event) => {
            const db = event.target.result;
            stores.forEach(store => {
                if (!db.objectStoreNames.contains(store.name)) {
                    const objectStore = db.createObjectStore(
                        store.name,
                        { keyPath: store.keyPath }
                    );
                    store.indexes.forEach(index => {
                        objectStore.createIndex(
                            index.name,
                            index.keyPath,
                            { unique: index.unique }
                        );
                    });
                }
            });
        };
    });
}

// Example 2: Add data
function addData(db, storeName, data) {
    return new Promise((resolve, reject) => {
        const transaction = db.transaction([storeName], 'readwrite');
        const store = transaction.objectStore(storeName);
        const request = store.add(data);
        
        request.onsuccess = () => resolve(request.result);
        request.onerror = () => reject(request.error);
    });
}

// Example 3: Query data
function queryData(db, storeName, indexName, value) {
    return new Promise((resolve, reject) => {
        const transaction = db.transaction([storeName], 'readonly');
        const store = transaction.objectStore(storeName);
        const index = store.index(indexName);
        const request = index.getAll(value);
        
        request.onsuccess = () => resolve(request.result);
        request.onerror = () => reject(request.error);
    });
}
```

### 🧪 Practice Questions
1. Create a function that implements CRUD operations
2. Implement a function that handles complex queries
3. Create a function that manages database versioning

## 4. Web SQL (Deprecated)

### 🧠 Theory
- SQL-based storage
- Deprecated but still supported
- Synchronous API
- Limited browser support

### 🛠️ Sample Code
```javascript
const db = openDatabase('MyDB', '1.0', 'My Database', 2 * 1024 * 1024);

db.transaction(function(tx) {
    tx.executeSql('CREATE TABLE IF NOT EXISTS users (id, name)');
    tx.executeSql('INSERT INTO users VALUES (?, ?)', [1, 'John']);
});
```

### 🔍 Explanation
- SQL-based queries
- Transaction-based
- Limited storage
- Not recommended for new projects

### 🔁 Practical Examples
```javascript
// Example 1: Create table
function createTable(db, tableName, columns) {
    return new Promise((resolve, reject) => {
        db.transaction(tx => {
            const query = `CREATE TABLE IF NOT EXISTS ${tableName} (${columns.join(', ')})`;
            tx.executeSql(query, [], resolve, reject);
        });
    });
}

// Example 2: Insert data
function insertData(db, tableName, data) {
    return new Promise((resolve, reject) => {
        db.transaction(tx => {
            const columns = Object.keys(data).join(', ');
            const values = Object.values(data);
            const placeholders = values.map(() => '?').join(', ');
            const query = `INSERT INTO ${tableName} (${columns}) VALUES (${placeholders})`;
            tx.executeSql(query, values, resolve, reject);
        });
    });
}

// Example 3: Query data
function queryData(db, tableName, conditions) {
    return new Promise((resolve, reject) => {
        db.transaction(tx => {
            const whereClause = conditions ? `WHERE ${conditions}` : '';
            const query = `SELECT * FROM ${tableName} ${whereClause}`;
            tx.executeSql(query, [], (tx, results) => {
                resolve(Array.from(results.rows));
            }, reject);
        });
    });
}
```

### 🧪 Practice Questions
1. Create a function that implements basic SQL operations
2. Implement a function that handles database migrations
3. Create a function that manages database connections

## 5. Storage Events

### 🧠 Theory
- Events fired when storage changes
- Works across tabs/windows
- Can sync data between tabs
- Useful for real-time updates

### 🛠️ Sample Code
```javascript
window.addEventListener('storage', (event) => {
    if (event.key === 'user') {
        const user = JSON.parse(event.newValue);
        console.log('User updated:', user);
    }
});
```

### 🔍 Explanation
- storage event properties
- Cross-tab communication
- Event handling
- Data synchronization

### 🔁 Practical Examples
```javascript
// Example 1: Listen for changes
function listenForChanges(callback) {
    window.addEventListener('storage', (event) => {
        callback({
            key: event.key,
            oldValue: event.oldValue,
            newValue: event.newValue,
            url: event.url
        });
    });
}

// Example 2: Sync data
function syncData(key, value) {
    localStorage.setItem(key, JSON.stringify(value));
    window.dispatchEvent(new StorageEvent('storage', {
        key: key,
        oldValue: null,
        newValue: JSON.stringify(value),
        url: window.location.href
    }));
}

// Example 3: Cross-tab communication
function setupCrossTabCommunication(channel) {
    const key = `channel_${channel}`;
    
    function sendMessage(message) {
        const data = {
            timestamp: Date.now(),
            message: message
        };
        localStorage.setItem(key, JSON.stringify(data));
    }
    
    function listenForMessages(callback) {
        window.addEventListener('storage', (event) => {
            if (event.key === key && event.newValue) {
                const data = JSON.parse(event.newValue);
                callback(data.message);
            }
        });
    }
    
    return { sendMessage, listenForMessages };
}
```

### 🧪 Practice Questions
1. Create a function that syncs data between tabs
2. Implement a function that handles storage events
3. Create a function that manages cross-tab communication 

---
*© 2025 CodingNest. All rights reserved.* 
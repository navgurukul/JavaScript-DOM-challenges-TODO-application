# APPENDIX: Advanced JavaScript Topics for React Prerequisites
## Interactive Learning Reference for BCA Third Semester Students

This appendix provides detailed coverage of advanced JavaScript topics encountered throughout the 10-day DOM curriculum. Each topic includes concepts, interview questions, and hands-on VS Code activities to reinforce learning.

---

## **Day 1-2 Topics: Function Expressions & Modern Syntax**

### **1. Arrow Functions (ES6)**
*Referenced in: Day 2 (Element Selection), Day 5 (Event Handling)*

#### Concept
Arrow functions provide a concise syntax for writing functions and have different `this` binding behavior compared to regular functions.

**Key Features:**
• Shorter syntax for function expressions
• Lexical `this` binding (inherits from enclosing scope)
• Cannot be used as constructors
• No `arguments` object

**Use Cases:**
• Event handlers where you need to preserve outer `this`
• Array methods (map, filter, forEach)
• Short callback functions
• Modern React component development

#### Examples
```javascript
// Traditional function
function addNumbers(a, b) {
    return a + b;
}

// Arrow function
const addNumbers = (a, b) => a + b;

// With multiple statements
const processTask = (task) => {
    console.log(`Processing: ${task}`);
    return task.toUpperCase();
};

// Array methods with arrow functions
const tasks = ['learn', 'code', 'build'];
const uppercased = tasks.map(task => task.toUpperCase());
```

#### Interview Questions
1. **What is the main difference between arrow functions and regular functions?**
   - Arrow functions have lexical `this` binding, regular functions have dynamic `this`
   - Arrow functions cannot be used as constructors
   - Arrow functions don't have their own `arguments` object

2. **When should you NOT use arrow functions?**
   - As object methods when you need `this` to refer to the object
   - As event handlers when you need `this` to refer to the element
   - When you need to use `arguments` object

3. **How does `this` behave in arrow functions vs regular functions?**
   - Arrow functions inherit `this` from enclosing lexical scope
   - Regular functions have `this` determined by how they're called

#### Interactive Activity (learn.js)
```javascript
// Create learn.js in VS Code and practice these concepts

// 1. Basic arrow function conversion
console.log('=== Arrow Function Practice ===');

// Convert these regular functions to arrow functions
function multiply(a, b) {
    return a * b;
}

function greetUser(name) {
    return `Hello, ${name}!`;
}

// Your arrow function versions here:
const multiplyArrow = (a, b) => a * b;
const greetUserArrow = name => `Hello, ${name}!`;

// Test them
console.log('Regular multiply:', multiply(3, 4));
console.log('Arrow multiply:', multiplyArrow(3, 4));

// 2. Array methods with arrow functions
const numbers = [1, 2, 3, 4, 5];

// Practice: Use arrow functions with these array methods
const doubled = numbers.map(/* your arrow function here */);
const evens = numbers.filter(/* your arrow function here */);
const sum = numbers.reduce(/* your arrow function here */);

console.log('Doubled:', doubled);
console.log('Evens:', evens);
console.log('Sum:', sum);

// 3. this binding practice
const todoApp = {
    tasks: ['Learn JS', 'Build app'],
    
    // Regular function method
    displayTasksRegular: function() {
        console.log('Regular function this:', this);
        this.tasks.forEach(function(task) {
            console.log('Task:', task, 'this inside forEach:', this);
        });
    },
    
    // Arrow function method
    displayTasksArrow: function() {
        console.log('Outer this:', this);
        this.tasks.forEach(task => {
            console.log('Task:', task, 'this inside arrow forEach:', this);
        });
    }
};

// Test both methods and observe the difference
todoApp.displayTasksRegular();
todoApp.displayTasksArrow();
```

---

### **2. Template Literals (ES6)**
*Referenced in: Day 3 (Creating Elements), Day 8 (Dynamic Content)*

#### Concept
Template literals provide an easy way to create strings with embedded expressions and multi-line strings.

**Key Features:**
• Use backticks (`) instead of quotes
• Embed expressions with ${expression}
• Support multi-line strings
• Tagged template literals for advanced processing

**Use Cases:**
• Dynamic HTML generation
• SQL query building
• Multi-line string creation
• Internationalization and localization

#### Examples
```javascript
// Basic template literal
const name = 'Alice';
const message = `Hello, ${name}! Welcome to our app.`;

// Multi-line strings
const htmlTemplate = `
    <div class="user-card">
        <h2>${name}</h2>
        <p>Status: Active</p>
    </div>
`;

// Expression evaluation
const a = 5, b = 10;
const result = `The sum of ${a} and ${b} is ${a + b}`;

// Function calls in templates
const formatDate = (date) => date.toLocaleDateString();
const dateString = `Today is ${formatDate(new Date())}`;
```

#### Interview Questions
1. **What are the advantages of template literals over string concatenation?**
   - More readable syntax for complex strings
   - Support for multi-line strings
   - Expression evaluation inside strings
   - No need for escape characters in most cases

2. **How do template literals help with XSS prevention?**
   - They don't automatically prevent XSS - still need to sanitize user input
   - But they make it easier to see what's being interpolated

3. **What are tagged template literals?**
   - Functions that process template literals
   - Allow custom string processing logic
   - Used in libraries like styled-components

#### Interactive Activity (learn.js)
```javascript
// Add to learn.js file

console.log('\n=== Template Literals Practice ===');

// 1. Basic interpolation
const user = {
    name: 'John Doe',
    age: 25,
    role: 'Developer'
};

// Create a user profile string using template literals
const userProfile = `Name: ${user.name}, Age: ${user.age}, Role: ${user.role}`;
console.log(userProfile);

// 2. Multi-line HTML template
const createTaskHTML = (taskId, taskText, isCompleted) => {
    return `
        <li class="task-item ${isCompleted ? 'completed' : ''}" data-id="${taskId}">
            <span class="task-text">${taskText}</span>
            <button class="delete-btn">Delete</button>
            <button class="edit-btn">Edit</button>
        </li>
    `;
};

// Test the function
console.log(createTaskHTML(1, 'Learn JavaScript', false));
console.log(createTaskHTML(2, 'Build TODO app', true));

// 3. Complex expressions in templates
const tasks = ['Learn', 'Practice', 'Build'];
const taskSummary = `
    Total tasks: ${tasks.length}
    Tasks: ${tasks.join(', ')}
    Average length: ${tasks.reduce((sum, task) => sum + task.length, 0) / tasks.length}
`;
console.log(taskSummary);

// 4. Conditional rendering with templates
const createWelcomeMessage = (user, isLoggedIn) => {
    return `
        <div class="welcome">
            ${isLoggedIn 
                ? `Welcome back, ${user.name}!` 
                : 'Please log in to continue'
            }
        </div>
    `;
};

console.log(createWelcomeMessage(user, true));
console.log(createWelcomeMessage(user, false));
```

---

## **Day 5-7 Topics: Advanced Event Handling Concepts**

### **3. Callback Functions**
*Referenced in: Day 5 (Event Handling), Day 7 (Advanced Events)*

#### Concept
Callback functions are functions passed as arguments to other functions, allowing for asynchronous operations and event-driven programming.

**Key Features:**
• Functions as first-class citizens in JavaScript
• Enable asynchronous programming patterns
• Foundation for Promises and async/await
• Essential for event handling and array methods

**Use Cases:**
• Event handlers (click, input, submit)
• Array iteration methods (forEach, map, filter)
• Asynchronous operations (setTimeout, API calls)
• Higher-order function patterns

#### Examples
```javascript
// Simple callback example
function processData(data, callback) {
    console.log('Processing:', data);
    callback(data.toUpperCase());
}

function displayResult(result) {
    console.log('Result:', result);
}

processData('hello world', displayResult);

// Array methods with callbacks
const numbers = [1, 2, 3, 4, 5];
numbers.forEach(function(number, index) {
    console.log(`Index ${index}: ${number}`);
});

// Event handling callbacks
document.addEventListener('click', function(event) {
    console.log('Clicked:', event.target);
});
```

#### Interview Questions
1. **What is a callback function?**
   - A function passed as an argument to another function
   - Executed at a specific time or when a condition is met
   - Enables asynchronous and event-driven programming

2. **What is callback hell and how can it be avoided?**
   - Deeply nested callback functions that are hard to read
   - Can be avoided using Promises, async/await, or named functions

3. **Explain the difference between synchronous and asynchronous callbacks.**
   - Synchronous: Execute immediately (like Array.map)
   - Asynchronous: Execute later (like setTimeout, event handlers)

#### Interactive Activity (learn.js)
```javascript
// Add to learn.js file

console.log('\n=== Callback Functions Practice ===');

// 1. Basic callback pattern
function executeOperation(a, b, operation) {
    return operation(a, b);
}

function add(x, y) { return x + y; }
function multiply(x, y) { return x * y; }

// Test different operations
console.log('Add:', executeOperation(5, 3, add));
console.log('Multiply:', executeOperation(5, 3, multiply));

// Using anonymous functions as callbacks
console.log('Subtract:', executeOperation(10, 4, function(a, b) { return a - b; }));

// 2. Array iteration with callbacks
const taskList = ['Learn callbacks', 'Practice DOM', 'Build project'];

// Custom forEach implementation
function customForEach(array, callback) {
    for (let i = 0; i < array.length; i++) {
        callback(array[i], i, array);
    }
}

customForEach(taskList, function(task, index) {
    console.log(`Task ${index + 1}: ${task}`);
});

// 3. Async callback simulation
function simulateAsyncOperation(data, callback) {
    console.log('Starting async operation...');
    setTimeout(function() {
        const result = data.toUpperCase();
        callback(null, result); // Node.js style: error-first callback
    }, 1000);
}

simulateAsyncOperation('hello async', function(error, result) {
    if (error) {
        console.error('Error:', error);
    } else {
        console.log('Async result:', result);
    }
});

// 4. Event handler callbacks practice
// Simulate DOM event handling with callbacks
function simulateEventSystem() {
    const eventHandlers = {};
    
    function addEventListener(event, callback) {
        if (!eventHandlers[event]) {
            eventHandlers[event] = [];
        }
        eventHandlers[event].push(callback);
    }
    
    function triggerEvent(event, data) {
        if (eventHandlers[event]) {
            eventHandlers[event].forEach(callback => callback(data));
        }
    }
    
    // Add some event handlers
    addEventListener('taskAdded', function(taskData) {
        console.log('Handler 1: Task added:', taskData.name);
    });
    
    addEventListener('taskAdded', function(taskData) {
        console.log('Handler 2: Updating UI for task:', taskData.name);
    });
    
    // Trigger the event
    triggerEvent('taskAdded', { name: 'Learn React', completed: false });
}

simulateEventSystem();
```

---

### **4. Event Lifecycle & Event Loop**
*Referenced in: Day 7 (Advanced Event Concepts), Day 9 (Performance)*

#### Concept
Understanding how JavaScript handles events through the event loop and call stack is crucial for writing efficient applications.

**Key Features:**
• Call stack for function execution
• Web APIs for asynchronous operations
• Callback queue for pending callbacks
• Event loop coordinating execution

**Use Cases:**
• Optimizing performance in event-heavy applications
• Understanding timing issues in async code
• Debugging complex event interactions
• Planning efficient DOM updates

#### Examples
```javascript
// Event loop demonstration
console.log('1: Start');

setTimeout(() => console.log('2: Timeout'), 0);

Promise.resolve().then(() => console.log('3: Promise'));

console.log('4: End');

// Output order: 1, 4, 3, 2 (microtasks before macrotasks)

// Event phases demonstration
document.addEventListener('click', () => console.log('Bubble'), false);
document.addEventListener('click', () => console.log('Capture'), true);
// Click order: Capture -> Bubble
```

#### Interview Questions
1. **Explain the JavaScript event loop.**
   - Single-threaded execution with call stack
   - Web APIs handle async operations
   - Event loop moves callbacks from queue to stack

2. **What's the difference between microtasks and macrotasks?**
   - Microtasks: Promises, queueMicrotask (higher priority)
   - Macrotasks: setTimeout, setInterval, DOM events

3. **How do you optimize event handling performance?**
   - Use event delegation
   - Debounce/throttle frequent events
   - Use passive listeners for scroll events

#### Interactive Activity (learn.js)
```javascript
// Add to learn.js file

console.log('\n=== Event Lifecycle Practice ===');

// 1. Event loop timing
console.log('=== Event Loop Timing ===');
console.log('1: Synchronous start');

setTimeout(() => console.log('2: setTimeout (macrotask)'), 0);

Promise.resolve().then(() => {
    console.log('3: Promise (microtask)');
    return Promise.resolve();
}).then(() => {
    console.log('4: Chained Promise (microtask)');
});

queueMicrotask(() => console.log('5: queueMicrotask'));

console.log('6: Synchronous end');

// 2. Simulating event phases
function simulateEventPhases() {
    const events = [];
    
    // Simulate capture phase
    function capturePhase(eventName) {
        events.push(`Capture: ${eventName}`);
    }
    
    // Simulate bubble phase
    function bubblePhase(eventName) {
        events.push(`Bubble: ${eventName}`);
    }
    
    // Simulate event dispatch
    function dispatchEvent(eventName) {
        events.length = 0; // Clear previous events
        
        // Capture phase (parent to child)
        capturePhase(eventName);
        
        // Target phase
        events.push(`Target: ${eventName}`);
        
        // Bubble phase (child to parent)
        bubblePhase(eventName);
        
        console.log('Event phases:', events);
    }
    
    dispatchEvent('click');
}

setTimeout(simulateEventPhases, 100);

// 3. Performance timing simulation
function performanceDemo() {
    console.log('\n=== Performance Timing ===');
    
    const start = performance.now();
    
    // Simulate heavy synchronous work
    function heavyWork() {
        let result = 0;
        for (let i = 0; i < 1000000; i++) {
            result += Math.random();
        }
        return result;
    }
    
    // Blocking operation
    console.log('Heavy work result:', heavyWork());
    console.log('Time taken:', performance.now() - start, 'ms');
    
    // Non-blocking alternative
    function heavyWorkAsync(callback) {
        setTimeout(() => {
            const result = heavyWork();
            callback(result);
        }, 0);
    }
    
    console.log('Starting async heavy work...');
    heavyWorkAsync((result) => {
        console.log('Async heavy work result:', result);
        console.log('Total time:', performance.now() - start, 'ms');
    });
    
    console.log('This runs immediately after scheduling async work');
}

setTimeout(performanceDemo, 200);
```

---

## **Day 8-10 Topics: Modern JavaScript & React Preparation**

### **5. Destructuring Assignment (ES6)**
*Referenced in: Day 8 (Dynamic Content), Day 10 (React Preparation)*

#### Concept
Destructuring allows extracting values from arrays or properties from objects into distinct variables.

**Key Features:**
• Extract multiple values in one statement
• Set default values for undefined properties
• Rename variables during extraction
• Nested destructuring for complex objects

**Use Cases:**
• Function parameters (especially in React)
• API response handling
• State management
• Array and object manipulation

#### Examples
```javascript
// Array destructuring
const colors = ['red', 'green', 'blue'];
const [primary, secondary, tertiary] = colors;

// Object destructuring
const user = { name: 'Alice', age: 30, city: 'NYC' };
const { name, age } = user;

// With default values
const { country = 'USA' } = user;

// Renaming variables
const { name: userName, age: userAge } = user;

// Function parameters
function createUser({ name, email, role = 'user' }) {
    return { name, email, role, id: Date.now() };
}
```

#### Interview Questions
1. **What is destructuring and why is it useful?**
   - Syntax for extracting values from arrays/objects
   - Makes code more readable and concise
   - Reduces repetitive property access

2. **How do you handle undefined values in destructuring?**
   - Use default values: `const { name = 'Anonymous' } = user`
   - Check for existence before destructuring

3. **Can you destructure nested objects?**
   - Yes: `const { address: { city } } = user`
   - Useful for complex API responses

#### Interactive Activity (learn.js)
```javascript
// Add to learn.js file

console.log('\n=== Destructuring Practice ===');

// 1. Array destructuring
const todoItems = [
    { id: 1, text: 'Learn JavaScript', completed: false },
    { id: 2, text: 'Build TODO app', completed: true },
    { id: 3, text: 'Deploy project', completed: false }
];

// Extract first and second items
const [firstTodo, secondTodo, ...remainingTodos] = todoItems;
console.log('First todo:', firstTodo.text);
console.log('Second todo:', secondTodo.text);
console.log('Remaining todos:', remainingTodos.length);

// 2. Object destructuring with nested objects
const userProfile = {
    id: 1,
    name: 'John Doe',
    email: 'john@example.com',
    preferences: {
        theme: 'dark',
        notifications: true,
        language: 'en'
    },
    stats: {
        tasksCompleted: 25,
        tasksTotal: 30
    }
};

// Extract nested properties
const { 
    name, 
    email, 
    preferences: { theme, notifications },
    stats: { tasksCompleted, tasksTotal }
} = userProfile;

console.log(`User: ${name} (${email})`);
console.log(`Theme: ${theme}, Notifications: ${notifications}`);
console.log(`Progress: ${tasksCompleted}/${tasksTotal}`);

// 3. Function parameter destructuring
function createTaskSummary({ tasks = [], user = null, filters = {} }) {
    const { completed = false, priority = 'all' } = filters;
    
    let filteredTasks = tasks;
    if (completed !== 'all') {
        filteredTasks = tasks.filter(task => task.completed === completed);
    }
    
    return {
        user: user?.name || 'Anonymous',
        totalTasks: filteredTasks.length,
        filters: { completed, priority }
    };
}

// Test the function
const summary = createTaskSummary({
    tasks: todoItems,
    user: { name: 'Alice' },
    filters: { completed: false }
});

console.log('Task summary:', summary);

// 4. Destructuring in array methods
const taskTexts = todoItems.map(({ text, completed }) => 
    completed ? `✓ ${text}` : `• ${text}`
);

console.log('Formatted tasks:', taskTexts);

// 5. Swapping variables with destructuring
let a = 1, b = 2;
console.log('Before swap:', { a, b });
[a, b] = [b, a];
console.log('After swap:', { a, b });
```

---

### **6. Spread and Rest Operators (ES6)**
*Referenced in: Day 8 (Dynamic Content), Day 9 (Modern Practices)*

#### Concept
The spread (...) operator expands iterables, while the rest operator collects multiple elements into an array.

**Key Features:**
• Spread: Expands arrays/objects into individual elements
• Rest: Collects multiple elements into an array
• Same syntax (...) but different contexts
• Immutable operations (doesn't modify original)

**Use Cases:**
• Array concatenation and copying
• Object merging and copying
• Function parameters
• React state updates (immutable patterns)

#### Examples
```javascript
// Spread with arrays
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]

// Spread with objects
const user = { name: 'Alice', age: 30 };
const updatedUser = { ...user, age: 31 }; // { name: 'Alice', age: 31 }

// Rest parameters
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}
sum(1, 2, 3, 4); // 10

// Rest in destructuring
const [first, ...others] = [1, 2, 3, 4]; // first = 1, others = [2, 3, 4]
```

#### Interview Questions
1. **What's the difference between spread and rest operators?**
   - Spread: Expands/unpacks elements (right side of assignment)
   - Rest: Collects/packs elements (left side of assignment)

2. **How does spread help with immutability?**
   - Creates new arrays/objects instead of modifying existing ones
   - Essential for React state management

3. **Can you use spread with strings?**
   - Yes: `[...'hello']` becomes `['h', 'e', 'l', 'l', 'o']`

#### Interactive Activity (learn.js)
```javascript
// Add to learn.js file

console.log('\n=== Spread and Rest Operators Practice ===');

// 1. Array operations with spread
const originalTasks = ['Task 1', 'Task 2', 'Task 3'];
const newTasks = ['Task 4', 'Task 5'];

// Combining arrays
const allTasks = [...originalTasks, ...newTasks];
console.log('Combined tasks:', allTasks);

// Adding elements to array
const tasksWithNew = [...originalTasks, 'New Task'];
console.log('Tasks with new item:', tasksWithNew);

// Copying array
const tasksCopy = [...originalTasks];
tasksCopy.push('Modified');
console.log('Original:', originalTasks);
console.log('Copy:', tasksCopy);

// 2. Object operations with spread
const baseTask = {
    id: 1,
    text: 'Learn JavaScript',
    priority: 'high'
};

// Adding properties
const taskWithTimestamp = {
    ...baseTask,
    createdAt: new Date(),
    completed: false
};

// Updating properties
const completedTask = {
    ...baseTask,
    completed: true,
    completedAt: new Date()
};

console.log('Base task:', baseTask);
console.log('Task with timestamp:', taskWithTimestamp);
console.log('Completed task:', completedTask);

// 3. Rest parameters in functions
function logTaskDetails(id, text, ...extraInfo) {
    console.log(`Task ${id}: ${text}`);
    if (extraInfo.length > 0) {
        console.log('Extra info:', extraInfo);
    }
}

logTaskDetails(1, 'Learn React');
logTaskDetails(2, 'Build App', 'high priority', 'due tomorrow');

// 4. Rest in destructuring
const taskData = {
    id: 1,
    text: 'Complete project',
    priority: 'high',
    tags: ['work', 'important'],
    assignee: 'Alice',
    dueDate: '2024-12-31'
};

// Extract specific properties, collect rest
const { id, text, ...metadata } = taskData;
console.log('Essential:', { id, text });
console.log('Metadata:', metadata);

// Array rest destructuring
const scores = [95, 87, 92, 78, 85];
const [highest, second, ...otherScores] = scores;
console.log('Top scores:', { highest, second });
console.log('Other scores:', otherScores);

// 5. Practical example: Immutable state updates
let appState = {
    user: { name: 'Alice', id: 1 },
    tasks: [
        { id: 1, text: 'Task 1', completed: false },
        { id: 2, text: 'Task 2', completed: true }
    ],
    filters: { showCompleted: true }
};

// Adding a new task (immutable)
function addTask(state, newTask) {
    return {
        ...state,
        tasks: [...state.tasks, newTask]
    };
}

// Updating a task (immutable)
function updateTask(state, taskId, updates) {
    return {
        ...state,
        tasks: state.tasks.map(task => 
            task.id === taskId ? { ...task, ...updates } : task
        )
    };
}

// Test immutable updates
const newTask = { id: 3, text: 'New Task', completed: false };
const stateWithNewTask = addTask(appState, newTask);

const stateWithUpdatedTask = updateTask(stateWithNewTask, 1, { completed: true });

console.log('Original state:', appState);
console.log('State with new task:', stateWithNewTask);
console.log('State with updated task:', stateWithUpdatedTask);
```

---

### **7. JSX Fundamentals**
*Referenced in: Day 10 (React Preparation)*

#### Concept
JSX is a syntax extension for JavaScript that allows writing HTML-like syntax in JavaScript files, primarily used with React.

**Key Features:**
• HTML-like syntax in JavaScript
• Transpiled to React.createElement() calls
• JavaScript expressions in curly braces {}
• Component composition and props passing

**Use Cases:**
• React component development
• Declarative UI description
• Dynamic content rendering
• Component-based architecture

#### Examples
```javascript
// Basic JSX
const element = <h1>Hello, World!</h1>;

// JSX with expressions
const name = 'Alice';
const greeting = <h1>Hello, {name}!</h1>;

// JSX with components
function TaskItem({ task, onDelete }) {
    return (
        <li className="task-item">
            <span>{task.text}</span>
            <button onClick={() => onDelete(task.id)}>Delete</button>
        </li>
    );
}

// JSX with conditional rendering
const TaskList = ({ tasks, showCompleted }) => (
    <ul>
        {tasks
            .filter(task => showCompleted || !task.completed)
            .map(task => <TaskItem key={task.id} task={task} />)
        }
    </ul>
);
```

#### Interview Questions
1. **What is JSX and how does it work?**
   - Syntax extension for JavaScript allowing HTML-like syntax
   - Transpiled to React.createElement() function calls
   - Not required for React but commonly used

2. **What are the rules for JSX?**
   - Must return single parent element or Fragment
   - Use className instead of class
   - Self-closing tags must end with />
   - JavaScript expressions in curly braces

3. **How do you handle events in JSX?**
   - Use camelCase event names (onClick, onChange)
   - Pass function references or arrow functions
   - Event object is automatically passed

#### Interactive Activity (learn.js)
```javascript
// Add to learn.js file

console.log('\n=== JSX Fundamentals Practice ===');

// Note: This is conceptual practice - actual JSX requires transpilation
// We'll simulate JSX patterns with JavaScript

// 1. JSX-like element creation (simulating React.createElement)
function createElement(type, props, ...children) {
    return {
        type,
        props: {
            ...props,
            children: children.length === 1 ? children[0] : children
        }
    };
}

// Simulate JSX: <h1 className="title">Hello, World!</h1>
const element1 = createElement('h1', { className: 'title' }, 'Hello, World!');
console.log('Simulated JSX element:', element1);

// 2. Component-like functions
function TaskItem({ task, onDelete }) {
    return createElement(
        'li',
        { className: 'task-item', key: task.id },
        createElement('span', { className: 'task-text' }, task.text),
        createElement(
            'button',
            { 
                className: 'delete-btn',
                onClick: () => onDelete(task.id)
            },
            'Delete'
        )
    );
}

function TaskList({ tasks, showCompleted = true }) {
    const filteredTasks = tasks.filter(task => 
        showCompleted || !task.completed
    );
    
    return createElement(
        'ul',
        { className: 'task-list' },
        ...filteredTasks.map(task => TaskItem({ 
            task, 
            onDelete: (id) => console.log('Delete task:', id)
        }))
    );
}

// 3. Test the component-like structure
const sampleTasks = [
    { id: 1, text: 'Learn JSX', completed: true },
    { id: 2, text: 'Build React app', completed: false },
    { id: 3, text: 'Deploy project', completed: false }
];

const taskListElement = TaskList({ 
    tasks: sampleTasks, 
    showCompleted: false 
});

console.log('Task list structure:', JSON.stringify(taskListElement, null, 2));

// 4. Conditional rendering patterns
function ConditionalComponent({ isLoggedIn, user, tasks }) {
    if (!isLoggedIn) {
        return createElement('div', { className: 'login-prompt' }, 'Please log in');
    }
    
    const hasNoTasks = tasks.length === 0;
    
    return createElement(
        'div',
        { className: 'dashboard' },
        createElement('h1', null, `Welcome, ${user.name}!`),
        hasNoTasks 
            ? createElement('p', null, 'No tasks yet. Add your first task!')
            : TaskList({ tasks, showCompleted: true })
    );
}

// Test conditional rendering
const loggedInView = ConditionalComponent({
    isLoggedIn: true,
    user: { name: 'Alice' },
    tasks: sampleTasks
});

const loggedOutView = ConditionalComponent({
    isLoggedIn: false,
    user: null,
    tasks: []
});

console.log('Logged in view:', JSON.stringify(loggedInView, null, 2));
console.log('Logged out view:', JSON.stringify(loggedOutView, null, 2));

// 5. Props handling patterns
function Button({ children, variant = 'primary', size = 'medium', onClick, ...rest }) {
    const className = `btn btn-${variant} btn-${size}`;
    
    return createElement(
        'button',
        {
            className,
            onClick,
            ...rest
        },
        children
    );
}

// Test props patterns
const primaryButton = Button({
    children: 'Add Task',
    variant: 'primary',
    onClick: () => console.log('Add task clicked'),
    'data-testid': 'add-task-btn'
});

const secondaryButton = Button({
    children: 'Cancel',
    variant: 'secondary',
    size: 'small',
    onClick: () => console.log('Cancel clicked')
});

console.log('Primary button:', primaryButton);
console.log('Secondary button:', secondaryButton);
```

---

### **8. React Hooks Fundamentals**
*Referenced in: Day 10 (React Preparation)*

#### Concept
React Hooks are functions that allow you to use state and other React features in functional components.

**Key Features:**
• useState for local component state
• useEffect for side effects and lifecycle
• Custom hooks for reusable logic
• Rules of hooks (only call at top level)

**Use Cases:**
• Managing component state
• API calls and data fetching
• Event listeners and subscriptions
• Form handling and validation

#### Examples
```javascript
// useState hook
function Counter() {
    const [count, setCount] = useState(0);
    
    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}

// useEffect hook
function UserProfile({ userId }) {
    const [user, setUser] = useState(null);
    
    useEffect(() => {
        fetchUser(userId).then(setUser);
    }, [userId]); // Dependency array
    
    if (!user) return <div>Loading...</div>;
    
    return <div>Hello, {user.name}!</div>;
}

// Custom hook
function useTasks() {
    const [tasks, setTasks] = useState([]);
    
    const addTask = (task) => {
        setTasks(prev => [...prev, { ...task, id: Date.now() }]);
    };
    
    const removeTask = (id) => {
        setTasks(prev => prev.filter(task => task.id !== id));
    };
    
    return { tasks, addTask, removeTask };
}
```

#### Interview Questions
1. **What are React Hooks and why were they introduced?**
   - Functions that let you use state and lifecycle features in functional components
   - Introduced to simplify component logic and enable better code reuse

2. **What are the rules of hooks?**
   - Only call hooks at the top level of functions
   - Don't call hooks inside loops, conditions, or nested functions
   - Only call hooks from React functions

3. **What is the dependency array in useEffect?**
   - Second argument that determines when effect runs
   - Empty array [] means run once on mount
   - Values in array mean run when those values change

#### Interactive Activity (learn.js)
```javascript
// Add to learn.js file

console.log('\n=== React Hooks Simulation ===');

// Simulating React hooks behavior for learning
// Note: This is educational simulation, not actual React

// 1. useState simulation
function createUseState() {
    let stateValue;
    let hasBeenSet = false;
    
    return function useState(initialValue) {
        if (!hasBeenSet) {
            stateValue = initialValue;
            hasBeenSet = true;
        }
        
        const setState = (newValue) => {
            if (typeof newValue === 'function') {
                stateValue = newValue(stateValue);
            } else {
                stateValue = newValue;
            }
            console.log('State updated to:', stateValue);
            // In real React, this would trigger re-render
        };
        
        return [stateValue, setState];
    };
}

// Test useState simulation
const useState = createUseState();
const [count, setCount] = useState(0);

console.log('Initial count:', count);
setCount(1);
setCount(prev => prev + 1);

// 2. useEffect simulation
function createUseEffect() {
    let lastDependencies = [];
    let cleanupFunction = null;
    
    return function useEffect(effect, dependencies = []) {
        // Check if dependencies changed
        const depsChanged = dependencies.length === 0 || 
            dependencies.some((dep, index) => dep !== lastDependencies[index]);
        
        if (depsChanged) {
            // Cleanup previous effect
            if (cleanupFunction) {
                cleanupFunction();
            }
            
            // Run new effect
            console.log('Running effect with deps:', dependencies);
            cleanupFunction = effect();
            lastDependencies = [...dependencies];
        }
    };
}

// Test useEffect simulation
const useEffect = createUseEffect();

let userId = 1;
useEffect(() => {
    console.log('Fetching user data for ID:', userId);
    
    // Simulate cleanup
    return () => {
        console.log('Cleaning up user data fetch');
    };
}, [userId]);

// Simulate prop change
userId = 2;
useEffect(() => {
    console.log('Effect runs again with new userId:', userId);
}, [userId]);

// 3. Custom hook simulation
function useTasks() {
    const [tasks, setTasks] = useState([]);
    
    const addTask = (taskText) => {
        const newTask = {
            id: Date.now(),
            text: taskText,
            completed: false,
            createdAt: new Date().toISOString()
        };
        
        setTasks(prevTasks => [...prevTasks, newTask]);
        return newTask;
    };
    
    const toggleTask = (taskId) => {
        setTasks(prevTasks => 
            prevTasks.map(task =>
                task.id === taskId 
                    ? { ...task, completed: !task.completed }
                    : task
            )
        );
    };
    
    const removeTask = (taskId) => {
        setTasks(prevTasks => 
            prevTasks.filter(task => task.id !== taskId)
        );
    };
    
    const getStats = () => {
        const total = tasks.length;
        const completed = tasks.filter(task => task.completed).length;
        const pending = total - completed;
        
        return { total, completed, pending };
    };
    
    return {
        tasks,
        addTask,
        toggleTask,
        removeTask,
        stats: getStats()
    };
}

// Test custom hook
const taskManager = useTasks();

console.log('Initial tasks:', taskManager.tasks);
console.log('Initial stats:', taskManager.stats);

taskManager.addTask('Learn React Hooks');
taskManager.addTask('Build TODO app');
taskManager.toggleTask(taskManager.tasks[0]?.id);

console.log('After operations:', taskManager.tasks);
console.log('Updated stats:', taskManager.stats);

// 4. Effect dependency patterns
function simulateComponentLifecycle() {
    console.log('\n--- Component Lifecycle Simulation ---');
    
    // Mount effect (empty dependency array)
    console.log('Component mounting...');
    useEffect(() => {
        console.log('Mount effect: Component mounted');
        return () => console.log('Mount cleanup: Component unmounting');
    }, []);
    
    // Update effect (with dependencies)
    let props = { userId: 1, theme: 'light' };
    useEffect(() => {
        console.log('Update effect: User or theme changed', props);
    }, [props.userId, props.theme]);
    
    // Simulate prop changes
    props = { userId: 2, theme: 'light' };
    useEffect(() => {
        console.log('Effect runs: userId changed to', props.userId);
    }, [props.userId, props.theme]);
    
    props = { userId: 2, theme: 'dark' };
    useEffect(() => {
        console.log('Effect runs: theme changed to', props.theme);
    }, [props.userId, props.theme]);
}

simulateComponentLifecycle();

// 5. Advanced hook patterns
function useLocalStorage(key, initialValue) {
    // Simulate localStorage
    const storage = {};
    
    const [value, setValue] = useState(() => {
        try {
            const item = storage[key];
            return item ? JSON.parse(item) : initialValue;
        } catch (error) {
            return initialValue;
        }
    });
    
    const setStoredValue = (newValue) => {
        try {
            setValue(newValue);
            storage[key] = JSON.stringify(newValue);
            console.log(`Stored in localStorage[${key}]:`, newValue);
        } catch (error) {
            console.error('Error storing value:', error);
        }
    };
    
    return [value, setStoredValue];
}

// Test localStorage hook
const useSettingsState = () => {
    const [settings, setSettings] = useLocalStorage('userSettings', {
        theme: 'light',
        notifications: true,
        language: 'en'
    });
    
    const updateSetting = (key, value) => {
        setSettings(prev => ({ ...prev, [key]: value }));
    };
    
    return { settings, updateSetting };
};

const { settings, updateSetting } = useSettingsState();
console.log('Initial settings:', settings);

updateSetting('theme', 'dark');
updateSetting('notifications', false);

console.log('Updated settings:', settings);
```

---

## **Summary and Next Steps**

This appendix covers the advanced JavaScript topics that prepare students for React development. Each topic builds upon previous concepts and reinforces the patterns commonly used in modern JavaScript development.

### **Key Learning Outcomes:**
• Understanding modern JavaScript syntax and patterns
• Event-driven programming concepts
• Functional programming principles
• State management patterns
• Performance optimization techniques
• React preparation through hands-on practice

### **Recommended Study Sequence:**
1. Master arrow functions and template literals (Days 1-2)
2. Practice callback functions and event handling (Days 5-7)
3. Learn destructuring and spread operators (Day 8)
4. Understand JSX fundamentals (Day 10)
5. Practice React hooks patterns (Day 10)

### **Additional Practice:**
• Complete all interactive activities in VS Code
• Build mini-projects using each concept
• Practice interview questions with peers
• Review MDN documentation for deeper understanding
• Explore React documentation once comfortable with these concepts

This foundation will ensure smooth transition to React development and modern JavaScript frameworks.
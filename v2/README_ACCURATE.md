# 10-Day JavaScript DOM Curriculum for React Prerequisites
## BCA Third Semester - Personal Task Manager TODO Application

---

## Day 1: DOM Fundamentals & Document Structure

### Concepts

**Understanding the DOM:**
• The Document Object Model (DOM) is a programming interface that represents the structure of HTML/XML documents as a tree of objects
• DOM connects web pages to scripts by representing the document structure in memory
• Every element, attribute, and text in an HTML document becomes a node in the DOM tree
• The `document` object serves as the entry point to access and manipulate the DOM tree

**Core DOM Concepts:**
• **Document Tree Structure**: HTML elements form a hierarchical tree with parent-child relationships
• **Node Types**: Element nodes (`<div>`, `<p>`), text nodes (actual text content), attribute nodes (element attributes)
• **Document Object**: The root object that provides access to the entire DOM tree
• **DOM vs JavaScript**: DOM is a Web API, not part of JavaScript language itself

**Key Document Properties:**
• `document.documentElement` - Returns the root `<html>` element
• `document.head` - Returns the `<head>` element
• `document.body` - Returns the `<body>` element
• `document.title` - Gets/sets the document title
• `document.URL` - Returns the document's URL

**Browser DevTools for DOM Inspection:**
• Elements panel for viewing and modifying DOM structure
• Console for testing DOM manipulation commands
• Understanding the relationship between HTML source and DOM representation

### Use Cases & Examples

**Real-world Applications:**
• Dynamic content updates (social media feeds, news updates)
• Interactive web applications (forms, games, dashboards)
• Single Page Applications (SPAs) - foundation for React
• Real-time data visualization and updates

**Basic DOM Access Example:**
```javascript
// Accessing document properties
console.log(document.title);
console.log(document.URL);
console.log(document.documentElement); // <html> element
console.log(document.body); // <body> element

// Checking document ready state
console.log(document.readyState); // "loading", "interactive", or "complete"
```

### Interview Questions

1. **What is the DOM and how does it differ from HTML?**
   - DOM is the in-memory representation of HTML as a tree structure that JavaScript can manipulate
   - HTML is static markup, DOM is dynamic and can be modified by scripts

2. **Explain the DOM tree structure with an example.**
   - Hierarchical structure with nodes (elements, text, attributes)
   - Parent-child relationships: `<html>` → `<body>` → `<div>` → `<p>` → text

3. **What is the difference between the DOM and JavaScript?**
   - DOM is a Web API that provides interface to interact with documents
   - JavaScript is the programming language that uses DOM APIs

4. **How do you access the root element of an HTML document?**
   - `document.documentElement` returns the `<html>` element
   - `document.body` returns the `<body>` element

5. **What happens when JavaScript tries to access DOM before the page loads?**
   - Elements might not exist yet, causing null reference errors
   - Solutions: DOMContentLoaded event, script placement, window.onload

### Practical Project: TODO App Foundation

**Day 1 Implementation Tasks:**

1. **Set up Project Structure** (30 minutes)
   - Create/examine the provided HTML structure
   - Understand the CSS styling approach
   - Set up browser DevTools workspace

2. **DOM Inspection Exercise** (45 minutes)
   - Open the TODO app in browser
   - Use DevTools to inspect DOM structure
   - Practice accessing document properties in console:
     ```javascript
     console.log(document.title);
     console.log(document.body);
     console.log(document.querySelector('.todo-container'));
     ```

3. **Basic DOM Navigation** (45 minutes)
   - Create a simple script.js file
   - Add basic document ready detection:
     ```javascript
     // Method 1: DOMContentLoaded
     document.addEventListener('DOMContentLoaded', function() {
         console.log('DOM is ready!');
         console.log('Document title:', document.title);
     });
     
     // Method 2: Window load
     window.addEventListener('load', function() {
         console.log('Page fully loaded!');
     });
     ```

**Project Checklist for Day 1:**
- [ ] Project files are set up and running in browser
- [ ] Browser DevTools Elements panel can be navigated
- [ ] Basic document properties can be accessed via console
- [ ] Understanding of DOM tree structure for the TODO app
- [ ] script.js file created with basic DOM ready detection

### Resources for Deeper Learning

**MDN Documentation:**
- [Introduction to the DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
- [Document Interface](https://developer.mozilla.org/en-US/docs/Web/API/Document)
- [Using the Document Object Model](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Using_the_Document_Object_Model)

**Interactive Learning:**
- [JavaScript.info - DOM Tree](https://javascript.info/dom-nodes)
- [W3Schools DOM Introduction](https://www.w3schools.com/js/js_htmldom.asp)

**Video Tutorials:**
- "JavaScript DOM Crash Course" by Traversy Media
- "DOM Manipulation Explained" by Web Dev Simplified

**Practice Exercises:**
- Browser DevTools exploration exercises
- Console-based DOM property exploration
- Understanding browser rendering process

---

## Day 2: Element Selection & Traversal

### Concepts

**Element Selection Methods:**
• **querySelector()**: Returns the first element matching a CSS selector
• **querySelectorAll()**: Returns all elements matching CSS selectors as a NodeList
• **getElementById()**: Returns element with specific ID (fastest selection method)
• **getElementsByClassName()**: Returns HTMLCollection of elements with specific class
• **getElementsByTagName()**: Returns HTMLCollection of elements with specific tag name

**CSS Selector Syntax:**
• **Class selectors**: `.className` - selects elements with specific class
• **ID selectors**: `#idName` - selects element with specific ID
• **Element selectors**: `tagName` - selects elements by tag name
• **Attribute selectors**: `[attribute="value"]` - selects by attribute values
• **Complex selectors**: `parent child`, `element.class`, `element:nth-child(n)`

**Element Traversal Properties:**
• **parentNode/parentElement**: Navigate to parent element
• **childNodes**: All child nodes (including text nodes)
• **children**: Only child elements (HTMLCollection)
• **firstChild/firstElementChild**: First child node/element
• **lastChild/lastElementChild**: Last child node/element
• **nextSibling/nextElementSibling**: Next sibling node/element
• **previousSibling/previousElementSibling**: Previous sibling node/element

**NodeList vs HTMLCollection:**
• **NodeList**: Static or live collection returned by querySelectorAll()
• **HTMLCollection**: Live collection returned by getElementsBy* methods
• **forEach()**: Available on NodeList, need to convert HTMLCollection to Array

### Use Cases & Examples

**Real-world Applications:**
• Form validation and input field selection
• Navigation menu highlighting and interaction
• Content filtering and search functionality
• Dynamic content updates based on user selection
• Building interactive components and widgets

**Selection Examples:**
```javascript
// Different selection methods
const container = document.getElementById('task-list');
const firstTask = document.querySelector('.task-item');
const allTasks = document.querySelectorAll('.task-item');
const buttons = document.getElementsByTagName('button');

// Complex selectors
const activeTask = document.querySelector('.task-item.active');
const inputInContainer = document.querySelector('.todo-container input[type="text"]');
const lastTaskButton = document.querySelector('.task-item:last-child button');
```

**Traversal Examples:**
```javascript
// Element traversal
const taskItem = document.querySelector('.task-item');
const container = taskItem.parentElement;
const nextTask = taskItem.nextElementSibling;
const taskText = taskItem.firstElementChild;

// Navigating through siblings
let currentTask = container.firstElementChild;
while (currentTask) {
    console.log(currentTask.textContent);
    currentTask = currentTask.nextElementSibling;
}
```

### Interview Questions

1. **What's the difference between querySelector() and getElementById()?**
   - querySelector() uses CSS selectors, can select by any attribute/class/tag
   - getElementById() is faster, specifically for ID-based selection
   - querySelector() returns first match, getElementById() returns single element

2. **Explain NodeList vs HTMLCollection.**
   - NodeList: Returned by querySelectorAll(), can be static or live
   - HTMLCollection: Returned by getElementsBy* methods, always live
   - NodeList has forEach(), HTMLCollection needs Array.from() for iteration

3. **How do you select all elements with class 'active' inside a specific container?**
   - `container.querySelectorAll('.active')` or `document.querySelectorAll('#container .active')`

4. **What's the difference between childNodes and children?**
   - childNodes: All child nodes including text, comment, element nodes
   - children: Only element nodes (HTMLCollection)

5. **How would you find the parent of an element that has a specific class?**
   - Use parentElement in a loop: `while (element.parentElement && !element.parentElement.classList.contains('target-class'))`

### Practical Project: TODO App Element Selection

**Day 2 Implementation Tasks:**

1. **Basic Element Selection** (45 minutes)
   - Practice selecting TODO app elements using different methods:
     ```javascript
     // Add to script.js
     document.addEventListener('DOMContentLoaded', function() {
         // Practice different selection methods
         const container = document.getElementById('task-list');
         const addButton = document.querySelector('#add-task-btn');
         const input = document.querySelector('input[type="text"]');
         const todoContainer = document.querySelector('.todo-container');
         
         console.log('Container:', container);
         console.log('Add button:', addButton);
         console.log('Input field:', input);
         console.log('Main container:', todoContainer);
     });
     ```

2. **Element Traversal Practice** (45 minutes)
   - Create sample TODO items in HTML and practice navigation:
     ```javascript
     // Add some sample tasks to practice with
     const sampleTasks = ['Learn JavaScript', 'Build TODO app', 'Master DOM'];
     const taskList = document.getElementById('task-list');
     
     // Create sample tasks for practice
     sampleTasks.forEach(task => {
         const li = document.createElement('li');
         li.textContent = task;
         li.className = 'task-item';
         taskList.appendChild(li);
     });
     
     // Practice traversal
     const firstTask = taskList.firstElementChild;
     const lastTask = taskList.lastElementChild;
     console.log('First task:', firstTask?.textContent);
     console.log('Last task:', lastTask?.textContent);
     
     // Navigate through all tasks
     let currentTask = taskList.firstElementChild;
     while (currentTask) {
         console.log('Task:', currentTask.textContent);
         currentTask = currentTask.nextElementSibling;
     }
     ```

3. **Selection Strategy Implementation** (30 minutes)
   - Implement helper functions for common selections:
     ```javascript
     // Utility functions for element selection
     const TodoSelectors = {
         getContainer: () => document.querySelector('.todo-container'),
         getTaskList: () => document.getElementById('task-list'),
         getAddButton: () => document.getElementById('add-task-btn'),
         getInput: () => document.getElementById('task-input'),
         getAllTasks: () => document.querySelectorAll('#task-list li'),
         getTaskByIndex: (index) => document.querySelector(`#task-list li:nth-child(${index + 1})`)
     };
     
     // Test the utility functions
     console.log('All current tasks:', TodoSelectors.getAllTasks());
     ```

**Project Checklist for Day 2:**
- [ ] Can select elements using getElementById, querySelector, querySelectorAll
- [ ] Understand difference between NodeList and HTMLCollection
- [ ] Can navigate parent-child relationships using traversal properties
- [ ] Can navigate sibling relationships (next/previous)
- [ ] Helper functions created for common TODO app selections
- [ ] Practice with complex CSS selectors in TODO context

### Resources for Deeper Learning

**MDN Documentation:**
- [querySelector() method](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)
- [Node interface and traversal](https://developer.mozilla.org/en-US/docs/Web/API/Node)
- [Locating DOM elements using selectors](https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model/Locating_DOM_elements_using_selectors)

**Interactive Learning:**
- [JavaScript.info - Searching elements](https://javascript.info/searching-elements-dom)
- [CSS Selectors Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors)

**Video Tutorials:**
- "DOM Element Selection" by The Net Ninja
- "JavaScript DOM Traversal" by Traversy Media

**Practice Exercises:**
- CSS selector playground and practice
- Element traversal challenges
- Building selector utility functions

---

## Day 3: Creating & Modifying Elements

### Concepts

**Element Creation Methods:**
• **document.createElement()**: Creates a new HTML element with specified tag name
• **document.createTextNode()**: Creates a text node containing specified text
• **element.cloneNode()**: Creates a copy of an existing element (shallow or deep copy)
• **document.createDocumentFragment()**: Creates a lightweight container for multiple elements

**Adding Elements to DOM:**
• **appendChild()**: Adds element as the last child of parent
• **insertBefore()**: Inserts element before a reference node
• **append()**: Modern method to add multiple nodes/strings at once
• **prepend()**: Adds elements at the beginning of parent
• **insertAdjacentElement()**: Inserts element at specified position relative to target

**Removing Elements:**
• **removeChild()**: Removes child element from parent (older method)
• **remove()**: Modern method to remove element directly
• **replaceChild()**: Replaces one child with another

**Content Manipulation:**
• **innerHTML**: Gets/sets HTML content inside element (parses HTML tags)
• **textContent**: Gets/sets plain text content (ignores HTML tags)
• **innerText**: Gets/sets visible text (respects styling like display: none)
• **outerHTML**: Gets/sets element including its own opening/closing tags

**innerHTML vs textContent vs innerText:**
• **innerHTML**: Interprets HTML tags, can execute scripts (security risk with user input)
• **textContent**: Faster, secure, gets all text including hidden elements
• **innerText**: Slower, respects CSS styling, only visible text

### Use Cases & Examples

**Real-world Applications:**
• Dynamic content generation (news feeds, product listings)
• Interactive forms with conditional fields
• Real-time chat applications with message creation
• Todo lists, shopping carts, and CRUD applications
• Template rendering and component-based UI updates

**Element Creation Examples:**
```javascript
// Creating elements
const taskItem = document.createElement('li');
const taskText = document.createTextNode('Learn DOM manipulation');
const deleteButton = document.createElement('button');

// Setting properties and content
taskItem.className = 'task-item';
deleteButton.textContent = 'Delete';
deleteButton.className = 'delete-btn';

// Building element structure
taskItem.appendChild(taskText);
taskItem.appendChild(deleteButton);

// Adding to DOM
const taskList = document.getElementById('task-list');
taskList.appendChild(taskItem);
```

**Content Manipulation Examples:**
```javascript
const element = document.querySelector('.content');

// Different ways to set content
element.innerHTML = '<strong>Bold text</strong>';  // Renders HTML
element.textContent = '<strong>Bold text</strong>'; // Shows literal text
element.innerText = 'Visible text only';           // Respects CSS visibility

// Safe content update
element.textContent = userInput; // Prevents XSS attacks
```

### Interview Questions

1. **What's the difference between innerHTML and textContent?**
   - innerHTML parses and renders HTML tags, textContent treats everything as plain text
   - innerHTML can be a security risk with user input (XSS), textContent is safe
   - textContent is faster for reading/setting plain text

2. **Explain appendChild() vs append().**
   - appendChild() only accepts single Node objects, returns the appended node
   - append() accepts multiple nodes and strings, returns undefined
   - append() is more modern and flexible

3. **When would you use DocumentFragment?**
   - When adding multiple elements to avoid multiple DOM reflows
   - Better performance for bulk operations
   - Creating complex structures before inserting into DOM

4. **How do you safely insert user-generated content?**
   - Use textContent instead of innerHTML
   - Sanitize HTML if innerHTML is necessary
   - Use createElement() and textContent for dynamic content

5. **What happens when you set innerHTML on an element with event listeners?**
   - All child elements are destroyed and recreated
   - Event listeners are lost and need to be re-attached
   - Better to use createElement and appendChild for dynamic content

### Practical Project: TODO App Dynamic Creation

**Day 3 Implementation Tasks:**

1. **Basic Element Creation Function** (45 minutes)
   - Create a function to generate TODO items dynamically:
     ```javascript
     function createTaskElement(taskText) {
         // Create main list item
         const li = document.createElement('li');
         li.className = 'task-item';
         
         // Create task text span
         const textSpan = document.createElement('span');
         textSpan.textContent = taskText;
         textSpan.className = 'task-text';
         
         // Create delete button
         const deleteBtn = document.createElement('button');
         deleteBtn.textContent = 'Delete';
         deleteBtn.className = 'delete-btn';
         
         // Assemble the task item
         li.appendChild(textSpan);
         li.appendChild(deleteBtn);
         
         return li;
     }
     
     // Test the function
     const newTask = createTaskElement('Test dynamic creation');
     document.getElementById('task-list').appendChild(newTask);
     ```

2. **Content Manipulation Practice** (45 minutes)
   - Practice different content setting methods:
     ```javascript
     // Content manipulation utilities
     const ContentManager = {
         // Safe text setting
         setTaskText: function(element, text) {
             const textSpan = element.querySelector('.task-text');
             textSpan.textContent = text; // Safe from XSS
         },
         
         // HTML content (for formatting)
         setFormattedContent: function(element, htmlContent) {
             // Only use with trusted content
             element.innerHTML = htmlContent;
         },
         
         // Clear all tasks
         clearAllTasks: function() {
             const taskList = document.getElementById('task-list');
             taskList.textContent = ''; // Fast way to clear
         },
         
         // Get all task texts
         getAllTaskTexts: function() {
             const tasks = document.querySelectorAll('.task-text');
             return Array.from(tasks).map(task => task.textContent);
         }
     };
     
     // Test content manipulation
     console.log('Current tasks:', ContentManager.getAllTaskTexts());
     ```

3. **Advanced Creation Patterns** (30 minutes)
   - Implement template-based creation and DocumentFragment usage:
     ```javascript
     // Template-based creation
     function createTaskFromTemplate(taskData) {
         const template = document.createElement('template');
         template.innerHTML = `
             <li class="task-item" data-id="${taskData.id}">
                 <span class="task-text">${taskData.text}</span>
                 <button class="delete-btn">Delete</button>
             </li>
         `;
         return template.content.firstElementChild;
     }
     
     // Bulk creation with DocumentFragment
     function addMultipleTasks(tasksArray) {
         const fragment = document.createDocumentFragment();
         
         tasksArray.forEach(taskText => {
             const taskElement = createTaskElement(taskText);
             fragment.appendChild(taskElement);
         });
         
         document.getElementById('task-list').appendChild(fragment);
     }
     
     // Test bulk creation
     addMultipleTasks(['Task 1', 'Task 2', 'Task 3']);
     ```

**Project Checklist for Day 3:**
- [ ] Can create elements using createElement() and createTextNode()
- [ ] Understand appendChild(), insertBefore(), and modern append() methods
- [ ] Know the difference between innerHTML, textContent, and innerText
- [ ] Can safely handle user input using textContent
- [ ] Implemented dynamic TODO item creation function
- [ ] Practice with DocumentFragment for performance optimization

### Resources for Deeper Learning

**MDN Documentation:**
- [createElement() method](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)
- [innerHTML property](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML)
- [textContent property](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent)
- [DocumentFragment](https://developer.mozilla.org/en-US/docs/Web/API/DocumentFragment)

**Interactive Learning:**
- [JavaScript.info - Modifying the document](https://javascript.info/modifying-document)
- [DOM Manipulation Methods Guide](https://javascript.info/dom-nodes)

**Video Tutorials:**
- "Creating DOM Elements with JavaScript" by Web Dev Simplified
- "innerHTML vs textContent vs innerText" by The Net Ninja

**Practice Exercises:**
- Dynamic list creation challenges
- Safe content insertion exercises
- Performance comparison: innerHTML vs createElement

---

## Day 4: Attributes & Styling Manipulation

### Concepts

**Element Attributes:**
• **getAttribute()**: Retrieves the value of a specified attribute
• **setAttribute()**: Sets the value of an attribute on the specified element
• **hasAttribute()**: Returns boolean indicating if element has the specified attribute
• **removeAttribute()**: Removes the specified attribute from an element
• **toggleAttribute()**: Toggles a boolean attribute (adds if absent, removes if present)

**HTML Attributes vs DOM Properties:**
• **Attributes**: Defined in HTML markup, always strings, case-insensitive
• **Properties**: JavaScript object properties, can be any type, case-sensitive
• **Synchronization**: Some attributes sync with properties (id, className), others don't

**classList API:**
• **classList.add()**: Adds one or more CSS classes to element
• **classList.remove()**: Removes one or more CSS classes from element
• **classList.toggle()**: Toggles a class (adds if missing, removes if present)
• **classList.contains()**: Returns true if element has the specified class
• **classList.replace()**: Replaces one class with another

**Direct Style Manipulation:**
• **element.style**: Access to inline CSS styles object
• **element.style.property**: Set individual CSS properties
• **getComputedStyle()**: Get actual computed styles (read-only)
• **CSS custom properties**: Using setProperty() for CSS variables

**Data Attributes:**
• **data-* attributes**: Custom attributes for storing extra information
• **dataset property**: JavaScript interface to access data attributes
• **Naming convention**: data-my-value becomes dataset.myValue

### Use Cases & Examples

**Real-world Applications:**
• Dynamic theme switching and visual feedback
• Form validation with visual indicators
• Interactive UI components with state changes
• Accessibility attributes for screen readers
• Progressive enhancement of existing content

**Attribute Manipulation Examples:**
```javascript
const taskItem = document.querySelector('.task-item');

// Working with attributes
taskItem.setAttribute('data-priority', 'high');
taskItem.setAttribute('aria-label', 'High priority task');
const priority = taskItem.getAttribute('data-priority'); // "high"
const hasId = taskItem.hasAttribute('id'); // true/false

// Data attributes
taskItem.dataset.completed = 'false';
taskItem.dataset.createdAt = new Date().toISOString();
console.log(taskItem.dataset.priority); // "high"
```

**CSS Class Manipulation Examples:**
```javascript
const element = document.querySelector('.task-item');

// Adding/removing classes
element.classList.add('completed', 'highlighted');
element.classList.remove('pending');
element.classList.toggle('active'); // adds if missing, removes if present

// Conditional toggling
element.classList.toggle('visible', isVisible); // toggle based on condition

// Checking for classes
if (element.classList.contains('completed')) {
    console.log('Task is completed');
}

// Replacing classes
element.classList.replace('old-style', 'new-style');
```

**Style Manipulation Examples:**
```javascript
const element = document.querySelector('.progress-bar');

// Direct style manipulation
element.style.width = '75%';
element.style.backgroundColor = '#4caf50';
element.style.transition = 'width 0.3s ease';

// CSS custom properties
element.style.setProperty('--progress-color', '#ff5722');
document.documentElement.style.setProperty('--theme-color', '#2196f3');

// Getting computed styles
const computedStyle = getComputedStyle(element);
const actualWidth = computedStyle.width; // "300px"
```

### Interview Questions

1. **What's the difference between setAttribute() and direct property assignment?**
   - setAttribute() always works with strings, affects HTML attribute
   - Direct property (element.id) can work with different types, affects DOM property
   - Some attributes and properties stay in sync, others don't

2. **Explain the classList API and its advantages over className.**
   - classList provides methods (add, remove, toggle, contains) for easy class manipulation
   - className is a string that requires manual parsing and concatenation
   - classList prevents common errors like duplicate classes

3. **When should you use element.style vs CSS classes?**
   - element.style for dynamic values calculated in JavaScript
   - CSS classes for predefined styles and better separation of concerns
   - element.style creates inline styles (highest specificity)

4. **How do data attributes work and when are they useful?**
   - data-* attributes store custom data in HTML elements
   - Accessible via dataset property in JavaScript
   - Useful for storing metadata, configuration, or state information

5. **What's the difference between element.style and getComputedStyle()?**
   - element.style only shows inline styles, read/write
   - getComputedStyle() shows final computed styles from all sources, read-only
   - getComputedStyle() includes inherited and default browser styles

### Practical Project: TODO App Styling & Visual Feedback

**Day 4 Implementation Tasks:**

1. **Task State Management with Classes** (45 minutes)
   - Implement visual states for TODO items using CSS classes:
     ```javascript
     // Add to script.js - Task state management
     const TaskStates = {
         toggleComplete: function(taskElement) {
             taskElement.classList.toggle('completed');
             const isCompleted = taskElement.classList.contains('completed');
             
             // Update data attribute
             taskElement.dataset.completed = isCompleted;
             
             // Update aria-label for accessibility
             const taskText = taskElement.querySelector('.task-text').textContent;
             taskElement.setAttribute('aria-label', 
                 `${taskText} - ${isCompleted ? 'completed' : 'pending'}`);
         },
         
         setPriority: function(taskElement, priority) {
             // Remove existing priority classes
             taskElement.classList.remove('priority-low', 'priority-medium', 'priority-high');
             
             // Add new priority class
             if (priority) {
                 taskElement.classList.add(`priority-${priority}`);
                 taskElement.dataset.priority = priority;
             }
         },
         
         highlight: function(taskElement, isHighlighted) {
             taskElement.classList.toggle('highlighted', isHighlighted);
         }
     };
     
     // Test the functions
     const firstTask = document.querySelector('.task-item');
     if (firstTask) {
         TaskStates.setPriority(firstTask, 'high');
         TaskStates.highlight(firstTask, true);
     }
     ```

2. **Dynamic Styling and Attributes** (45 minutes)
   - Add dynamic styling capabilities to TODO items:
     ```javascript
     // Visual feedback utilities
     const VisualFeedback = {
         animateTaskCreation: function(taskElement) {
             // Add creation animation class
             taskElement.classList.add('task-creating');
             
             // Remove animation class after animation completes
             setTimeout(() => {
                 taskElement.classList.remove('task-creating');
             }, 300);
         },
         
         showValidationError: function(inputElement, message) {
             inputElement.classList.add('error');
             inputElement.setAttribute('aria-invalid', 'true');
             inputElement.setAttribute('title', message);
             
             // Auto-remove error state after 3 seconds
             setTimeout(() => {
                 this.clearValidationError(inputElement);
             }, 3000);
         },
         
         clearValidationError: function(inputElement) {
             inputElement.classList.remove('error');
             inputElement.removeAttribute('aria-invalid');
             inputElement.removeAttribute('title');
         },
         
         updateTaskCounter: function(count) {
             const counter = document.querySelector('.task-counter');
             if (counter) {
                 counter.textContent = `${count} tasks`;
                 counter.style.setProperty('--task-count', count);
             }
         }
     };
     
     // Test visual feedback
     const input = document.getElementById('task-input');
     VisualFeedback.showValidationError(input, 'Task cannot be empty');
     ```

3. **Advanced Styling with CSS Custom Properties** (30 minutes)
   - Implement theme switching and custom styling:
     ```javascript
     // Theme and style management
     const StyleManager = {
         themes: {
             light: {
                 '--bg-color': '#ffffff',
                 '--text-color': '#333333',
                 '--accent-color': '#007bff'
             },
             dark: {
                 '--bg-color': '#1a1a1a',
                 '--text-color': '#ffffff',
                 '--accent-color': '#4fc3f7'
             }
         },
         
         applyTheme: function(themeName) {
             const theme = this.themes[themeName];
             const root = document.documentElement;
             
             Object.entries(theme).forEach(([property, value]) => {
                 root.style.setProperty(property, value);
             });
             
             // Store theme preference
             localStorage.setItem('theme', themeName);
             document.body.dataset.theme = themeName;
         },
         
         setTaskProgress: function(taskElement, progress) {
             // Update progress bar width
             const progressBar = taskElement.querySelector('.progress-bar');
             if (progressBar) {
                 progressBar.style.width = `${progress}%`;
                 progressBar.setAttribute('aria-valuenow', progress);
             }
         },
         
         addCustomStyles: function(element, styles) {
             Object.entries(styles).forEach(([property, value]) => {
                 element.style[property] = value;
             });
         }
     };
     
     // Test theme switching
     StyleManager.applyTheme('dark');
     ```

**Project Checklist for Day 4:**
- [ ] Can manipulate element attributes using getAttribute/setAttribute
- [ ] Understand classList API for adding/removing/toggling CSS classes
- [ ] Can apply direct styling using element.style properties
- [ ] Working with data attributes for storing custom information
- [ ] Implemented visual feedback for TODO app interactions
- [ ] Created theme switching capability using CSS custom properties

### Resources for Deeper Learning

**MDN Documentation:**
- [getAttribute() method](https://developer.mozilla.org/en-US/docs/Web/API/Element/getAttribute)
- [classList property](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)
- [Using data attributes](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes)
- [CSS custom properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)

**Interactive Learning:**
- [JavaScript.info - Styles and classes](https://javascript.info/styles-and-classes)
- [CSS-Tricks - Using Data Attributes](https://css-tricks.com/a-complete-guide-to-data-attributes/)

**Video Tutorials:**
- "JavaScript DOM Styling" by Web Dev Simplified
- "CSS Custom Properties with JavaScript" by Kevin Powell

**Practice Exercises:**
- Dynamic theme switching challenges
- Attribute manipulation practice
- Visual feedback implementation exercises

---

## Day 5: Event Handling Fundamentals

### Concepts

**Event Handling Basics:**
• **addEventListener()**: Modern method to attach event listeners to elements
• **Event object**: Contains information about the event (type, target, coordinates, etc.)
• **Event types**: Click, mouseover, keydown, submit, load, DOMContentLoaded, etc.
• **Event target**: The element that triggered the event (event.target)
• **Event currentTarget**: The element the event listener is attached to (event.currentTarget)

**Common DOM Events:**
• **Mouse events**: click, dblclick, mousedown, mouseup, mouseover, mouseout, mousemove
• **Keyboard events**: keydown, keyup, keypress (deprecated)
• **Form events**: submit, change, input, focus, blur
• **Window events**: load, resize, scroll, beforeunload
• **Touch events**: touchstart, touchend, touchmove (for mobile)

**Event Listener Options:**
• **once**: Event listener will only fire once, then automatically remove itself
• **passive**: Event listener will never call preventDefault(), improves performance
• **capture**: Event listener will fire during capture phase instead of bubble phase
• **signal**: AbortSignal to remove event listener programmatically

**Removing Event Listeners:**
• **removeEventListener()**: Removes previously added event listener
• **Same function reference**: Must use exact same function reference to remove
• **AbortController**: Modern way to manage and remove multiple event listeners

**Event Handler Function Context:**
• **this binding**: In regular functions, 'this' refers to the element that triggered the event
• **Arrow functions**: 'this' inherits from surrounding scope, not the event target
• **Function parameters**: Event object is automatically passed as first parameter

### Use Cases & Examples

**Real-world Applications:**
• User interaction handling (clicks, form submissions, keyboard shortcuts)
• Dynamic UI updates based on user actions
• Form validation and real-time feedback
• Interactive components (dropdowns, modals, carousels)
• Game controls and interactive animations

**Basic Event Handling Examples:**
```javascript
// Basic click event
const button = document.getElementById('add-task-btn');
button.addEventListener('click', function(event) {
    console.log('Button clicked!');
    console.log('Event type:', event.type);
    console.log('Target element:', event.target);
});

// Arrow function event handler
const input = document.getElementById('task-input');
input.addEventListener('input', (event) => {
    console.log('Input value:', event.target.value);
});

// Multiple event types
const element = document.querySelector('.task-item');
element.addEventListener('mouseenter', handleMouseEnter);
element.addEventListener('mouseleave', handleMouseLeave);
element.addEventListener('click', handleClick);
```

**Event Object Properties:**
```javascript
function handleEvent(event) {
    console.log('Event type:', event.type);           // 'click', 'keydown', etc.
    console.log('Target:', event.target);             // Element that triggered event
    console.log('Current target:', event.currentTarget); // Element with listener
    console.log('Mouse position:', event.clientX, event.clientY);
    console.log('Key pressed:', event.key);           // For keyboard events
    console.log('Timestamp:', event.timeStamp);       // When event occurred
}
```

**Event Listener Options:**
```javascript
// Once option - listener runs only once
button.addEventListener('click', handleClick, { once: true });

// Passive option - improves scroll performance
document.addEventListener('wheel', handleScroll, { passive: true });

// Using AbortController for cleanup
const controller = new AbortController();
element.addEventListener('click', handleClick, { 
    signal: controller.signal 
});
// Later: controller.abort(); // Removes all listeners with this signal
```

### Interview Questions

1. **What's the difference between addEventListener() and onclick property?**
   - addEventListener() can attach multiple listeners to same event
   - onclick can only hold one function, newer assignments overwrite previous ones
   - addEventListener() provides more options (once, passive, capture)

2. **Explain the event object and its key properties.**
   - Automatically passed to event handlers as first parameter
   - Contains event.type, event.target, event.currentTarget
   - Mouse events have clientX/clientY, keyboard events have key/keyCode

3. **What happens if you don't remove event listeners?**
   - Memory leaks, especially when removing DOM elements
   - Event listeners keep references to functions and elements
   - Use removeEventListener() or AbortController for cleanup

4. **How do arrow functions behave differently in event handlers?**
   - Arrow functions don't have their own 'this' binding
   - 'this' refers to surrounding scope, not the event target
   - Regular functions have 'this' pointing to the element that triggered the event

5. **What are passive event listeners and when should you use them?**
   - Passive listeners promise never to call preventDefault()
   - Browser can optimize scrolling and touch performance
   - Use for scroll, wheel, and touch events that don't need to prevent default

### Practical Project: TODO App Click Handlers

**Day 5 Implementation Tasks:**

1. **Basic Click Event Handling** (45 minutes)
   - Add click handlers for TODO app buttons:
     ```javascript
     // Add to script.js - Basic event handling
     document.addEventListener('DOMContentLoaded', function() {
         const addButton = document.getElementById('add-task-btn');
         const taskInput = document.getElementById('task-input');
         const taskList = document.getElementById('task-list');
         
         // Add task button click handler
         addButton.addEventListener('click', function(event) {
             console.log('Add button clicked');
             const taskText = taskInput.value.trim();
             
             if (taskText) {
                 addNewTask(taskText);
                 taskInput.value = ''; // Clear input
             } else {
                 alert('Please enter a task!');
             }
         });
         
         // Input field enter key handler
         taskInput.addEventListener('keydown', function(event) {
             if (event.key === 'Enter') {
                 console.log('Enter key pressed');
                 addButton.click(); // Trigger button click
             }
         });
         
         // Simple add task function
         function addNewTask(text) {
             const li = document.createElement('li');
             li.className = 'task-item';
             li.innerHTML = `
                 <span class="task-text">${text}</span>
                 <button class="delete-btn">Delete</button>
             `;
             taskList.appendChild(li);
         }
     });
     ```

2. **Event Object Exploration** (45 minutes)
   - Practice working with event objects and different event types:
     ```javascript
     // Event object practice
     const EventPractice = {
         init: function() {
             const taskList = document.getElementById('task-list');
             
             // Click events with detailed logging
             taskList.addEventListener('click', this.handleTaskListClick.bind(this));
             
             // Mouse events for visual feedback
             taskList.addEventListener('mouseover', this.handleMouseOver);
             taskList.addEventListener('mouseout', this.handleMouseOut);
             
             // Input events
             const input = document.getElementById('task-input');
             input.addEventListener('input', this.handleInputChange);
             input.addEventListener('focus', this.handleInputFocus);
             input.addEventListener('blur', this.handleInputBlur);
         },
         
         handleTaskListClick: function(event) {
             console.log('=== Click Event Details ===');
             console.log('Event type:', event.type);
             console.log('Target element:', event.target);
             console.log('Target tag name:', event.target.tagName);
             console.log('Target class list:', event.target.classList.toString());
             console.log('Current target:', event.currentTarget);
             console.log('Mouse position:', event.clientX, event.clientY);
             
             // Handle delete button clicks
             if (event.target.classList.contains('delete-btn')) {
                 this.deleteTask(event.target.closest('.task-item'));
             }
         },
         
         handleMouseOver: function(event) {
             if (event.target.classList.contains('task-item')) {
                 event.target.style.backgroundColor = '#f0f0f0';
             }
         },
         
         handleMouseOut: function(event) {
             if (event.target.classList.contains('task-item')) {
                 event.target.style.backgroundColor = '';
             }
         },
         
         handleInputChange: function(event) {
             console.log('Input value changed:', event.target.value);
             console.log('Input length:', event.target.value.length);
         },
         
         handleInputFocus: function(event) {
             console.log('Input focused');
             event.target.style.borderColor = '#007bff';
         },
         
         handleInputBlur: function(event) {
             console.log('Input blurred');
             event.target.style.borderColor = '';
         },
         
         deleteTask: function(taskItem) {
             console.log('Deleting task:', taskItem.querySelector('.task-text').textContent);
             taskItem.remove();
         }
     };
     
     // Initialize event practice
     EventPractice.init();
     ```

3. **Event Management and Cleanup** (30 minutes)
   - Implement proper event listener management:
     ```javascript
     // Event manager for cleanup and organization
     class EventManager {
         constructor() {
             this.controllers = new Map();
         }
         
         addListener(element, eventType, handler, options = {}) {
             // Create abort controller for this listener
             const controller = new AbortController();
             const listenerId = `${element.id || 'element'}_${eventType}_${Date.now()}`;
             
             // Add signal to options
             const finalOptions = { ...options, signal: controller.signal };
             
             // Add the listener
             element.addEventListener(eventType, handler, finalOptions);
             
             // Store controller for later cleanup
             this.controllers.set(listenerId, controller);
             
             console.log(`Added listener: ${listenerId}`);
             return listenerId;
         }
         
         removeListener(listenerId) {
             const controller = this.controllers.get(listenerId);
             if (controller) {
                 controller.abort();
                 this.controllers.delete(listenerId);
                 console.log(`Removed listener: ${listenerId}`);
             }
         }
         
         removeAllListeners() {
             this.controllers.forEach((controller, id) => {
                 controller.abort();
                 console.log(`Removed listener: ${id}`);
             });
             this.controllers.clear();
         }
     }
     
     // Usage example
     const eventManager = new EventManager();
     
     // Add managed listeners
     const buttonListenerId = eventManager.addListener(
         document.getElementById('add-task-btn'),
         'click',
         function(event) {
             console.log('Managed click event');
         },
         { once: false }
     );
     
     // Clean up when needed (e.g., when component unmounts)
     // eventManager.removeListener(buttonListenerId);
     // eventManager.removeAllListeners();
     ```

**Project Checklist for Day 5:**
- [ ] Can attach event listeners using addEventListener()
- [ ] Understand event object properties and how to access them
- [ ] Implemented click handlers for add and delete functionality
- [ ] Added keyboard event handling (Enter key)
- [ ] Practice with mouse events for visual feedback
- [ ] Understand event listener cleanup and management

### Resources for Deeper Learning

**MDN Documentation:**
- [addEventListener() method](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)
- [Event object reference](https://developer.mozilla.org/en-US/docs/Web/API/Event)
- [DOM Events overview](https://developer.mozilla.org/en-US/docs/Web/Events)
- [AbortController for event cleanup](https://developer.mozilla.org/en-US/docs/Web/API/AbortController)

**Interactive Learning:**
- [JavaScript.info - Introduction to Events](https://javascript.info/introduction-browser-events)
- [Event types reference](https://developer.mozilla.org/en-US/docs/Web/Events)

**Video Tutorials:**
- "JavaScript Event Listeners" by Web Dev Simplified
- "DOM Events Explained" by The Net Ninja

**Practice Exercises:**
- Event handler implementation challenges
- Event object exploration exercises
- Event cleanup and management practice

---

## Day 6: Form Handling & Input Validation

### Concepts

**Form Elements and Attributes:**
• **form**: The `<form>` element represents a document section that contains interactive controls for submitting information
• **input**: The `<input>` element is used to create interactive controls in a form that users can use to enter data
• **textarea**: The `<textarea>` element is used for multi-line text inputs
• **select**: The `<select>` element is used to create a drop-down list
• **button**: The `<button>` element represents a clickable button, used to submit forms or trigger actions

**Form Events:**
• **submit**: Fired when a form is submitted
• **change**: Fired when the value of an `<input>`, `<textarea>`, or `<select>` element has been changed
• **input**: Fired synchronously when the value of an `<input>` or `<textarea>` element changes
• **focus**: Fired when an element has received focus
• **blur**: Fired when an element has lost focus

**Input Validation:**
• **Required fields**: Use the `required` attribute to specify that an input field must be filled out
• **Pattern matching**: Use the `pattern` attribute with a regular expression to specify a pattern for the input value
• **Min/max length**: Use `minlength` and `maxlength` attributes to specify the minimum and maximum number of characters
• **Type-specific validation**: Use input types like `email`, `url`, `number` for built-in validation

**FormData API:**
• **FormData**: A built-in object that provides a way to easily construct a set of key/value pairs representing form fields and their values
• **Appending data**: Use the `append()` method to add a new value onto an existing key inside a FormData object
• **Deleting data**: Use the `delete()` method to remove a key/value pair from the FormData object
• **Iterating data**: Use the `forEach()` method to iterate over the FormData object

### Use Cases & Examples

**Real-world Applications:**
• User registration and login forms
• Profile information and settings forms
• Search and filter forms
• Payment and checkout forms
• Feedback and comment forms

**Basic Form Handling Examples:**
```javascript
// Basic form submission
const form = document.getElementById('task-form');
form.addEventListener('submit', function(event) {
    event.preventDefault(); // Prevent default form submission
    console.log('Form submitted!');
    
    // Accessing form data
    const formData = new FormData(form);
    for (let [key, value] of formData.entries()) {
        console.log(key, value);
    }
});
```

**Input Validation Examples:**
```javascript
// Real-time input validation
const emailInput = document.getElementById('email');
emailInput.addEventListener('input', function(event) {
    const email = event.target.value;
    if (email.includes('@')) {
        emailInput.setCustomValidity(''); // Reset custom error message
    } else {
        emailInput.setCustomValidity('Email must contain @ symbol');
    }
});

// Form submission with validation
form.addEventListener('submit', function(event) {
    if (!emailInput.checkValidity()) {
        event.preventDefault(); // Prevent form submission
        alert('Please fix the errors in the form');
    }
});
```

### Interview Questions

1. **What is the purpose of the form element in HTML?**
   - The `<form>` element is used to collect user input and submit it to a server for processing
   - It can contain various input elements like text fields, checkboxes, radio buttons, and buttons

2. **How do you prevent a form from submitting in JavaScript?**
   - Use `event.preventDefault()` in the form's submit event handler to prevent the default form submission behavior

3. **What is the FormData API and how do you use it?**
   - The FormData API provides a way to construct a set of key/value pairs representing form fields and their values
   - It can be used to easily send form data using `XMLHttpRequest` or the `fetch` API

4. **How can you validate form inputs in HTML?**
   - Use attributes like `required`, `pattern`, `minlength`, and `maxlength` on form elements
   - Use JavaScript to add custom validation logic and display error messages

5. **What are some common form events in JavaScript?**
   - `submit`, `change`, `input`, `focus`, `blur`, `reset`

### Practical Project: TODO App Form Handling

**Day 6 Implementation Tasks:**

1. **Form Structure and Basic Handling** (45 minutes)
   - Create a form for adding new TODO items:
     ```html
     <form id="task-form">
         <input type="text" id="task-input" placeholder="Enter a new task" required>
         <button type="submit" id="add-task-btn">Add Task</button>
     </form>
     ```
   - Add basic form submission handling:
     ```javascript
     // Add to script.js - Form handling
     document.addEventListener('DOMContentLoaded', function() {
         const form = document.getElementById('task-form');
         const taskInput = document.getElementById('task-input');
         const taskList = document.getElementById('task-list');
         
         // Form submission handler
         form.addEventListener('submit', function(event) {
             event.preventDefault(); // Prevent default form submission
             const taskText = taskInput.value.trim();
             
             if (taskText) {
                 addNewTask(taskText);
                 taskInput.value = ''; // Clear input
             } else {
                 alert('Please enter a task!');
             }
         });
     });
     ```

2. **Input Validation Implementation** (45 minutes)
   - Add real-time validation and custom error messages:
     ```javascript
     // Add to script.js - Input validation
     document.addEventListener('DOMContentLoaded', function() {
         const form = document.getElementById('task-form');
         const taskInput = document.getElementById('task-input');
         
         // Real-time input validation
         taskInput.addEventListener('input', function(event) {
             const taskText = event.target.value.trim();
             if (taskText.length < 3) {
                 taskInput.setCustomValidity('Task must be at least 3 characters long');
             } else {
                 taskInput.setCustomValidity(''); // Reset custom error message
             }
         });
     });
     ```

3. **FormData API Practice** (30 minutes)
   - Use FormData API to handle form data:
     ```javascript
     // Add to script.js - FormData API usage
     document.addEventListener('DOMContentLoaded', function() {
         const form = document.getElementById('task-form');
         
         // Form submission handler
         form.addEventListener('submit', function(event) {
             event.preventDefault(); // Prevent default form submission
             
             // Using FormData API
             const formData = new FormData(form);
             for (let [key, value] of formData.entries()) {
                 console.log(key, value);
             }
         });
     });
     ```

**Project Checklist for Day 6:**
- [ ] Form is structured with appropriate input elements
- [ ] Basic form submission is handled in JavaScript
- [ ] Input validation is implemented and working
- [ ] FormData API is used to handle form data

### Resources for Deeper Learning

**MDN Documentation:**
- [HTML form element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form)
- [FormData interface](https://developer.mozilla.org/en-US/docs/Web/API/FormData)
- [Input events](https://developer.mozilla.org/en-US/docs/Web/Events/input)

**Interactive Learning:**
- [JavaScript.info - Forms](https://javascript.info/forms)
- [MDN Web Docs - Using FormData](https://developer.mozilla.org/en-US/docs/Web/API/FormData/Using_FormData_Objects)

**Video Tutorials:**
- "HTML Forms and JavaScript" by Traversy Media
- "JavaScript Form Validation" by The Net Ninja

**Practice Exercises:**
- Build a user registration form with validation
- Create a search filter form with dynamic results
- Implement a multi-step form with progress indicators

---

## Day 7: Advanced Event Concepts

### Concepts

**Event Bubbling and Capturing:**
• **Event bubbling**: The event starts from the target element and bubbles up to the root
• **Event capturing**: The event starts from the root and captures down to the target element
• **addEventListener() options**: Use `{ capture: true }` to enable capturing, default is bubbling

**Event Delegation:**
• **Event delegation**: A technique where a single event listener is added to a parent element to manage events for multiple child elements
• Benefits: Improved performance, easier management of dynamic elements
• Common use cases: Navigation menus, tabbed interfaces, dynamically added content

**Preventing Default Behavior:**
• **event.preventDefault()**: A method that cancels the default action of an event (e.g., preventing form submission, link navigation)
• Common scenarios: Custom form validation, handling links with JavaScript

**Stopping Event Propagation:**
• **event.stopPropagation()**: A method that stops the event from bubbling up or capturing down the DOM tree
• Use cases: Preventing parent handlers from being notified of events on child elements

**AbortController and Signals:**
• **AbortController**: A built-in object that allows you to abort one or more DOM requests (e.g., fetch, event listeners)
• **signal**: An instance of AbortSignal, used to communicate with the controller

### Use Cases & Examples

**Real-world Applications:**
• Navigation menus and dropdowns
• Modal dialogs and popups
• Infinite scrolling and lazy loading
• Custom form controls and validation
• Game development and interactive animations

**Event Bubbling and Capturing Examples:**
```javascript
// Event capturing example
document.getElementById('parent').addEventListener('click', function(event) {
    console.log('Parent clicked (capturing)');
}, true); // true for capturing

// Event bubbling example
document.getElementById('child').addEventListener('click', function(event) {
    console.log('Child clicked (bubbling)');
}); // false or omitted for bubbling
```

**Event Delegation Examples:**
```javascript
// Event delegation example
document.getElementById('task-list').addEventListener('click', function(event) {
    if (event.target.classList.contains('delete-btn')) {
        // Handle delete button click
        const taskItem = event.target.closest('.task-item');
        taskItem.remove();
    }
});
```

**Preventing Default Behavior Examples:**
```javascript
// Preventing default form submission
document.getElementById('task-form').addEventListener('submit', function(event) {
    event.preventDefault();
    // Custom form submission logic
});

// Preventing default link navigation
document.querySelector('a').addEventListener('click', function(event) {
    event.preventDefault();
    // Custom link handling logic
});
```

**Stopping Event Propagation Examples:**
```javascript
// Stopping event propagation
document.getElementById('child').addEventListener('click', function(event) {
    event.stopPropagation();
    console.log('Child click event stopped');
});
```

### Interview Questions

1. **What is event delegation and why is it useful?**
   - Event delegation is a technique where a single event listener is added to a parent element to manage events for multiple child elements
   - It improves performance and simplifies event management, especially for dynamic content

2. **Explain the difference between event bubbling and capturing.**
   - Event bubbling: The event starts from the target element and bubbles up to the root
   - Event capturing: The event starts from the root and captures down to the target element
   - Default behavior of addEventListener() is to use bubbling

3. **How do you prevent the default behavior of an event?**
   - Use event.preventDefault() in the event handler to cancel the default action of the event

4. **What is the purpose of stopPropagation() method?**
   - The stopPropagation() method is used to stop the event from bubbling up or capturing down the DOM tree
   - It prevents parent handlers from being notified of events on child elements

5. **How can AbortController be used with event listeners?**
   - AbortController can be used to remove event listeners programmatically
   - By passing the signal property of an AbortController instance to an event listener, you can later call controller.abort() to remove the listener

### Practical Project: TODO App Advanced Event Handling

**Day 7 Implementation Tasks:**

1. **Event Delegation Implementation** (45 minutes)
   - Refactor TODO app to use event delegation for task item actions:
     ```javascript
     // Add to script.js - Event delegation
     document.addEventListener('DOMContentLoaded', function() {
         const taskList = document.getElementById('task-list');
         
         // Event delegation for task actions
         taskList.addEventListener('click', function(event) {
             const target = event.target;
             
             if (target.classList.contains('delete-btn')) {
                 // Handle delete button click
                 const taskItem = target.closest('.task-item');
                 taskItem.remove();
             } else if (target.classList.contains('task-text')) {
                 // Handle task text click (toggle complete)
                 const taskItem = target.closest('.task-item');
                 TaskStates.toggleComplete(taskItem);
             }
         });
     });
     ```

2. **Custom Form Validation** (45 minutes)
   - Implement custom form validation logic:
     ```javascript
     // Add to script.js - Custom form validation
     document.addEventListener('DOMContentLoaded', function() {
         const form = document.getElementById('task-form');
         const taskInput = document.getElementById('task-input');
         
         // Form submission handler
         form.addEventListener('submit', function(event) {
             event.preventDefault(); // Prevent default form submission
             
             const taskText = taskInput.value.trim();
             if (taskText.length < 3) {
                 alert('Task must be at least 3 characters long');
                 taskInput.focus();
                 return;
             }
             
             addNewTask(taskText);
             taskInput.value = ''; // Clear input
         });
     });
     ```

3. **AbortController Usage** (30 minutes)
   - Demonstrate usage of AbortController with event listeners:
     ```javascript
     // Add to script.js - AbortController usage
     document.addEventListener('DOMContentLoaded', function() {
         const controller = new AbortController();
         const signal = controller.signal;
         
         // Add event listener with AbortController signal
         document.getElementById('add-task-btn').addEventListener('click', function(event) {
             console.log('Add task button clicked');
         }, { signal });
         
         // Later, abort the controller to remove the listener
         // controller.abort();
     });
     ```

**Project Checklist for Day 7:**
- [ ] Implemented event delegation for task item actions
- [ ] Custom form validation logic is working
- [ ] Demonstrated usage of AbortController with event listeners

### Resources for Deeper Learning

**MDN Documentation:**
- [Event delegation](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events#event_delegation)
- [Event propagation](https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Introduction_to_events#event_propagation)
- [AbortController](https://developer.mozilla.org/en-US/docs/Web/API/AbortController)

**Interactive Learning:**
- [JavaScript.info - Event delegation](https://javascript.info/event-delegation)
- [CSS-Tricks - A Complete Guide to Event Delegation](https://css-tricks.com/event-delegation-make-events-bubble/)

**Video Tutorials:**
- "JavaScript Event Delegation" by Web Dev Simplified
- "Understanding Event Bubbling and Capturing" by The Net Ninja

**Practice Exercises:**
- Implement event delegation in a navigation menu
- Create a dynamic list with event delegation
- Build a form with custom validation and error handling

---

## Day 8: Dynamic Content & Data Management

### Concepts

**Working with Arrays:**
• **Array methods**: forEach, map, filter, reduce, find, some, every, etc.
• **Mutating vs non-mutating methods**: Understanding how methods like push, pop, shift, unshift, splice, and slice work
• **Destructuring**: Extracting values from arrays using destructuring assignment

**Template Literals:**
• **Template literals**: String literals allowing embedded expressions, multi-line strings, and string interpolation
• Syntax: Backticks (``) are used instead of quotes, `${expression}` for embedding expressions

**Local Storage:**
• **LocalStorage API**: A web storage API that allows you to store key/value pairs in a web browser with no expiration time
• **setItem() / getItem() / removeItem() / clear()**: Methods to manipulate local storage
• **JSON.stringify() / JSON.parse()**: Methods to serialize and deserialize objects for storage

**Dynamic Content Rendering:**
• **Rendering lists**: Using array methods to render lists of data (e.g., tasks) to the DOM
• **Conditional rendering**: Showing or hiding elements based on conditions (e.g., no tasks message)

### Use Cases & Examples

**Real-world Applications:**
• Managing and displaying lists of data (e.g., TODO items, products, messages)
• Storing user preferences and settings
• Caching data for offline access
• Implementing undo/redo functionality

**Array Manipulation Examples:**
```javascript
const tasks = ['Learn JavaScript', 'Build TODO app', 'Master DOM'];

// Adding a task
tasks.push('New task'); // Mutating method
const updatedTasks = [...tasks, 'Another new task']; // Non-mutating method

// Removing a task
tasks.splice(1, 1); // Removes 1 item at index 1

// Filtering tasks
const filteredTasks = tasks.filter(task => task.includes('JavaScript'));

// Mapping tasks to elements
const taskElements = tasks.map(task => `<li>${task}</li>`);

// Reducing tasks to a single value
const allTasksString = tasks.reduce((acc, task) => acc + ', ' + task);
```

**Template Literal Examples:**
```javascript
const task = 'Learn JavaScript';
const message = `Today's task: ${task}`;

// Multi-line string
const html = `
    <div class="task">
        <h2>${task}</h2>
        <button class="delete-btn">Delete</button>
    </div>
`;
```

**Local Storage Examples:**
```javascript
// Storing data
const taskData = JSON.stringify(tasks);
localStorage.setItem('tasks', taskData);

// Retrieving data
const storedData = localStorage.getItem('tasks');
const parsedTasks = JSON.parse(storedData);

// Removing data
localStorage.removeItem('tasks');

// Clearing all data
localStorage.clear();
```

**Dynamic Content Rendering Examples:**
```javascript
// Rendering tasks to the DOM
function renderTasks(tasks) {
    const taskList = document.getElementById('task-list');
    taskList.innerHTML = ''; // Clear existing tasks
    
    tasks.forEach(task => {
        const li = document.createElement('li');
        li.textContent = task;
        taskList.appendChild(li);
    });
}

// Conditional rendering example
function updateNoTasksMessage(tasks) {
    const noTasksMessage = document.getElementById('no-tasks-message');
    if (tasks.length === 0) {
        noTasksMessage.style.display = 'block';
    } else {
        noTasksMessage.style.display = 'none';
    }
}
```

### Interview Questions

1. **How do you add, remove, and modify items in an array?**
   - Use array methods like push, pop, shift, unshift, splice, and slice
   - Understand the difference between mutating and non-mutating methods

2. **What are template literals and how do you use them?**
   - Template literals are string literals allowing embedded expressions, multi-line strings, and string interpolation
   - Use backticks (``) instead of quotes, `${expression}` for embedding expressions

3. **How does local storage work and how do you use it?**
   - Local storage is a web storage API that allows you to store key/value pairs in a web browser with no expiration time
   - Use methods like setItem, getItem, removeItem, and clear to manipulate local storage

4. **What is the difference between JSON.stringify() and JSON.parse()?**
   - JSON.stringify() converts a JavaScript object or value to a JSON string
   - JSON.parse() parses a JSON string and constructs the JavaScript value or object described by the string

5. **How do you render a list of items to the DOM?**
   - Use array methods like forEach, map, or reduce to iterate over the items
   - Create and append elements to the DOM for each item

### Practical Project: TODO App Data Management

**Day 8 Implementation Tasks:**

1. **Array and Object Destructuring** (45 minutes)
   - Practice array and object destructuring:
     ```javascript
     // Array destructuring
     const colors = ['red', 'green', 'blue'];
     const [primary, secondary] = colors;
     
     // Object destructuring
     const task = { id: 1, text: 'Learn JavaScript', completed: false };
     const { text, completed } = task;
     ```

2. **Template Literal Usage** (45 minutes)
   - Use template literals for dynamic content:
     ```javascript
     const taskText = 'Learn JavaScript';
     const taskId = 1;
     const taskElement = `
         <div class="task" data-id="${taskId}">
             <span class="task-text">${taskText}</span>
             <button class="delete-btn">Delete</button>
         </div>
     `;
     document.getElementById('task-list').insertAdjacentHTML('beforeend', taskElement);
     ```

3. **Local Storage Integration** (30 minutes)
   - Integrate local storage for TODO app data persistence:
     ```javascript
     // Save tasks to local storage
     function saveTasksToLocalStorage(tasks) {
         localStorage.setItem('tasks', JSON.stringify(tasks));
     }
     
     // Load tasks from local storage
     function loadTasksFromLocalStorage() {
         const tasks = localStorage.getItem('tasks');
         return tasks ? JSON.parse(tasks) : [];
     }
     
     // Initial load
     document.addEventListener('DOMContentLoaded', function() {
         const tasks = loadTasksFromLocalStorage();
         renderTasks(tasks);
     });
     ```

**Project Checklist for Day 8:**
- [ ] Practiced array methods for data manipulation
- [ ] Used template literals for dynamic content
- [ ] Integrated local storage for data persistence

### Resources for Deeper Learning

**MDN Documentation:**
- [Working with arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [Template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)
- [Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API)

**Interactive Learning:**
- [JavaScript.info - Arrays](https://javascript.info/array)
- [JavaScript.info - Object basics](https://javascript.info/object-basics)

**Video Tutorials:**
- "JavaScript Array Methods" by Traversy Media
- "Local Storage in JavaScript" by The Net Ninja

**Practice Exercises:**
- Build a shopping cart with array and local storage integration
- Create a notes app with CRUD operations and data persistence
- Implement a quiz app with score tracking and local storage

---

## Day 9: DOM Performance & Modern Practices

### Concepts

**DocumentFragment:**
• **DocumentFragment**: A minimal document object that has no parent and is not part of the active document tree
• Used as a lightweight container for holding and manipulating a portion of the DOM

**Efficient DOM Updates:**
• Batch DOM updates to minimize reflows and repaints
• Use DocumentFragment to build and modify DOM structures off-screen
• Use requestAnimationFrame for visual updates

**Debouncing and Throttling:**
• **Debouncing**: Delaying the processing of events to limit the rate of execution (e.g., resize, scroll)
• **Throttling**: Ensuring a function is called at most once in a specified time period

**Modern JavaScript Features:**
• **Arrow functions**: Shorter syntax for writing functions, lexically binds `this`
• **Spread and rest operators**: `...` syntax for expanding and collecting elements
• **Destructuring**: Extracting values from arrays or objects into distinct variables

**Module Bundlers:**
• **Module bundlers**: Tools like Webpack, Rollup, or Parcel that bundle JavaScript files for usage in a browser
• Support for modern JavaScript features, code splitting, and asset optimization

### Use Cases & Examples

**Real-world Applications:**
• High-performance web applications with complex DOM manipulations
• Responsive and interactive user interfaces
• Applications with real-time data updates (e.g., chats, notifications)
• Progressive web apps (PWAs) with offline support

**DocumentFragment Examples:**
```javascript
// Using DocumentFragment for efficient DOM updates
const fragment = document.createDocumentFragment();

tasks.forEach(task => {
    const li = document.createElement('li');
    li.textContent = task;
    fragment.appendChild(li);
});

// Append all at once
document.getElementById('task-list').appendChild(fragment);
```

**Debouncing and Throttling Examples:**
```javascript
// Debouncing example
function debounce(func, delay) {
    let timeout;
    return function(...args) {
        const context = this;
        clearTimeout(timeout);
        timeout = setTimeout(() => func.apply(context, args), delay);
    };
}

// Throttling example
function throttle(func, limit) {
    let lastFunc;
    let lastRan;
    return function() {
        const context = this;
        const args = arguments;
        if (!lastRan) {
            func.apply(context, args);
            lastRan = Date.now();
        } else {
            clearTimeout(lastFunc);
            lastFunc = setTimeout(function() {
                if ((Date.now() - lastRan) >= limit) {
                    func.apply(context, args);
                    lastRan = Date.now();
                }
            }, limit - (Date.now() - lastRan));
        }
    };
}
```

### Interview Questions

1. **What is DocumentFragment and when would you use it?**
   - DocumentFragment is a minimal document object that has no parent and is not part of the active document tree
   - It is used as a lightweight container for holding and manipulating a portion of the DOM
   - Useful for efficient DOM updates, as changes to a DocumentFragment do not cause reflows or repaints

2. **How do you optimize DOM updates for performance?**
   - Batch DOM updates to minimize reflows and repaints
   - Use DocumentFragment to build and modify DOM structures off-screen
   - Use requestAnimationFrame for visual updates

3. **What is the difference between debouncing and throttling?**
   - Debouncing: Delaying the processing of events to limit the rate of execution (e.g., resize, scroll)
   - Throttling: Ensuring a function is called at most once in a specified time period
   - Both techniques are used to optimize performance and improve user experience

4. **Explain the use of arrow functions in modern JavaScript.**
   - Arrow functions provide a shorter syntax for writing functions
   - They lexically bind `this`, meaning `this` retains the value of the enclosing lexical context
   - Useful for preserving `this` in callbacks and methods

5. **What are module bundlers and why are they used?**
   - Module bundlers are tools like Webpack, Rollup, or Parcel that bundle JavaScript files for usage in a browser
   - They support modern JavaScript features, code splitting, and asset optimization
   - Used to improve performance, manage dependencies, and enable modern development workflows

### Practical Project: TODO App Performance Optimization

**Day 9 Implementation Tasks:**

1. **DocumentFragment Usage** (45 minutes)
   - Refactor TODO app to use DocumentFragment for batch DOM updates:
     ```javascript
     // Add to script.js - DocumentFragment usage
     document.addEventListener('DOMContentLoaded', function() {
         const taskList = document.getElementById('task-list');
         const fragment = document.createDocumentFragment();
         
         // Add tasks to fragment
         tasks.forEach(task => {
             const li = document.createElement('li');
             li.className = 'task-item';
             li.innerHTML = `
                 <span class="task-text">${task.text}</span>
                 <button class="delete-btn">Delete</button>
             `;
             fragment.appendChild(li);
         });
         
         // Append all at once
         taskList.appendChild(fragment);
     });
     ```

2. **Debouncing and Throttling Implementation** (45 minutes)
   - Implement debouncing and throttling for performance optimization:
     ```javascript
     // Add to script.js - Debouncing and throttling
     document.addEventListener('DOMContentLoaded', function() {
         const input = document.getElementById('task-input');
         
         // Debounced input handler
         const debouncedInputHandler = debounce(function(event) {
             console.log('Input value (debounced):', event.target.value);
         }, 300);
         
         input.addEventListener('input', debouncedInputHandler);
     });
     ```

3. **Modern JavaScript Features Practice** (30 minutes)
   - Practice using modern JavaScript features:
     ```javascript
     // Arrow functions and array methods
     const tasks = ['Learn JavaScript', 'Build TODO app', 'Master DOM'];
     const taskLengths = tasks.map(task => task.length);
     console.log('Task lengths:', taskLengths);
     
     // Destructuring and template literals
     const task = { id: 1, text: 'Learn JavaScript', completed: false };
     const { text, completed } = task;
     const message = `Task: ${text}, Completed: ${completed}`;
     console.log(message);
     ```

**Project Checklist for Day 9:**
- [ ] Used DocumentFragment for efficient DOM updates
- [ ] Implemented debouncing and throttling for performance optimization
- [ ] Practiced modern JavaScript features

### Resources for Deeper Learning

**MDN Documentation:**
- [DocumentFragment](https://developer.mozilla.org/en-US/docs/Web/API/DocumentFragment)
- [Debounce and throttle](https://developer.mozilla.org/en-US/docs/Web/API/Window/requestAnimationFrame#optimizing_performance_with_debouncing_and_throttling)
- [JavaScript language overview](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)

**Interactive Learning:**
- [JavaScript.info - Browser events](https://javascript.info/events)
- [JavaScript.info - Array methods](https://javascript.info/array-methods)
- [JavaScript.info - Object destructuring](https://javascript.info/destructuring-assignment#object-destructuring)

**Video Tutorials:**
- "JavaScript Performance Optimization" by Traversy Media
- "Understanding JavaScript Debouncing and Throttling" by The Net Ninja

**Practice Exercises:**
- Optimize a slow web page by implementing debouncing and throttling
- Refactor a project to use DocumentFragment for batch DOM updates
- Practice array and object destructuring in various scenarios

---

## Day 10: Advanced Features & React Preparation

### Concepts

**Component-like Thinking:**
• Breaking down the UI into reusable components
• Understanding props and state
• Component lifecycle methods and hooks (useState, useEffect)

**State Management Concepts:**
• Lifting state up vs. prop drilling
• Context API for global state management
• Introduction to Redux (actions, reducers, store)

**React Basics:**
• Creating functional components
• Using JSX syntax
• Handling events and forms in React

**Modern JavaScript Features Review:**
• Review of key modern JavaScript features used in React development (e.g., spread/rest operators, destructuring, arrow functions)

### Use Cases & Examples

**Real-world Applications:**
• Building reusable and composable UI components
• Managing complex state and side effects in applications
• Optimizing performance with memoization and lazy loading
• Integrating with APIs and handling asynchronous data

**Component Creation Example:**
```javascript
// Functional component example
function TaskItem({ task, onDelete }) {
    return (
        <div className="task-item">
            <span className="task-text">{task.text}</span>
            <button className="delete-btn" onClick={() => onDelete(task.id)}>Delete</button>
        </div>
    );
}
```

**State Management Example:**
```javascript
// Using useState and useEffect hooks
function TaskList() {
    const [tasks, setTasks] = useState([]);
    
    useEffect(() => {
        // Fetch tasks from API or local storage
        const fetchedTasks = loadTasksFromLocalStorage();
        setTasks(fetchedTasks);
    }, []); // Empty dependency array means this effect runs once on mount
    
    const handleDelete = (taskId) => {
        // Delete task logic
        const updatedTasks = tasks.filter(task => task.id !== taskId);
        setTasks(updatedTasks);
        saveTasksToLocalStorage(updatedTasks);
    };
    
    return (
        <div id="task-list">
            {tasks.map(task => (
                <TaskItem key={task.id} task={task} onDelete={handleDelete} />
            ))}
        </div>
    );
}
```

### Interview Questions

1. **What is component-based architecture?**
   - A software design approach where the user interface is divided into independent, reusable components
   - Each component manages its own state and logic, and can be composed to build complex UIs

2. **How do you manage state in a React application?**
   - Using React's built-in state management (useState, useReducer) for local component state
   - Lifting state up to common ancestors to share state between components
   - Using Context API or external libraries (e.g., Redux) for global state management

3. **What are props in React?**
   - Short for "properties", props are read-only attributes used to pass data from parent to child components
   - Props are used to configure components and render dynamic data

4. **Explain the useEffect hook.**
   - A built-in hook that lets you perform side effects in function components
   - It can be used for data fetching, subscriptions, or manually changing the DOM
   - The effect runs after the render, and you can optionally clean up after it

5. **What is the purpose of the key prop in React lists?**
   - The key prop is a unique identifier for each element in a list
   - It helps React optimize rendering by identifying which items have changed, are added, or are removed

### Practical Project: TODO App Refactor for React

**Day 10 Implementation Tasks:**

1. **Component Refactoring** (45 minutes)
   - Refactor TODO app to use component-based architecture:
     ```javascript
     // TaskItem component
     function TaskItem({ task, onDelete }) {
         return (
             <div className="task-item">
                 <span className="task-text">{task.text}</span>
                 <button className="delete-btn" onClick={() => onDelete(task.id)}>Delete</button>
             </div>
         );
     }
     
     // TaskList component
     function TaskList() {
         const [tasks, setTasks] = useState([]);
         
         useEffect(() => {
             const fetchedTasks = loadTasksFromLocalStorage();
             setTasks(fetchedTasks);
         }, []);
         
         const handleDelete = (taskId) => {
             const updatedTasks = tasks.filter(task => task.id !== taskId);
             setTasks(updatedTasks);
             saveTasksToLocalStorage(updatedTasks);
         };
         
         return (
             <div id="task-list">
                 {tasks.map(task => (
                     <TaskItem key={task.id} task={task} onDelete={handleDelete} />
                 ))}
             </div>
         );
     }
     ```

2. **State Management Implementation** (45 minutes)
   - Implement state management using hooks:
     ```javascript
     // Using useState and useEffect in TaskList component
     function TaskList() {
         const [tasks, setTasks] = useState([]);
         
         useEffect(() => {
             const fetchedTasks = loadTasksFromLocalStorage();
             setTasks(fetchedTasks);
         }, []);
         
         const handleDelete = (taskId) => {
             const updatedTasks = tasks.filter(task => task.id !== taskId);
             setTasks(updatedTasks);
             saveTasksToLocalStorage(updatedTasks);
         };
         
         return (
             <div id="task-list">
                 {tasks.map(task => (
                     <TaskItem key={task.id} task={task} onDelete={handleDelete} />
                 ))}
             </div>
         );
     }
     ```

3. **React Features Practice** (30 minutes)
   - Practice using React features:
     ```javascript
     // Custom hook example
     function useTasks() {
         const [tasks, setTasks] = useState([]);
         
         useEffect(() => {
             const fetchedTasks = loadTasksFromLocalStorage();
             setTasks(fetchedTasks);
         }, []);
         
         const addTask = (task) => {
             const updatedTasks = [...tasks, task];
             setTasks(updatedTasks);
             saveTasksToLocalStorage(updatedTasks);
         };
         
         return { tasks, addTask };
     }
     ```

**Project Checklist for Day 10:**
- [ ] Refactored TODO app to use component-based architecture
- [ ] Implemented state management using hooks
- [ ] Practiced React features and concepts

### Resources for Deeper Learning

**MDN Documentation:**
- [React - A JavaScript library for building user interfaces](https://reactjs.org/)
- [Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)
- [Rendering Elements](https://reactjs.org/docs/rendering-elements.html)
- [Components and Props](https://reactjs.org/docs/components-and-props.html)
- [State and Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)
- [Handling Events](https://reactjs.org/docs/handling-events.html)
- [Forms](https://reactjs.org/docs/forms.html)
- [Lifting State Up](https://reactjs.org/docs/lifting-state-up.html)
- [Composition vs inheritance](https://reactjs.org/docs/composition-vs-inheritance.html)

**Interactive Learning:**
- [React Official Tutorial](https://reactjs.org/tutorial/tutorial.html)
- [JavaScript.info - React](https://javascript.info/react)

**Video Tutorials:**
- "React JS Crash Course" by Traversy Media
- "React - The Complete Guide" by Academind

**Practice Exercises:**
- Build a complete TODO app with React
- Create a weather app using a public API and React
- Implement a chat application with real-time messaging and React

---

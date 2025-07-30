# 10-Day JavaScript DOM Mastery Schedule
## Pre-Requisite to React for BCA Third Semester Students

*Total Daily Effort: 2 Hours Maximum | Self-Learning with Mentor Guidance*

---

### Day 1: DOM Fundamentals & Document Structure
#### Concept: Understanding the DOM Tree
• **What is DOM**: Document Object Model as a programming interface for HTML documents that represents the structure and content of a document on the web
• **DOM Tree Structure**: Parent-child relationships, nodes, elements, and attributes forming a hierarchical tree representation
• **Browser Rendering**: How HTML becomes a DOM tree in memory that JavaScript can manipulate through APIs
• **Key Concepts**: Document object (root of the document), Window object (browser representation), Node types (Element, Text, Attribute, Comment)
• **DOM vs HTML**: DOM is the live representation in memory while HTML is the markup language text

**Essential Resources:**
- [MDN DOM Introduction](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
- [JavaScript DOM Tutorial - YouTube](https://www.youtube.com/watch?v=0ik6X4DJKCc)
- [DOM Tree Visualizer](https://software.hixie.ch/utilities/js/live-dom-viewer/)

#### Interview Questions:
1. What is the difference between HTML and DOM?
2. Explain the DOM tree structure with an example
3. What are different types of nodes in DOM (Element, Text, Attribute, Comment)?
4. How does the browser create DOM from HTML?
5. What is the relationship between the Document and Window objects?
6. Why is the DOM called a "programming interface"?

#### Practical Project - Day 1:
**Project: Personal Task Manager Foundation**
1. Open browser DevTools (F12) and navigate to the Elements tab to inspect the provided HTML structure. Identify and document the three main node types: Element nodes (like `<div>`, `<input>`), Text nodes (content inside elements), and Attribute nodes (like `id="task-input"`).
2. Practice DOM tree navigation by clicking through the `.todo-container` hierarchy to understand parent-child relationships. Use the DevTools to expand/collapse elements and observe how `.input-container` is a child of `.todo-container` and parent to `#task-input`.
3. Create a `script.js` file in your project directory and add the script link to your HTML (already provided). Open the browser console and type `console.log(document)` to explore the document object properties.
4. Access specific elements using the console by typing `document.getElementById('task-input')` and observe the returned Element object. Practice accessing the `window` object and explore properties like `window.location` and `window.document`.
5. Use DevTools to modify the DOM structure temporarily by adding/removing elements and observe how changes affect the page. Practice identifying different node types by right-clicking elements and selecting "Inspect Element".

---

### Day 2: Selecting DOM Elements
#### Concept: Element Selection Methods
• **getElementById()**: Fastest method for unique element selection, returns single Element or null
• **querySelector()**: Returns the first Element matching specified CSS selectors using depth-first pre-order traversal, or null if no matches
• **querySelectorAll()**: Returns static NodeList of all elements matching selectors, not live collection
• **getElementsByClassName()** and **getElementsByTagName()**: Return live HTMLCollections that update automatically
• **Performance & Security**: querySelector syntax validation throws SyntaxError for invalid selectors, CSS.escape() for attribute values

**Essential Resources:**
- [MDN Element Selection](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)
- [JavaScript Selectors Explained - YouTube](https://www.youtube.com/watch?v=JlgLDfINXvY)
- [CSS Selectors Reference](https://www.w3schools.com/cssref/css_selectors.asp)

#### Interview Questions:
1. What's the difference between `querySelector()` and `getElementById()` in terms of performance and return values?
2. When would you use `querySelectorAll()` vs `getElementsByClassName()` and what are the differences between NodeList and HTMLCollection?
3. How does querySelector handle complex CSS selectors and what happens with invalid selectors?
4. How do you safely select elements when class or id values are not valid CSS identifiers?
5. What is depth-first pre-order traversal and how does it affect querySelector results?

#### Practical Project - Day 2:
**Element Selection Mastery**
1. Use `document.getElementById('task-input')` to select the input field and log its properties to console. Compare this with `document.querySelector('#task-input')` and measure performance using `console.time()` and `console.timeEnd()`.
2. Practice advanced CSS selectors by selecting `.input-container > input` (direct child) and `#task-list li:nth-child(odd)` (pseudo-selectors). Test these selectors in the console and observe what elements they return.
3. Store references to key elements in variables: `const taskInput = document.getElementById('task-input')` and similar for button and list. Create a function that logs each element's `nodeName`, `nodeType`, and `className` properties.
4. Use `document.querySelectorAll()` to select multiple elements and explore the returned NodeList. Practice converting NodeList to Array using `Array.from()` and understand the difference between live HTMLCollections and static NodeLists.
5. Create a selector testing function that tries different selection methods on the same element and compares their results. Test edge cases like selecting non-existent elements and observe how different methods handle errors.

---

### Day 3: Manipulating Element Content & Attributes
#### Concept: Content and Attribute Manipulation
• **innerHTML Security Risk**: Using innerHTML with user-supplied data creates XSS vulnerabilities; sanitizer libraries recommended for untrusted content
• **textContent vs innerHTML**: textContent inserts as raw text preventing HTML parsing, innerHTML renders HTML tags which can execute scripts
• **innerText vs textContent**: innerText respects styling (hidden elements), textContent gets all text including hidden content
• **Attribute Manipulation**: `getAttribute()`, `setAttribute()`, `removeAttribute()` for standard and custom attributes
• **Dataset API**: Modern approach using `element.dataset.propertyName` for data-* attributes
• **Value Property**: Direct access to form element values, more efficient than getAttribute('value')

**Essential Resources:**
- [MDN innerHTML vs textContent](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML)
- [XSS Prevention in JavaScript](https://owasp.org/www-community/xss-filter-evasion-cheatsheet)
- [Data Attributes Tutorial - YouTube](https://www.youtube.com/watch?v=R9eQZ4PsEDw)

#### Interview Questions:
1. Why is innerHTML a security risk when handling user input and how does textContent prevent XSS attacks?
2. When would you use data attributes vs regular attributes and what are the benefits of the dataset API?
3. How do you safely insert user-generated content into DOM without creating security vulnerabilities?
4. What's the difference between `innerText` and `textContent` in terms of CSS styling and performance?
5. How does using textContent instead of innerHTML help prevent cross-site scripting attacks?
6. What happens when you use innerHTML with `<script>` tags vs other potentially malicious HTML?

#### Practical Project - Day 3:
**Dynamic Content & Attribute Manipulation**
1. Get the task input value using `taskInput.value` and create a new list item using `createElement('li')`. Practice safely inserting user text with `textContent` and demonstrate security by testing with malicious input like `<script>alert('XSS')</script>`.
2. Experiment with `innerHTML` vs `textContent` by creating two identical tasks using both methods with HTML content. Observe how `innerHTML` renders HTML tags while `textContent` treats them as plain text for security.
3. Add custom data attributes to each task using `setAttribute('data-created', Date.now())` and `setAttribute('data-priority', 'medium')`. Practice retrieving this data using both `getAttribute('data-created')` and the modern `dataset.created` API.
4. Create a task information tooltip that appears on hover by accessing data attributes with `dataset`. Use `element.dataset.created` to display the creation timestamp and `element.dataset.priority` to show priority level.
5. Practice form element manipulation by programmatically setting and getting the input value, placeholder text, and disabled state. Create a function that validates input length and provides visual feedback using attribute manipulation.

---

### Day 4: CSS Class & Style Manipulation
#### Concept: Dynamic Styling with JavaScript
• **classList API**: Read-only property returning live DOMTokenList with `add()`, `remove()`, `toggle()`, `contains()`, `replace()` methods
• **DOMTokenList Features**: Support for multiple class operations with spread syntax, conditional toggle with second parameter
• **className Property**: String-based class manipulation, less flexible than classList but still widely used
• **style Property**: Inline style manipulation with camelCase conversion (backgroundColor vs background-color)
• **getComputedStyle()**: Reading actual applied styles including CSS cascade, inheritance, and computed values
• **CSS Custom Properties**: Manipulating CSS variables with `setProperty()` and `getPropertyValue()` methods

**Essential Resources:**
- [MDN classList API](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)
- [CSS Custom Properties with JS](https://css-tricks.com/updating-a-css-variable-with-javascript/)
- [Dynamic Styling Tutorial - YouTube](https://www.youtube.com/watch?v=9-hP8gXUwMc)

#### Interview Questions:
1. What are the advantages of `classList` over `className` and how does DOMTokenList work?
2. How do you read computed styles vs inline styles and what's the difference?
3. When should you use classes vs inline styles for dynamic changes and why?
4. How can you manipulate CSS custom properties with JavaScript using setProperty()?
5. What are the benefits of using classList.toggle() with a conditional second parameter?
6. How does the live DOMTokenList update when class attributes change?

#### Practical Project - Day 4:
**Dynamic Styling & Theme Management**
1. Practice using `classList.toggle('completed')` on task list items when clicked to mark them as complete. Test the difference between `classList.add()`, `classList.remove()`, and `classList.contains()` methods with the existing `.completed` class.
2. Implement a theme switcher button that toggles between light and dark modes using `classList.toggle()` on the body element. Create corresponding CSS classes and observe how `getComputedStyle(element).backgroundColor` reads the current applied styles.
3. Use the `style` property to dynamically change inline styles like `element.style.backgroundColor = 'red'` for urgent tasks. Practice converting CSS property names to camelCase (background-color becomes backgroundColor).
4. Add CSS custom properties to your stylesheet and manipulate them with JavaScript using `document.documentElement.style.setProperty('--main-color', '#ff0000')`. Create a color picker that changes the theme colors in real-time.
5. Save the user's theme preference in localStorage and restore it on page load using `localStorage.setItem()` and `localStorage.getItem()`. Practice reading computed styles to determine the current theme state automatically.

---

### Day 5: Event Handling Fundamentals & DOM Events Understanding
#### Concept: Interactive Web Applications & DOM Event System
• **addEventListener()**: Modern recommended approach allowing multiple listeners, with options for capture/bubble phases and AbortSignal cleanup
• **Event Object Interface**: All handlers receive Event object (or derived interface) with properties like target, type, timeStamp, bubbles
• **Event Registration**: Two approaches - onevent properties (single handler) vs addEventListener() (multiple handlers with better control)
• **Event Phases**: Capture phase (top-down), target phase, and bubble phase (bottom-up) through DOM tree
• **Event Types by Category**: Mouse (click, dblclick, mousedown, mouseup), Keyboard (keydown, keyup), Form (submit, input, change), Window (load, resize, scroll)
• **Memory Management**: removeEventListener() importance for preventing memory leaks, especially with anonymous functions
• **AbortSignal Pattern**: Modern cleanup approach using AbortController for removing multiple event listeners simultaneously

**Essential Resources:**
- [MDN Event Handling](https://developer.mozilla.org/en-US/docs/Web/Events/Event_handlers)
- [JavaScript Events Explained - YouTube](https://www.youtube.com/watch?v=XF1_MlZ5l6M)
- [Event Reference](https://developer.mozilla.org/en-US/docs/Web/Events)
- [DOM Events Comprehensive Guide](https://javascript.info/introduction-browser-events)

#### Interview Questions:
1. What's the difference between `onclick` property and `addEventListener()` in terms of multiple handlers and control?
2. Explain the three phases of event propagation (capture, target, bubble) and when each occurs?
3. When and why would you use `preventDefault()` and `stopPropagation()`?
4. How do you properly remove event listeners and why is it important for memory management?
5. What are the different categories of DOM events and their typical use cases?
6. How does the AbortSignal pattern help with event listener cleanup?
7. What Event object properties are available in all event handlers and what do they represent?

#### Practical Project - Day 5:
**Interactive Event-Driven Application**
1. Add a click event listener to the "Add Task" button using `addEventListener('click', function)` and log the event object properties. Practice accessing `event.target`, `event.type`, and `event.timeStamp` to understand the event structure.
2. Implement Enter key support by adding a `keydown` event listener to the task input that checks for `event.key === 'Enter'`. Use `event.preventDefault()` to prevent form submission and call your task addition function instead.
3. Create hover effects on the `.todo-container` using `mouseenter` and `mouseleave` events to change background color. Practice different mouse events like `mousedown`, `mouseup`, and `mousemove` to track user interactions.
4. Implement form validation that prevents empty task submission by checking input value length in the event handler. Provide visual feedback by adding/removing CSS classes and use `event.stopPropagation()` to prevent event bubbling.
5. Add keyboard shortcuts using global `keydown` events: Escape to clear input and Ctrl+Enter to add tasks. Practice event detection with `event.ctrlKey`, `event.shiftKey`, and `event.key` combinations for advanced user interactions.

---

### Day 6: Advanced Event Handling, Delegation & MVC Architecture Refactoring
#### Concept: Efficient Event Management & Code Organization
• **Event Delegation**: Leveraging event bubbling to handle events on parent elements for dynamically created child elements
• **Event Bubbling & Capturing**: Three-phase event flow - capture (top-down), target, and bubble (bottom-up) through DOM hierarchy
• **Custom Events**: Creating synthetic events with CustomEvent constructor and dispatchEvent() method for component communication
• **AbortSignal Integration**: Modern cleanup pattern using AbortController for removing multiple event listeners simultaneously
• **Performance Optimization**: Debouncing (delay execution until inactivity) and throttling (limit execution frequency) techniques
• **MVC Architecture**: Separation of concerns - Model (data/business logic), View (DOM/presentation), Controller (events/coordination)
• **Benefits of MVC**: Improved maintainability, testability, scalability, and code organization for complex applications

**Essential Resources:**
- [Event Delegation Explained](https://javascript.info/event-delegation)
- [Custom Events Tutorial - YouTube](https://www.youtube.com/watch?v=92OOGugZIYo)
- [Debouncing vs Throttling](https://css-tricks.com/debouncing-throttling-explained-examples/)
- [MVC Pattern in JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/MVC)
- [JavaScript MVC Architecture Tutorial](https://www.taniarascia.com/javascript-mvc-todo-app/)

#### Interview Questions:
1. What is event delegation and when should you use it for dynamic content?
2. Explain the three phases of event propagation and how event.stopPropagation() affects each phase
3. How do you create and dispatch custom events with data payload using CustomEvent?
4. What's the difference between debouncing and throttling and when to use each?
5. What is the MVC pattern and how does it improve code maintainability?
6. How do you separate data logic from presentation logic in JavaScript applications?
7. How does the AbortSignal pattern help with memory management in event handling?
8. How does MVC architecture prepare you for React's component-based thinking?

#### Practical Project - Day 6:
**Event Delegation & MVC Architecture Implementation**
1. Implement event delegation by adding a single click listener to `#task-list` that handles all delete button clicks using `event.target.matches('.delete-btn')`. Practice checking event targets and understand how event bubbling allows parent elements to handle child events.
2. Create custom events using `new CustomEvent('taskAdded', {detail: {taskData}})` and dispatch them with `element.dispatchEvent()`. Listen for these custom events in different parts of your application to create loose coupling between components.
3. Implement debouncing for search functionality using `setTimeout` and `clearTimeout` to limit API calls or filtering operations. Create a debounce utility function that delays execution until the user stops typing for 300ms.
4. Create separate `model.js` file with a TaskModel class that handles data operations (add, delete, update tasks) and localStorage persistence. Move all task data management logic from your main script to this dedicated Model layer.
5. Refactor DOM manipulation into `view.js` with a TaskView class responsible for rendering tasks and updating the UI. Create `controller.js` to coordinate between Model and View, handling all event listeners and application flow control.

---

### Day 7: DOM Traversal & Node Relationships
#### Concept: Navigating the DOM Tree
• **Parent-Child Relationships**: `parentElement` (Element only), `parentNode` (all Node types), `children` (Element HTMLCollection), `childNodes` (all Node NodeList)
• **Sibling Navigation**: `nextElementSibling`/`previousElementSibling` (Element only), `nextSibling`/`previousSibling` (all Node types including text nodes)
• **Tree Walking**: `firstElementChild`/`lastElementChild` (Element only), `firstChild`/`lastChild` (all Node types)
• **Node vs Element**: Element properties filter out text/comment nodes, Node properties include all node types
• **Closest Method**: `element.closest(selector)` traverses up the ancestor chain until it finds a matching element or reaches document root
• **Performance Considerations**: DOM traversal is generally faster than re-querying with selectors for related elements

**Essential Resources:**
- [MDN DOM Traversal](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Locating_DOM_elements_using_selectors)
- [Element vs Node Properties](https://javascript.info/dom-navigation)

#### Interview Questions:
1. What's the difference between `children` and `childNodes` in terms of what node types they include?
2. How do you find the closest ancestor element with a specific class using the closest() method?
3. When would you use DOM traversal vs `querySelector()` for performance optimization?
4. Explain the difference between Element properties (like nextElementSibling) and Node properties (like nextSibling)?
5. How does the closest() method work and what does it return when no match is found?
6. Why might DOM traversal be more efficient than re-querying the DOM in certain scenarios?

#### Practical Project - Day 7:
**DOM Navigation & Task Organization**
1. Practice DOM traversal by navigating from task list items to their parent container using `parentElement` and finding sibling tasks with `nextElementSibling`. Log each element's relationship properties to understand the DOM tree structure.
2. Implement a feature that highlights the entire `.todo-container` when hovering over any task using the `closest()` method. Practice finding ancestor elements with `closest('.todo-container')` and observe the traversal path.
3. Add task priority levels by creating priority indicators (high, medium, low) and use `firstElementChild` to access the first child of each task. Practice the difference between `children` and `childNodes` when accessing task elements.
4. Create keyboard navigation (arrow keys) between tasks using `nextElementSibling` and `previousElementSibling` instead of re-querying the DOM. Implement focus management that moves between task items without using `querySelector`.
5. Build a task grouping feature that uses DOM traversal to organize related tasks by priority or category. Practice using `parentElement.children` to access all sibling tasks and group them dynamically.

---

### Day 8: Creating & Removing DOM Elements
#### Concept: Dynamic Content Generation
* **createElement()**: Creating new elements programmatically
* **appendChild()** vs **append()**: Adding elements to DOM
* **insertBefore()**, **insertAdjacentElement()**: Precise element positioning
* **removeChild()** vs **remove()**: Element removal methods
* **cloneNode()**: Duplicating elements efficiently
* **Performance Optimization**: Batch operations and efficient DOM updates

**Essential Resources:**
- [MDN Creating DOM Elements](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)
- [DOM Manipulation Best Practices](https://www.youtube.com/watch?v=wiozYyXQEVk)
- [Efficient DOM Manipulation](https://javascript.info/modifying-document)

#### Interview Questions:
1. What's the difference between `appendChild()` and `append()`?
2. How do you efficiently create multiple elements at once?
3. What are the performance implications of frequent DOM manipulations?
4. When should you batch DOM operations for better performance?

#### Practical Project - Day 8:
**Dynamic Content Creation & Management**
1. Practice creating new task list items using `createElement('li')` and adding delete buttons with `createElement('button')` and the existing `.delete-btn` class. Compare performance between `appendChild()` and `append()` when adding multiple elements to your task list.
2. Experiment with precise element positioning using `insertBefore()` to add tasks at specific positions and `insertAdjacentElement()` with different positions ('beforebegin', 'afterbegin', 'beforeend', 'afterend'). Create a function that inserts high-priority tasks at the top of the list automatically.
3. Implement efficient element removal using both `removeChild()` and the modern `remove()` method when deleting tasks. Practice the difference between removing elements from DOM vs just hiding them with CSS for performance considerations.
4. Use `cloneNode(true)` to duplicate existing task elements and modify their content for task templates or recurring tasks. Compare deep cloning (with children) vs shallow cloning and understand when each is appropriate.
5. Implement batch DOM operations by creating multiple elements in memory before adding them to the DOM in a single operation. Practice drag-and-drop task reordering and add real-time search filtering that shows/hides tasks based on user input.

---

### Day 9: Form Handling & Validation
#### Concept: Interactive Forms and Data Validation
* **Form Events**: submit, change, input, focus, blur
* **Form Data**: FormData API, form serialization
* **Validation API**: Constraint validation, custom validity
* **Input Types**: Modern HTML5 input types and their JavaScript integration
* **Real-time Validation**: Providing immediate feedback to users

**Essential Resources:**
- [MDN Form Validation](https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation)
- [FormData API Tutorial - YouTube](https://www.youtube.com/watch?v=5-x4OUM-SP8)
- [Custom Form Validation](https://css-tricks.com/form-validation-ux-html-css/)

#### Interview Questions:
1. How do you implement custom form validation in JavaScript?
2. What's the difference between `change` and `input` events?
3. How do you serialize form data for AJAX submission?
4. What are the benefits of the Constraint Validation API?

#### Practical Project - Day 9:
**Advanced Form Handling & Validation**
1. Enhance the existing task input with real-time validation using `input` and `blur` events to provide immediate feedback for empty or invalid entries. Practice using the Constraint Validation API with `setCustomValidity()` and `reportValidity()` methods on your task input field.
2. Create an advanced task creation form with additional fields (due date using `<input type="date">`, priority dropdown, category selection) using modern HTML5 input types. Practice accessing form values using the `FormData` constructor and `Object.fromEntries()` for easy data collection.
3. Implement real-time task search functionality that filters existing tasks as the user types using `input` events and string matching methods. Create a search input that shows/hides tasks based on text content using `textContent.toLowerCase().includes()` for case-insensitive matching.
4. Add form validation that checks for minimum task length, validates due dates (no past dates), and ensures priority selection before submission. Use `checkValidity()` and custom error messages with `setCustomValidity()` to provide specific feedback for each validation rule.
5. Create import/export functionality using the File API to read JSON task data from uploaded files and download current tasks as JSON. Practice using `FileReader` for importing and `Blob` with `URL.createObjectURL()` for exporting task data to maintain data portability.

---

### Day 10: Performance Optimization & React Preparation
#### Concept: Efficient DOM Manipulation & Modern Patterns
* **Virtual DOM Concept**: Understanding React's optimization strategy
* **Component Thinking**: Breaking UI into reusable components
* **State Management**: Tracking and updating application state
* **Event Patterns**: Preparing for React's synthetic events
* **Performance Best Practices**: Minimizing reflows and repaints

**Essential Resources:**
- [Debouncing and Throttling Explained](https://css-tricks.com/debouncing-throttling-explained-examples/)
- [Using requestAnimationFrame](https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame)
- [localStorage API](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
- [Error Handling in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [Component-Based Architecture](https://vuejs.org/v2/guide/components.html)

#### Interview Questions:
1. What are some common performance bottlenecks in web applications?
2. How do you implement debouncing and throttling in JavaScript?
3. What is the purpose of requestAnimationFrame()?
4. How do you handle errors in JavaScript applications?
5. What are the benefits of component-based architecture?

#### Practical Project - Day 10:
**Performance Optimization & Component Architecture**
1. Refactor your task manager into component-like patterns by creating separate functions for task creation, rendering, and state management. Practice separating concerns by moving each functionality into dedicated functions with clear responsibilities and interfaces.
2. Implement performance optimization by adding debounced search (delays execution until user stops typing) and batching DOM updates when adding multiple tasks. Use `requestAnimationFrame()` for smooth animations and measure performance improvements with DevTools Performance tab.
3. Add comprehensive data persistence with localStorage that saves/restores all task data, user preferences, and application state on page load. Create error handling for localStorage quota exceeded and corrupted data scenarios using try-catch blocks.
4. Implement advanced error handling for edge cases like network failures, invalid user input, and DOM manipulation errors. Create user-friendly error messages and fallback behaviors that maintain application stability in all scenarios.
5. Complete your final project by adding a deployment-ready build process and creating a presentation showcasing your DOM mastery. Deploy your project using GitHub Pages and document all features, code architecture, and performance optimizations in a comprehensive README.
# 10-Day JavaScript DOM Mastery Schedule
## Pre-Requisite to React for BCA Third Semester Students

*Total Daily Effort: 2 Hours Maximum | Self-Learning with Mentor Guidance*

---

### Day 1: DOM Fundamentals & Document Structure
#### Concept: Understanding the DOM Tree
* **What is DOM**: Document Object Model as a programming interface for HTML documents
* **DOM Tree Structure**: Parent-child relationships, nodes, elements, and attributes
* **Browser Rendering**: How HTML becomes a DOM tree that JavaScript can manipulate
* **Key Concepts**: Document, Window, Node types (Element, Text, Attribute)

**Essential Resources:**
- [MDN DOM Introduction](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
- [JavaScript DOM Tutorial - YouTube](https://www.youtube.com/watch?v=0ik6X4DJKCc)
- [DOM Tree Visualizer](https://software.hixie.ch/utilities/js/live-dom-viewer/)

#### Interview Questions:
1. What is the difference between HTML and DOM?
2. Explain the DOM tree structure with an example
3. What are different types of nodes in DOM?
4. How does the browser create DOM from HTML?

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
* **getElementById()**: Fastest method for unique element selection
* **querySelector()**: CSS selector-based selection (most versatile)
* **querySelectorAll()**: Multiple element selection with NodeList
* **getElementsByClassName()** and **getElementsByTagName()**: Live HTMLCollections
* **Performance Considerations**: When to use each method

**Essential Resources:**
- [MDN Element Selection](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)
- [JavaScript Selectors Explained - YouTube](https://www.youtube.com/watch?v=JlgLDfINXvY)
- [CSS Selectors Reference](https://www.w3schools.com/cssref/css_selectors.asp)

#### Interview Questions:
1. What's the difference between `querySelector()` and `getElementById()`?
2. When would you use `querySelectorAll()` vs `getElementsByClassName()`?
3. What is the difference between NodeList and HTMLCollection?
4. How do you select elements with complex CSS selectors?

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
* **textContent vs innerHTML**: Security implications and use cases
* **innerText vs textContent**: Styling considerations and performance
* **Attribute Manipulation**: `getAttribute()`, `setAttribute()`, `removeAttribute()`
* **Data Attributes**: Using `dataset` for custom data storage
* **Value Property**: Form element value manipulation

**Essential Resources:**
- [MDN innerHTML vs textContent](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML)
- [XSS Prevention in JavaScript](https://owasp.org/www-community/xss-filter-evasion-cheatsheet)
- [Data Attributes Tutorial - YouTube](https://www.youtube.com/watch?v=R9eQZ4PsEDw)

#### Interview Questions:
1. What's the security difference between `innerHTML` and `textContent`?
2. When would you use data attributes vs regular attributes?
3. How do you safely insert user-generated content into DOM?
4. What's the difference between `innerText` and `textContent`?

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
* **classList API**: `add()`, `remove()`, `toggle()`, `contains()`
* **className Property**: String-based class manipulation
* **style Property**: Inline style manipulation and camelCase conversion
* **getComputedStyle()**: Reading actual applied styles
* **CSS Custom Properties**: Manipulating CSS variables with JavaScript

**Essential Resources:**
- [MDN classList API](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)
- [CSS Custom Properties with JS](https://css-tricks.com/updating-a-css-variable-with-javascript/)
- [Dynamic Styling Tutorial - YouTube](https://www.youtube.com/watch?v=9-hP8gXUwMc)

#### Interview Questions:
1. What are the advantages of `classList` over `className`?
2. How do you read computed styles vs inline styles?
3. When should you use classes vs inline styles for dynamic changes?
4. How can you manipulate CSS custom properties with JavaScript?

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
* **addEventListener()**: Modern event handling approach
* **Event Types**: click, input, change, submit, keyboard events
* **Event Object**: `event.target`, `event.preventDefault()`, `event.stopPropagation()`
* **Removing Event Listeners**: `removeEventListener()` and memory management
* **Event Handler Context**: `this` keyword in event handlers
* **DOM Events Deep Dive**: Understanding browser event lifecycle, event phases, and performance implications
* **Mouse Events**: click, dblclick, mousedown, mouseup, mouseover, mouseout, mousemove
* **Keyboard Events**: keydown, keyup, keypress - handling user input and shortcuts
* **Form Events**: submit, reset, focus, blur, change, input - creating interactive forms
* **Window Events**: load, resize, scroll - responding to browser and viewport changes

**Essential Resources:**
- [MDN Event Handling](https://developer.mozilla.org/en-US/docs/Web/Events/Event_handlers)
- [JavaScript Events Explained - YouTube](https://www.youtube.com/watch?v=XF1_MlZ5l6M)
- [Event Reference](https://developer.mozilla.org/en-US/docs/Web/Events)
- [DOM Events Comprehensive Guide](https://javascript.info/introduction-browser-events)
- [Event Types and Browser Compatibility](https://developer.mozilla.org/en-US/docs/Web/Events)

#### Interview Questions:
1. What's the difference between `onclick` and `addEventListener()`?
2. Explain event bubbling and event capturing
3. When and why would you use `preventDefault()`?
4. How do you remove event listeners and why is it important?
5. What are the different types of DOM events and when do they fire?
6. How do mouse events differ from keyboard events in terms of handling?
7. What is the event lifecycle in the browser?

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
* **Event Delegation**: Handling events on parent elements for dynamic content
* **Event Bubbling & Capturing**: Understanding event flow phases
* **Custom Events**: Creating and dispatching custom events
* **Touch Events**: Basic mobile interaction handling
* **Performance Optimization**: Debouncing and throttling
* **MVC Architecture Introduction**: Separating concerns in JavaScript applications
* **Model Layer**: Data management and business logic separation
* **View Layer**: DOM manipulation and presentation logic
* **Controller Layer**: Event handling and application flow control
* **Refactoring Strategy**: Converting procedural code to MVC pattern
* **Benefits of MVC**: Maintainability, testability, and scalability

**Essential Resources:**
- [Event Delegation Explained](https://javascript.info/event-delegation)
- [Custom Events Tutorial - YouTube](https://www.youtube.com/watch?v=92OOGugZIYo)
- [Debouncing vs Throttling](https://css-tricks.com/debouncing-throttling-explained-examples/)
- [MVC Pattern in JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/MVC)
- [JavaScript MVC Architecture Tutorial](https://www.taniarascia.com/javascript-mvc-todo-app/)
- [Separation of Concerns](https://en.wikipedia.org/wiki/Separation_of_concerns)

#### Interview Questions:
1. What is event delegation and when should you use it?
2. Explain the three phases of event propagation
3. How do you create and dispatch custom events?
4. What's the difference between debouncing and throttling?
5. What is the MVC pattern and why is it important in web development?
6. How do you separate data logic from presentation logic in JavaScript?
7. What are the benefits of refactoring procedural code to MVC architecture?
8. How does MVC prepare you for frameworks like React?

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
* **Parent-Child Relationships**: `parentElement`, `children`, `childNodes`
* **Sibling Navigation**: `nextElementSibling`, `previousElementSibling`
* **Tree Walking**: `firstElementChild`, `lastElementChild`
* **Node vs Element**: Understanding the difference and when to use each
* **Closest Method**: Finding ancestor elements with specific criteria

**Essential Resources:**
- [MDN DOM Traversal](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Locating_DOM_elements_using_selectors)
- [Element vs Node Properties](https://javascript.info/dom-navigation)

#### Interview Questions:
1. What's the difference between `children` and `childNodes`?
2. How do you find the closest ancestor element with a specific class?
3. When would you use DOM traversal vs `querySelector()`?
4. Explain the difference between Element and Node properties

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
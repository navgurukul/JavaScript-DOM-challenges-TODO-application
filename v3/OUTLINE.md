## [6.8 JavaScript object basics](#page-1)

Learning outcomes:

Understand that in JavaScript most things are objects, and you've probably used objectsevery time you've touched JavaScript.

- Basic syntax:

- Object literals.

- Properties and methods.

- Nesting objects and arrays in objects.

- Using constructors to create a new object.

- Object scope, and this .

- Accessing properties and methods — bracket and dot syntax.

- Object destructuring.

Resources:

- [JavaScript object basics](https://developer.mozilla.org/docs/Learn_web_development/Core/Scripting/Object_basics)

- [Object destructuring assignment](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Destructuring)

## [6.9 DOM scripting](#page-1)

Learning outcomes:

Understand what the DOM is — the browser's internal representation of the document'sHTML structure as a hierarchy of objects, which can be manipulated using JavaScript.

Understand the important parts of a web browser and how they are represented inJavaScript — Navigator , Window , and Document .

Understand how DOM nodes exist relative to each other in the DOM tree — root, parent,child, sibling, and descendant.

- Getting references to DOM nodes, for examplewith querySelector() and getElementById() .

- Creating new nodes, for example with innerHTML() and createElement() .

- Adding and removing nodes to the DOM with appendChild() and removeChild() .

- Adding attributes with setAttribute() .

- Manipulating styles with Element.style.* and Element.classList.* .

Resources:

- [Manipulating documents](https://developer.mozilla.org/docs/Learn_web_development/Core/Scripting/DOM_scripting)

- [DOM Scripting,](https://explainers.dev/dom-scripting/) explainers.dev

## [6.10 Events](#page-1)

30/07/2025, 11:586. JavaScript fundamentals | MDN Curriculum

https://developer.mozilla.org/en-US/curriculum/core/javascript-fundamentals/#6.8_javascript_object_basics1/6


---

Learning outcomes:

Understand what events are — a signal fired by the browser when something significanthappens, which the developer can run some code in response to.

Event handlers:

- addEventListener() and removeEventListener()

- Event handler properties.

- Inline event handler attributes, and why you shouldn't use them.

Event objects.

Preventing default behavior with preventDefault() .

Event delegation.

Resources:

[Introduction to events](https://developer.mozilla.org/docs/Learn_web_development/Core/Scripting/Events)

## [6.11 Async JavaScript basics](#page-2)

Learning outcomes:

Understand the concept of asynchronous JavaScript — what it is and how it differs fromsynchronous JavaScript.

Understand that callbacks and events have historically provided the means to doasynchronous programming in JavaScript.

Modern asynchronous programming with async functions and await :

- Basic usage.

- Understanding async function return values.

- Error handling with try ... catch .

Promises:

- Understand that async / await use promises under the hood; they provide a simplerabstraction.

- Chaining promises.

- Catching errors with catch() .

Resources:

[Asynchronous JavaScript](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Async_JS)

## [6.12 Network requests with fetch()](#page-2)

Learning outcomes:

Understand that[fetch()](https://developer.mozilla.org/en-US/docs/Web/API/Window/fetch) is used for asynchronous network requests, which is by far themost common asynchronous JavaScript use case on the web.

Common types of resources that are fetched from the network:

- Text content, JSON, media assets, etc.

30/07/2025, 11:586. JavaScript fundamentals | MDN Curriculum

https://developer.mozilla.org/en-US/curriculum/core/javascript-fundamentals/#6.8_javascript_object_basics2/6


---

Data [from RESTful APIs.](https://developer.mozilla.org/docs/Glossary/REST) Learn the basic concepts behind REST, including commonpatterns such [as CRUD.](https://developer.mozilla.org/en-US/docs/Glossary/CRUD)

- Understand what single-page apps (SPAs) are, and the issues surrounding them:

- Accessibility issues behind asynchronous updates, for example, content updates notbeing announced by screen readers by default.

- Usability issues behind asynchronous updates, like loss of history and breaking the backbutton.

- Understand HTTP basics. You should look at common HTTP methods suchas GET , DELETE , POST , and PUT , and how they are handled via fetch() .

Resources:

- [Fetching data from the server](https://developer.mozilla.org/docs/Learn_web_development/Core/Scripting/Network_requests)

## [6.13 Working with JSON](#page-3)

Learning outcomes:

- Understand what JSON is — a very commonly used data format based on JavaScript objectsyntax.

- Understand that JSON can also contain arrays.

- Retrieve JSON as a JavaScript object using mechanisms available in Web APIs(e.g. Response.json() in the Fetch API).

- Access values inside JSON data using bracket and dot syntax.

- Converting between objects and text using JSON.parse() and JSON.stringify() .

Resources:

- [Working with JSON](https://developer.mozilla.org/docs/Learn_web_development/Core/Scripting/JSON)

- [JSON Review,](https://v2.scrimba.com/the-frontend-developer-career-path-c0j/~0lt?via=mdn) ScrimbaCOURSE PARTNER

30/07/2025, 11:586. JavaScript fundamentals | MDN Curriculum

https://developer.mozilla.org/en-US/curriculum/core/javascript-fundamentals/#6.8_javascript_object_basics3/6


---

Clicking will load content from scrimba.com

## [6.14 Libraries and frameworks](#page-4)

Learning outcomes:

Understand what third-party code is — functionality written by someone else that you canuse in your own project, so you don't have to write everything yourself.

Why developers use third-party code:

Efficiency and productivity: A huge amount of complex functionality is already writtenfor you to use, created in a way that enforces efficient, modular code organization.

Compatibility: Reputable framework code is already optimized to work acrossbrowsers/devices, for performance, etc. Many frameworks also have systems to outputto specific platforms (e.g. Android or iOS) as build targets.

Support/ecosystem: Popular frameworks have vibrant communities and help resourcesto provide support, and rich systems of extensions/plugins to add functionality.

The difference between libraries and frameworks:

A library tends to be a single code component that offers a solution to a specificproblem, which you can integrate into your own app (for example, chart.js forcreating <canvas> -based charts, [or three.js for](https://threejs.org/) simplified 3D GPU-based graphicsrendering), whereas a framework tends to be a more expansive architecture made up ofmultiple components for building complete applications.

A library tends to be unopinionated about how you work with it in your codebase,whereas a framework tends to enforce a specific coding style and control flow.

Why should you use frameworks?

- They can provide a lot of functionality and save you a lot of time.

- A lot of companies use popular frameworks such as React or Angular to write theirapplications, therefore a lot of jobs list frameworks as requirements for applicants tohave.

Why is a framework not always the right choice? A framework:

# JSON REVIEW

30/07/2025, 11:586. JavaScript fundamentals | MDN Curriculum

https://developer.mozilla.org/en-US/curriculum/core/javascript-fundamentals/#6.8_javascript_object_basics4/6


---

Can easily be overkill for a small project — you might be better off writing a few lines ofvanilla JavaScript to solve the problem or using a tailored library.

Usually adds a lot of JavaScript to the initial download of your application, leading to aninitial performance hit and possible usability issues.

Usually comes with its own set of custom syntax and conventions, which can introducea significant additional learning curve to the project.

- May be incompatible with an existing codebase because of its architecture choice.

- Will need to be updated regularly, possibly leading to extra maintenance overhead foryour application.

- May introduce significant accessibility issues for people using assistive technologiesbecause of its architecture (for example, SPA-style client-side routing), which will needto be considered carefully.

How to choose? A good library or framework must:

Solve your problems while offering advantages that significantly outweigh any negativesthat it brings to the table.

- Have good support and a friendly community.

- Be actively maintained — don't choose a codebase that has not been updated for over ayear, or has no users.

Resources:

[Introduction to client-side frameworks](https://developer.mozilla.org/docs/Learn_web_development/Core/Frameworks_libraries/Introduction)

[Introduction to React,](https://v2.scrimba.com/the-frontend-developer-career-path-c0j/~0q2?via=mdn) ScrimbaCOURSE PARTNER

30/07/2025, 11:586. JavaScript fundamentals | MDN Curriculum

https://developer.mozilla.org/en-US/curriculum/core/javascript-fundamentals/#6.8_javascript_object_basics5/6


---

Clicking will load content from scrimba.com

## [6.15 Debugging JavaScript](#page-6)

Learning outcomes:

- Understand the different types of JavaScript errors, for example, syntax errors and logicerrors.

- Learn about the common types of JavaScript error messages and what they mean.

- Using browser developer tools to inspect the JavaScript running on your page and see whaterrors it is generating.

- Using console.log() and console.error() for simple debugging.

- Error handling:

- Using conditionals to avoid errors.

- try ... catch .

- throw .

- Advanced JavaScript debugging with breakpoints, watchers, etc.

Resources:

- [What went wrong? Troubleshooting JavaScript](https://developer.mozilla.org/docs/Learn_web_development/Core/Scripting/What_went_wrong)

- [Control flow and error handling > Exception handling statements](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling#exception_handling_statements)

- [The Firefox JavaScript debugger,](https://firefox-source-docs.mozilla.org/devtools-user/debugger/index.html) Firefox Source Docs

- [Chrome > Console overview,](https://developer.chrome.com/docs/devtools/console/) developer.chrome.com (2019)

- [Chrome > Debug JavaScript,](https://developer.chrome.com/docs/devtools/javascript/) developer.chrome.com (2017)

# LEARNREACT INTRO

30/07/2025, 11:586. JavaScript fundamentals | MDN Curriculum

https://developer.mozilla.org/en-US/curriculum/core/javascript-fundamentals/#6.8_javascript_object_basics6/6

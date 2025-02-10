# JavaScript Concepts and Problems

## Explanation of Key Concepts

### 1. Callbacks

A **callback function** is a function passed as an argument to another function, which gets executed later.

#### Example:

```js
function fetchData(callback) {
  setTimeout(() => {
    console.log("Data fetched");
    callback();
  }, 1000);
}

function processData() {
  console.log("Processing data...");
}

fetchData(processData);
```

### 2. Callback Hell

Callback hell occurs when multiple nested callbacks make code hard to read and maintain.

#### Example:

```js
setTimeout(() => {
  console.log("Task 1");
  setTimeout(() => {
    console.log("Task 2");
    setTimeout(() => {
      console.log("Task 3");
    }, 1000);
  }, 1000);
}, 1000);
```

### 3. Events and Event Handling

Events are user interactions or system-generated notifications.

#### Example:

```js
document.getElementById("btn").addEventListener("click", () => {
  console.log("Button clicked");
});
```

### 4. Mouse Events

Examples include `click`, `dblclick`, `mouseenter`, `mouseleave`.

#### Example:

```js
document.addEventListener("mousemove", (event) => {
  console.log(`Mouse moved: X=${event.clientX}, Y=${event.clientY}`);
});
```

### 5. Keyboard Events

Examples include `keydown`, `keyup`, `keypress`.

#### Example:

```js
document.addEventListener("keydown", (event) => {
  console.log(`Key pressed: ${event.key}`);
});
```

### 6. Form Events

Examples include `submit`, `change`, `input`.

#### Example:

```js
document.getElementById("form").addEventListener("submit", (event) => {
  event.preventDefault();
  console.log("Form submitted");
});
```

### 7. Window & Document Events

Examples include `load`, `resize`, `scroll`.

#### Example:

```js
window.addEventListener("resize", () => {
  console.log("Window resized");
});
```

### 8. Clipboard Events

Examples include `copy`, `paste`, `cut`.

#### Example:

```js
document.addEventListener("copy", () => {
  console.log("Content copied");
});
```

### 9. Drag & Drop Events

Examples include `dragstart`, `dragover`, `drop`.

#### Example:

```js
document.getElementById("drag-item").addEventListener("dragstart", () => {
  console.log("Dragging started");
});
```

### 10. Network Events

Examples include `online`, `offline`.

#### Example:

```js
window.addEventListener("offline", () => {
  console.log("You are offline");
});
```

### 11. Event Bubbling, Delegation, and Capturing

- **Event Bubbling:** Events propagate from child to parent.
- **Event Capturing:** Events propagate from parent to child.
- **Event Delegation:** Handling events at a higher level to manage multiple child elements efficiently.

#### Example:

```js
document.getElementById("parent").addEventListener("click", (event) => {
  console.log("Event Delegation: ", event.target);
});
```

### 12. Preventing Default Actions

The `preventDefault()` method prevents the default behavior of an event.

#### Example:

```js
document.getElementById("link").addEventListener("click", (event) => {
  event.preventDefault();
  console.log("Link click prevented");
});
```

### 13. Custom Events

Custom events allow you to create your own event types.

#### Example:

```js
const customEvent = new Event("myCustomEvent");
document.addEventListener("myCustomEvent", () => {
  console.log("Custom event triggered");
});
document.dispatchEvent(customEvent);
```

### 14. Event Throttling & Debouncing

- **Throttling:** Ensures an event is triggered at most once in a specified time interval.
- **Debouncing:** Ensures an event is triggered only after a certain period of inactivity.

#### Example (Throttling):

```js
function throttle(func, limit) {
  let inThrottle;
  return function () {
    if (!inThrottle) {
      func();
      inThrottle = true;
      setTimeout(() => (inThrottle = false), limit);
    }
  };
}

window.addEventListener(
  "scroll",
  throttle(() => {
    console.log("Throttled Scroll Event");
  }, 1000)
);
```

## JavaScript Problems

1. Implement a function that demonstrates callback usage.
2. Convert a callback hell scenario into a Promise-based approach.
3. Create an event listener for mouse movements that logs coordinates.
4. Implement a form submission handler that prevents default submission.
5. Write a function that detects online and offline status changes.
6. Demonstrate event delegation using a parent div and child buttons.
7. Implement event throttling for a window resize event.
8. Write a drag-and-drop event handler.
9. Create a custom event and dispatch it.
10. Implement event capturing for a nested element structure.

## Solutions

## 1. Callback Usage

```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback("Data received!");
  }, 1000);
}

fetchData((message) => {
  console.log(message); // Output: Data received!
});
```

## 2. Convert Callback Hell to Promises

```javascript
//CALLBACK HELL

function step1(callback) {
  setTimeout(() => {
    console.log("Step 1 completed");
    callback();
  }, 1000);
}

function step2(callback) {
  setTimeout(() => {
    console.log("Step 2 completed");
    callback();
  }, 1000);
}

function step3(callback) {
  setTimeout(() => {
    console.log("Step 3 completed");
    callback();
  }, 1000);
}

// Callback hell
step1(() => {
  step2(() => {
    step3(() => {
      console.log("All steps completed!");
    });
  });
});

//-------------------------------//

//PROMISE

function step1() {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log("Step 1 completed");
      resolve();
    }, 1000);
  });
}

function step2() {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log("Step 2 completed");
      resolve();
    }, 1000);
  });
}

function step3() {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log("Step 3 completed");
      resolve();
    }, 1000);
  });
}

// Using Promises
step1()
  .then(step2)
  .then(step3)
  .then(() => console.log("All steps completed!"));
```

## 3. Event Listener for Mouse Movements

```javascript
document.addEventListener("mousemove", (event) => {
  console.log(`Mouse X: ${event.clientX}, Mouse Y: ${event.clientY}`);
});
```

## 4. Form Submission Handler (Prevent Default)

```javascript
document.querySelector("form").addEventListener("submit", function (event) {
  event.preventDefault();
  console.log("Form submission prevented!");
});
```

## 5. Detect Online and Offline Status Changes

```javascript
window.addEventListener("online", () => console.log("You are online"));
window.addEventListener("offline", () => console.log("You are offline"));
```

## 6. Event Delegation with Parent Div and Child Buttons

```javascript
document
  .getElementById("parentDiv")
  .addEventListener("click", function (event) {
    if (event.target.tagName === "BUTTON") {
      console.log(`Button clicked: ${event.target.textContent}`);
    }
  });
```

```html
<div id="parentDiv">
  <button>Button 1</button>
  <button>Button 2</button>
</div>
```

## 7. Event Throttling for Window Resize

```javascript
function throttle(func, limit) {
  let inThrottle;
  return function () {
    const args = arguments;
    const context = this;
    if (!inThrottle) {
      func.apply(context, args);
      inThrottle = true;
      setTimeout(() => (inThrottle = false), limit);
    }
  };
}

window.addEventListener(
  "resize",
  throttle(() => {
    console.log("Window resized!");
  }, 500)
);
```

## 8. Drag-and-Drop Event Handler

```javascript
const draggable = document.getElementById("draggable");
draggable.addEventListener("dragstart", (event) => {
  event.dataTransfer.setData("text/plain", event.target.id);
});

const dropZone = document.getElementById("dropZone");
dropZone.addEventListener("dragover", (event) => {
  event.preventDefault();
});

dropZone.addEventListener("drop", (event) => {
  event.preventDefault();
  const data = event.dataTransfer.getData("text/plain");
  event.target.appendChild(document.getElementById(data));
});
```

```html
<div id="draggable" draggable="true">Drag Me</div>
<div
  id="dropZone"
  style="width: 200px; height: 200px; border: 2px dashed #000;"
>
  Drop Here
</div>
```

## 9. Custom Event and Dispatching

```javascript
const customEvent = new Event("customEvent");

document.addEventListener("customEvent", () => {
  console.log("Custom event triggered!");
});

document.dispatchEvent(customEvent);
```

## 10. Event Capturing for Nested Elements

```javascript
document.getElementById("outer").addEventListener(
  "click",
  () => {
    console.log("Outer div clicked");
  },
  true
);

document.getElementById("middle").addEventListener(
  "click",
  () => {
    console.log("Middle div clicked");
  },
  true
);

document.getElementById("inner").addEventListener(
  "click",
  () => {
    console.log("Inner div clicked");
  },
  true
);
```

```html
<div id="outer" style="padding: 30px; background-color: lightblue;">
  Outer
  <div id="middle" style="padding: 20px; background-color: lightcoral;">
    Middle
    <div id="inner" style="padding: 10px; background-color: lightgreen;">
      Inner
    </div>
  </div>
</div>
```
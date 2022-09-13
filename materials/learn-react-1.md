# Learn React 1

## Step 1. Getting started

Open up your terminal.

Make sure node and npm are working. Run the following commands:

```bash
node --version
```

It should display version 16.x (or 18.x).

```bash
npx --version
```

Any version means it is installed.

> Note: `npm` and `npx` are installed by Node.js

If these are not installed install the latest version of node.

  - https://github.com/CUNYTechPrep/guides#development-environment-setup
  
## Step 2. Create and Launch a React project

In your terminal, make a directory for your projects, and change directory to it. I like to keep my files in a directory named `ctp` under my home directory.

```bash
cd ~
mkdir ctp
cd ctp
```

> you only have to `mkdir ctp` if this directory doesn't already exist

Now we're going to create our first react app:

```bash
npx create-react-app learn-react-1
cd learn-react-1
npm start
```

If your browser opened up automatically and you see the spinning logo, then everything is working.

## Step 3. Look through the code

Open up the `learn-react-1` directory in your code editor.

Let's take a look at `/public/index.html`. Of importance here is `<div id="root"></div>`. This is the container where our React app will be loaded.

Now let's go to the `/src/index.js` and let's delete all of the code in this file. This is the entry point to our React app. No need to worry about the rest of the files in src for now. We will eventually delete them all, and create new files ourselves.

> When you delete all of the code and save the file, what happened in the browser?

## Step 4. Hello World

In `/src/index.js` add the following code:

```JSX
import React from "react";
import ReactDOM from "react-dom/client";

const htmlContainer = document.getElementById("root");
const root = ReactDOM.createRoot(htmlContainer);

root.render(<h1>Hello World!</h1>)
```

Let's break this code down.

- import statements
- `root = ReactDOM.createRoot(htmlDOMContainer)`
- `root.render(reactElement)`
- JSX `<h1>Hello World!</h1>`

> This is not HTML, it is JSX.

Try to change the JSX, add some other tags. Try the following examples and observe the results.

```JSX
<H1>Hello World!</H1>
```

```JSX
<div>
  <h1>Hello World!</h1>
  <h1>Hi Again</h1>
</div>
```

```JSX
<div>
  <h1>Hello World!
  <h1>Hi Again</h1>
</div>
```

```JSX
<h1>Hello World!</h1>
<h1>Hi Again</h1>
```

```JSX
<>
  <h1>Hello World!</h1>
  <h1>Hi Again</h1>
</>
```

- all standard HTML tags are available in lowercase version
- can nest multiple components
- all tags must be closed
- all JSX must have a single parent tag
- can use a fragment tag `<></>`

## Step 5. Functional Components

The point of a component based system is to create reusable componenets. Let's make the following changes to our code:

```JSX
import React from "react";
import ReactDOM from "react-dom/client";

function ClassList() {
  return (
    <div>
      <h1>Welcome to CTP</h1>
      <p>List of Students</p>
    </div>
  );
}

const htmlContainer = document.getElementById("root");
const root = ReactDOM.createRoot(htmlContainer);
root.render(<ClassList />);
```

What did we just do?

- components should begin with capital letters
- notice the `( )` in the return
- Try <ClassList></ClassList>, did it work?
- is <ClassList> a standard HTML tag?
	
We can and should create many small components, that we put together. Let's make the following changes:

```JSX
...

function StudentInfo() {
  return (
    <div>
      <div>
        Doe, Jane
      </div>
      <ul>
        <li>
          <strong>ID:</strong> 123
        </li>
        <li>
          <strong>School:</strong> Queens College
        </li>
        <li>
          <strong>Major:</strong> Computer Science
        </li>
      </ul>
    </div>
  );
}

function ClassList() {
  return (
    <div>
      <h1>Welcome to CTP</h1>
      <p>List of Students</p>
      <StudentInfo />
    </div>
  );
}

...
```

- Try adding multiple `StudentInfo` tags in the ClassList component. What happens?

## Step 6. Props and embedding JavaScript in JSX

A component like StudentInfo is a lot more useful if we can dynamically change its content. We will do that now:

```JSX
...

function StudentInfo(props) {
  return (
    <div>
      <div>
        {props.lastName}, {props.firstName}
      </div>
      <ul>
        <li>
          <strong>ID:</strong> {props.sId}
        </li>
        <li>
          <strong>School:</strong> {props.school}
        </li>
        <li>
          <strong>Major:</strong> {props.major}
        </li>
      </ul>
    </div>
  );
}

function ClassList() {
  return (
    <div>
      <h1>Welcome to CTP</h1>
      <p>List of Students</p>
      <StudentInfo firstName="Sally" lastName="James" />
      <StudentInfo />
      <StudentInfo />
    </div>
  );
}

...
```

- add different names to the last two `StudentInfo` tags
- `{  }` allows us to embed javascript within JSX
- `props` are always passed to components
- `props` are immutable, what does that mean?
- try changing `props.name = "Jose"`, what happens?
- props can be destructured in a component
  + `function StudentInfo({ firstName, lastName, sId, school, major }) {`

## Step 7. Rendering a list of students from a data array

When we render components in React, we usually get the data from an api or some other data source. We can use iterate over data lists with `.map()` to render each component. 

Add the following data to your index.js file.

```
const studentList = [
  {
    firstName: "Misty",
    lastName: "Knight",
    sId: "234",
    school: "Queens College",
    major: "Law",
  },
  {
    firstName: "Jessica",
    lastName: "Jones",
    sId: "434",
    school: "Brooklyn College",
    major: "CS",
  },
  {
    firstName: "Colleen",
    lastName: "Wing",
    sId: "233",
    school: "Queens College",
    major: "CS",
  },
  {
    firstName: "Dare",
    lastName: "Devil",
    sId: "876",
    school: "CCNY",
    major: "Law",
  },
  {
    firstName: "Luke",
    lastName: "Cage",
    sId: "323",
    school: "CCNY",
    major: "Math",
  },
];
```

Now modify your ClassList component to this:

```JSX
...
function ClassList() {
  return (
    <div>
      <h1>Welcome to CTP</h1>
      <p>List of Students</p>
      {studentList.map((student) => (
        <StudentInfo {...student} key={student.sId} />
      ))}
    </div>
  );
}
...
```

- we can destructure objects `{...student}` to pass them as props (keys and prop-names must match)
- when rendering lists of components we must provide unique keys

## Step 8. HTML Attributes like `<div class="red">` and adding CSS

JSX is not HTML, but it does allow you to set standard HTML attributes with slightly different names.

Instead of `class` we use `className`. React's designers did this on purpose to differentiate JSX from HTML.

There are many ways to handle CSS in React. For now we will keep it simple and use the file `/src/index.css`

in `/src/index.css` add the following to the bottom of the file:
```css
.red-text {
  color: red;
}
```

in `/src/index.js` add the following below your import statements:

```JSX
import './index.css'
```

and make the following change:

```JSX
...

function ClassList() {
  return (
    <div>
      <h1 className="red-text">Welcome to CTP</h1>
      <p>List of Students</p>
      {studentList.map((student) => (
        <StudentInfo {...student} key={student.sId} />
      ))}
    </div>
  );
}
...
```

## Step 9. Event Handling

Let's change our example app to explore the concept of events. What we ideally want to do now is keep track of how many times a user has clicked a button. It will take us two steps to get there. 

```JSX
...
function CountApp() {
  return (
    <div>
      <p>The button has been clicked 0 times</p>
      <button onClick={(e) => alert("the button was pressed!")}>
        Click this button
      </button>
    </div>
  );
}

// replace the root.render() call with this
root.render(<CountApp />);
```

In regular HTML, we can use the attribute `<div onclick="...">` to run some javascript event handling code. In react we will use the `onClick` prop instead.

- notice the camel casing of standard html attributes `className`, `onClick` in react
- onClick receives a function (callback) that will run in response to the event
- what happens if you change it to just `onClick={ alert('The button was pressed!) }`
- `onClick` works with other html tags, such as img, div, h1, etc.
- `e` stands for event, it contains information about the user event, such as which mouse button was used to click.


## Step 10. State and hooks

Now that we can handle the events like a button being clicked, we want to keep track of how many times the user has clicked the button.

Props are immutable (read-only) so we cannot use them to do that. So now we introduce another core react object that **is mutable, `state`**. 

```JSX
// Update your import to this
import React, { useState } from "react";

...

function CountApp() {
  const [numClicks, setNumClicks] = useState(0);

  const handleClick = (event) => {
    setNumClicks(numClicks + 1);
  };

  return (
    <div>
      <p>The button has been clicked {numClicks} times</p>
      <button onClick={handleClick}>Click this button</button>
    </div>
  );
}
```

In this example we initialize and access state by calling the `useState` hook and we update the state in the `handleClick` function.

- We can continue to use props if needed.
- the useState hook always returns an array of two things
  + `const [currentValue, setValueFunction] = useState(initialValue)`
- `handleClick` is our own function. We can call it anything we like.
- state can only be updated with the setValueFunction provided by the hook
- `numClicks = 42` will not work as expected, try this.

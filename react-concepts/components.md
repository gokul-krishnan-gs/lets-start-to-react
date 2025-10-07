# What is a React Component ?

- A React component is a JavaScript function that can combine logic with markup (JSX) to build reusable parts of a user interface.

- React encourages breaking down UIs into small, reusable, independent components (like buttons, images, forms, or entire pages).

### Example
```jsx
export function App() {
  return (
    <h1>Hello React!</h1>
  );
}
```

# Rules for Creating a Component

- Component names must start with a Capital Letter.
- React treats lowercase names as HTML tags and Capitalized names as Components.

### Example
```jsx
  export function Profile(){
  return (
    <h2>My Profile</h2>
  );
}
```

- A component should return JSX (JavaScript XML).
- JSX looks like HTML but is written inside JavaScript.
- Return must have only one parent element.
- Multiple sibling elements must be wrapped in a single parent (like <div> or <> fragment).


### Example
```jsx
return (
  <div>
    <h1>Hello</h1>
    <p>World</p>
  </div>
);
```

## Parent and Child Components

#### Parent component: The main container that holds child components.

#### Child components: Smaller components used inside the parent.

```jsx
//child
function Header() {
  return <h1>My Website</h1>;
}
//child
function Footer() {
  return <p>© 2025 All rights reserved</p>;
}
//parent
export function App() {
  return (
    <div>
      <Header />
      <p>This is the main content</p>
      <Footer />
    </div>
  );
}
```

### Key Learnings

- React lets us create reusable UI parts called components.

- In a React app, everything you see is a component.

- Components are just regular JavaScript functions that:

- -> Start with a Capital letter

- -> Return JSX

- Never define/nest a component inside another component definition (it causes bugs).

- Once a component is defined, you can use it anywhere, any number of times.

---

# Practice Questions
1. Create a component that displays a greeting message like “Welcome to My Website!”
2. Make a component that displays your name, your goal, and a motivational quote — all together.
3. Design two small child components (for example: “Header” and “Footer”) and use them inside a parent “App” component.
4. Create a small UI structure where the same child component is used multiple times

# Answers
1:
```jsx
function Greet(){
  return (
    <h1>Welcome to My Website!</h1>
  );
}
```
2:
```jsx
function Profile(){
  return (
    <>
      <h3>Name: Gokul Krishnan</h3>
      <h3>Goal : Full Stack Web Developer</h3>
      <h3>Quote: Hardwork Pays off</h3>
    </>
  );
}
```

3:
```jsx
function Header(){
  return (
    <>
      <h1>Welcome</h1>
    </>
  );
}

function Footer(){
  return(
    <>
      <h3>Thanks for Visiting</h3>
    </>
  );
}

function App() {
  return (
    <>
      <Header />
      <Footer />
    </>
  );
}
```
4:
```jsx
function Card(){
  return(
    <>
      <p>This is a paragraph.</p>
    </>
  );
}


function App() {
  return (
    <>
      <Card />
      <Card />
    </>
 );
}
```

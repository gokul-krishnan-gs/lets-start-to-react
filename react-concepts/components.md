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



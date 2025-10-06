#Export and Import 

---

### Root Component

- Every React project has a root component, usually named App.

- Other components are imported into this App component.

### Exporting Components

#### There are two main ways to export components:

### (a) Default Export

- A file can only have one default export.

- Good choice when the file has just one component.

```jsx
export default function Button() {
  return <button>Click Me</button>;
}
```
#### Importing
```jsx
import Button from './Button.jsx';

export function App() {
  return (
    <div>
      <h1>Hello React!</h1>
      <Button />
    </div>
  );
}
```

### (b) Named Export

- A file can have many named exports.

- Useful when exporting multiple components or values from the same file.

```jsx
export function Button() {
  return <button>Click Me</button>;
}

export function Header() {
  return <h1>Welcome!</h1>;
}
```

#### Importing
```jsx
import { Button, Header } from './Components.js';

export function App() {
  return (
    <div>
      <Header />
      <Button />
    </div>
  );
}
```

 ### Key Learning

- file can have only one default export.

- file can have multiple named exports.

- Default exports are often used when the file has only one main component.

- Named exports are often used when the file contains multiple components or values.

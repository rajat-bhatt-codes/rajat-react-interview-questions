# Higher Order Component (HOC)

### Defination

> A higher-order component is a function that takes a component and returns a new component.

### Uses

> A higher-order component (HOC) is an advanced technique in React for reusing component logic.

## code example

> In below example we are sharing he code for increment and counter with One and Two components.

### App.js

```javascript
import One from "./One";
import Two from "./Two";

export default function App() {
  return (
    <div className="App">
      <h1>Hello CodeSandbox</h1>
      <h2>Start editing to see some magic happen!</h2>
      <One />
      <Two />
    </div>
  );
}
```

### One.js

```javascript
import Counter from "./Counter";

const One = (props) => {
  const { count, incerment } = props;
  return (
    <>
      <h3>Count is: {count}</h3>
      <button onClick={incerment}>Incerment</button>
    </>
  );
};

export default Counter(One);
```

### Two.js

```javascript
import Counter from "./Counter";

const Two = (props) => {
  const { count, incerment } = props;
  return (
    <>
      <h3>Count is: {count}</h3>
      <button onClick={incerment}>Incerment</button>
    </>
  );
};

export default Counter(Two);
```

### Counter.js

```javascript
import { useState } from "react";

const Counter = (WrappedComponent) => {
  const Counter = () => {
    const [count, setCount] = useState(0);
    const incerment = () => {
      setCount(count + 1);
    };
    return (
      <>
        <WrappedComponent count={count} incerment={incerment} />
      </>
    );
  };
  return Counter;
};

export default Counter;
```

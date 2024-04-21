# ![Lifting State in React - Passing Functions as Props](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will understand how to pass functions as props in React.

## Passing functions as props

Functions are the mechanisms we use to lift state. Therefore, we must first learn how to pass a function down through props to lift state.

Thankfully, in React, passing functions as props is much like passing any other piece of data. For example, passing a string might look like the following:

```jsx
// Define the string variable in the parent component:
const myString = 'Hello World!';

// Pass down props:
return (
  <ChildComponent myString={myString} />
);
```

Within `ChildComponent`, that string value can be accessed through `props.myString`.

Similarly, passing a function might look like this:

```jsx
// define the function in the parent component:
const greetUser = () => {
  return 'Hello World!';
};

// pass down props:
return (
  <ChildComponent greetUser={greetUser} />
);
```

In `ChildComponent`, the function can be called upon to get its return value:

```jsx
const ChildComponent = (props) => {
  // call upon the function:
  const msg = props.greetUser();

  // display the value returned by the function:
  return (
    <h1>{msg}</h1>
  );
};
```

As you can see, functions can be passed down through props like any other data.

## Lifting state through props

Now that we've seen how functions can be passed down as props, let's use one to lift state.

To effectively lift state up, the function passed from the parent component to the child component must alter the parent component's state. Once a child component receives a state-modifying function through props, it can *call upon* that function and thereby influence the parent component's state.

Let's apply this concept with a small counter-application. In our app, we'll display a counter in `src/App.jsx`, and build a functionality that allows a child component to increment the value of the count.

Let's create a new component called `IncrementButton`:

```bash
touch src/components/IncrementButton.jsx
```

Our `IncrementButton` component will be a `<button>` that increments the display count.

Add the following to `src/components/IncrementButton.jsx`:

```jsx
// src/components/IncrementButton.jsx

const IncrementButton = (props) => {
  return (
    <button>Increment</button>
  );
};

export default IncrementButton;
```

With the child component defined, we can now import it into its parent.

At the top of `src/App.jsx`, add the following import:

```jsx
// src/App.jsx

import IncrementButton from './components/IncrementButton.jsx';
```

Our counter application will require a state that holds the current count value. We'll need to import the `useState` hook to do that.

Add the following to the top of `src/App.jsx`:

```jsx
// src/App.jsx

import { useState } from 'react';
```

Within the `App` function, define `count` state with an initial value of `0`:

```jsx
// src/App.jsx

  const [count, setCount] = useState(0);
```

Next, we can address the function that will update the state. The function should increment the current `count` value by `1`.

This function must be defined in the parent `App` component, where the `count` state variable resides. Once defined, we will pass the function down to the child component (`IncrementButton`), enabling it to invoke the function and increment the `count`.

Add the following function:

```jsx
// src/App.jsx

  const addOne = () => {
    setCount(count + 1);
  };
```

Next, we can render the `IncrementButton` component and pass down the `addOne` function through props.

Update the `return` in `src/App.jsx` with the following:

```jsx
// src/App.jsx

  return (
    <>
      <p>Count: {count}</p>
      <IncrementButton addOne={addOne} />
    </>
  );
```

Our final step is to update the `<button>` with an `onClick` event handler. The event handler should trigger the `addOne` function whenever a user clicks the button. Remember, the function can be accessed through the props object with `props.addOne`.

In `src/components/IncrementButton.jsx`, update the `<button>` as shown below:

```jsx
// src/components/IncrementButton.jsx

  return (
    <button onClick={props.addOne}>Increment</button>
  );
```

When we click the **Increment** button, it calls upon the `addOne` function as defined in `App`. The `addOne` function updates the `count` state and triggers a rerender with the increased display count. Through this, the child component can enact state changes on the parent.

Check your code in the browser to see the state of `App` update.

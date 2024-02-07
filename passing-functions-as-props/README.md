# ![Lifting State in React - Passing Functions as Props](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will understand how to pass functions as props in React.

## Passing functions as props

In order to lift state, we must first learn how to pass a function down through props. Thankfully, in React passing fuctions as props is much like passing any other piece of data.

For example, passing a string might look like the following:

```jsx
  // Define the string variable in parent component:
  const myString = 'Hello World!';

  // Pass down props:
	return (
    <ChildComponent myString={myString} />
	);
```

Within `ChildComponent`, that string value can be accessed through `props.myString`. 

Similarly, passing a function might look like this:

```jsx
  // Define the function in parent component:
  const greetUser = () => {
    return 'Hello World!';
  };

  // Pass down props:
	return (
    <ChildComponent greetUser={greetUser} />
	);
```

In `ChildComponent`, the function can be called upon to get its return value:

```jsx
const ChildComponent = (props) => {
  // Call upon the function:
	const msg = props.greetUser();

  // Display the value returned by the function:
	return (
		<>
      {msg}
		</>
	);
};
```

As you can see, functions can be passed down through props as you would any other data.

## Lifting state through props

Now that we've seen how functions can be passed down as props, let's add a bit of complexity. 

To effectively 'lift state up', the function being passed from the parent component to the child component must be one that alters the state of the parent component. Once a child component receives a state-modifying function through props, it can *call upon* that function and thereby influence the parent component's state.

Let's apply this concept with a small counter application. In our app, we'll display a counter in `src/App.jsx`, and build functionality that allows a child component to increment the value of the count.

Run the following command in your terminal:

```bash
touch src/components/IncrementButton.jsx
```

Our `IncrementButton` component will be just that, a `<button>` that increments the display count.

Add the following to `src/components/IncrementButton.jsx`:

```jsx
// src/components/IncrementButton.jsx
const IncrementButton = (props) => {
  return (
    <button>
      Increment
    </button>
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

Our counter application will require a piece of state that holds the current count value. To do that, we'll need to import the `useState` hook.

Add the following to the top of `src/App.jsx`:

```jsx
// src/App.jsx
import { useState } from 'react';
```

And within the `App` function, define `count` state with an initial value of `0`:

```jsx
// src/App.jsx
const App = () => {
	const [count, setCount] = useState(0);
```

Next we can address the function that will update state. The function should increment the current `count` value by `1`.

It's important that this function is defined in the parent `App` component, where the `count` state resides. Once defined, we will pass the function down to the child component (`IncrementButton`), enabling it to invoke the function and increment the `count`.

Add the following function:

```jsx
  // src/App.jsx
	const addOne = () => {
    setCount(count + 1);
  };
```

Next we can render the `IncrementButton` component, and pass down the `addOne` function through props.

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
    <button onClick={props.addOne}>
      Increment
    </button>
  );
```

Now when we click on the 'Increment' button, it calls upon the `addOne` function as defined in `App`. The `addOne` function  updates the `count` state and triggers a rerender with the increased display count. Through this, the child component is able to enact state changes on the parent.
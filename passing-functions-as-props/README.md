# ![Lifting State in React - Passing Functions as Props](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

A relatively simple stepping stone of a lesson to avoid slamming them all at once with the full pattern. This should not be complicated, just a "hey, you know you can send a function from a parent to a child too, right?" and put the event listener function in the child to then execute with `props.functionIWasGiven()`.

This could be an easy counter tracker or some such, but don't use an input just yet. This is baby-step 1, showing that functions can be passed then invoked by the child component and have an impact in the parent component.

The function should absolutely modify state and trigger a re-render in the parent.







this demonstrates a child manipulating the state of a parent
This could be an easy counter tracker or some such, but don't use an input just yet. This is baby-step 1, showing that functions can be passed then invoked by the child component and have an impact in the parent component.

before we can 'lift state', we'll learn how to pass functions as props

functions are just like any other data type that you've passed as a prop

pass a string, or a number

```jsx
const myString = 'Hell World!'
<MyComponent mySuperCoolString={myString} />
```

```jsx
props.mySuperCoolString
```
```jsx
const myObj = {name: 'Joe'}

<MyComponent myObject={myObj} />
```

```jsx
// rendering
props.myObject.name
```

in the same way, we can pass functions!

```jsx
// APP.JSX
const greetUser = () => {
  return 'Hello World!'
}

<Child greetUser={greetUser}/>
...
const ChildComponent = () => {
  const msg = props.greetUser()
  return(
    <>
      {msg}
    </>
  )
}
```

![tktk Hunter example of a function being passed]()

LET'S GET SOME PRACTICE with a practical example

setup - create the files
```bash
touch Incrementer.jsx
```

import etc

1. lets define a function in app
explain that the function will increment counter state
incrementCount

2. pass the function down as a prop

3. call upon the function in the Incrementer with an eventHandler (onClick)

example:

```jsx
// same pattern with a function
```

see the count display in app increment up with each click
notice, by modifying state, we trigger a re-render in the parent.
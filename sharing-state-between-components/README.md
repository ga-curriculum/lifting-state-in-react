# ![Lifting State in React - Sharing State Between Components](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

This is the big microlesson of this module. 

There should be a child component that is a form with its own internal state and controlled form pattern going on.

It will submit its state upwards into a stateful parent component.

That parent component probably has a list of objects that lives in state and that list gets modified by the child functions/components. The code-along-with-me section should get through ADDING a new item to the list and seeing that item get rendered into a sibling display component to the form.

Parent stateful container component - app
Child form new object component. - incrementer button
Child display objects list component. - display count

Discuss the timing of what should happen in that onSubmit event listener since the form values should probably get cleared and the state of the child gets updated in addition to calling the function that will update the state of the parent.






## Overview
let's get a sense of the mini app we will be building
The code-along-with-me section should get through ADDING a new item to the list and seeing that item get rendered into a sibling display component to the form.
see the component hiearchy diagram below
describe app
app will hold state, TodoList will render the todos held in state
NewTodo will be responsible for holding the form state and passing the newly created todo to its parent
so that it may be displayed by the its sibling

![tktk Hunter component hiearchy for this mini app]()
App
  todos[string], handleSubmit
NewTodo
TodoList

## mini setup

create the state variable

```jsx
// App.jsx
const [todos, setTodos] = useState([])
```

create the files

```bash
touch NewTodo.jsx TodoList.jsx
```

stub up the files
add the following starter code to each

- code that renders any todos in todo list
- setup html in new todo
```jsx
...
```

import the files
```jsx
// App.jsx
import
```

check your browser
it should look like this:
![tktk Hunter screenshot]()

## rendering todos

add some strings to the initial state of todos
pass it down to the TodoList which we stubbed up in the previous step
console log the todos
map through todos
and render some lis
before moving on, update todos state back to an empty array

## make functional form

NewTodoForm.jsx

- state -> formState / newTodo
- handleChange

state is just a simple string
single input in a form
(no complicated handleChange)

```jsx
const handleSubmit = () => {
  console.log('The form has been submitted)
  // clear state
}
<form onSubmit={handleSubmit}>
```

test it out, make sure you can update the form


## Lifting state

1. define the function/describe the function
accept newTodo as an argument
use your set state function to copy existing todos state,
add the new todo at the end of that array

```jsx
//app.jsx

const addTodo = (newTodo) => {
  setTodos([...todos, newTodo])
}
```

2. pass the function down

confirm that the function is available in the child
```jsx
console.log(props.addTodo)
```

3. build out handleSubmit
Discuss the timing of what should happen in that onSubmit event listener since the form values should probably get cleared and the state of the child gets updated in addition to calling the function that will update the state of the parent.

```jsx
const handleSubmit = () => {
  props.addTodo(newTodo)
  // clear form state / set new todo back to an empty string
  setNewTodo('')
}
```

4. dealing with the event handler

```jsx
<form onSubmit={handleSubmit}>
```

try it out in your browser, notice how the new todo entered into your NewTodoForm component, is displayed in the sibling TodoList




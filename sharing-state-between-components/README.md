# ![Lifting State in React - Sharing State Between Components](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to transfer state from one component to its parent and siblings

## Description

Now that we're able to pass a function from a parent down to a child, we're going to use that to explore how to pass information from the child back up to the parent.

## Code-along

In this code along, we're going to create a To-Do app.  The user will be able to add items (strings) to a list of items on the page.

The components in this app will be structured like so:

- App (parent)
	- (child) Form for creating new todos
	- (child) List of todos currently in App's state

It will look basically like this:

![tktk Hunter, please add awesome-o graphic]()

### Seting up `App.jsx`

Comment out your code in `App.jsx`.  We're not going to be using it for this lesson, but you should have it saved somewhere so that you can refer back to it later.

Next, set up `App.jsx` like so:

```js
const App = () => {

	const addTodo = (newTodo) => {
		console.log(newTodo)
	}


	return (
		<>
			<h1>To Do App</h1>
		</>
	);
}

export default App
```

Test this in your browser!

### Create `NewTodo` Form

In your terminal, create a new component file like so:

```bash
touch src/components/NewTodo.jsx
```

In `src/components/NewTodo.jsx`, add the following:

```js
const NewTodo = (props) => {
	const handleSubmit = (event) => {
		event.preventDefault()
		console.log("Creating a new To-Do...")
	}

	return (
		<form onSubmit={handleSubmit}>
			<input type="text" />
			<button>Create Todo</button>
		</form>
	)
}

export default NewTodo
```

Now let's import it at the top of `App.jsx`:

```js
import NewTodo from './components/NewTodo.jsx'
```

And now instantiate it within the `return` statement of `App.jsx`:

```js
return (
	<>
		<h1>To Do App</h1>
		<NewTodo />
	</>
);
```

Check your browser.  You should now see that the form has been added to the page.  Click the "Create Todo" button on the page and check the dev tools' console in your browser for the logged text "Creating a new To-Do...".

### Pass `addTodo` to the `NewTodo` Form

Now we want to pass `addTodo` down from `App.jsx` to `NewTodo.jsx` in much the same way that we passed `addOne` down from `App.jsx` to `IncrementButton.jsx`.

Make the following adjustment to the `return` statement of `App.jsx`:

```js
<NewTodo addTodo={addTodo} />
```

Now the `addTodo` function, defined in `App.jsx` will be available within `NewTodo.jsx` as `props.addTodo`.  Let's use that within our `handleSubmit` function:

```js
const handleSubmit = (event) => {
	event.preventDefault()
	props.addTodo('data created within NewTodo component')
}
```

Back in the browser, click the button and check the console to make sure that the text "data created within NewTodo component" has been logged.  The important thing here is that the text was logged by `addTodo` in `App.jsx`.  This function was called by `handleSubmit` within `NewTodo.jsx`, which passed `props.addTodo` the text as an argument.

![tktk Hunter, a diagram of the code please]
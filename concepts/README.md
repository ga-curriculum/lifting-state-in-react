# ![Lifting State in React - Concepts](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

## Understanding data flow in React

React enforces a **unidirectional data flow**, where data travels in one direction down the component tree, from parent to child. This structure simplifies the state management of your application and can make debugging more straightforward. However, this pattern presents a challenge when child components need to communicate changes back to their parent or to siblings.

To illustrate, consider the following scenarios involving state in React:

- **Passing state:** The parent `App.jsx` holds `todos` state. The `todos` state is passed down as a prop to the child `TodoList` where the data is rendered.
  ![Unidirectional data flow](./assets/unidirectional.png)

- **Shared state:** Our `todos` state is passed down to two siblings, `TodoList` and `NewTodo`.
  ![Shared state data flow](./assets/shared-state.png)

- **Localized state:** The `NewTodo` form has its own localized state, updating in response to user inputs without affecting the broader app.
  ![Local form state diagram](./assets/local-state.png)

Now, consider a scenario where a our `NewTodo` form needs to submit data that impacts a sibling component's display. Here, we encounter the limitations of unidirectional flow, as React doesn't naturally allow for upward or lateral state changes. This is where the concept of **lifting state** comes in to play.

## Lifting state

**Lifting state** means sending a function down as a prop, and using that function to update state. By defining a function in the parent component that updates its state and passing that function down to the child components as props, children can invoke this function, effectively updating the parent's state. The change then cascades down to other components that share that state.

In `App`, we can define a function called `addTodo`. This function will add a new `todo` object to state. The function can be passed down to `NewTodo`, so that it is called upon when a new todo is submitted. When the user submits the form, `NewTodo` doesn't directly alter `App`'s state. Instead, it calls `handleSubmit`, a function passed from `App` as a prop, to update `App`'s state with the new item. This updated state is then passed down to `TodoList` for display.

![App component hierarchy](./assets/lifting.png)

This setup allows `NewTodo` to relay updates to `App`, which in turn triggers a rerender and updates the data displayed in `TodoList`.

> 🏆 When designing an application and determining where to hold the state, consider where state needs to flow. What components are dependent on this state? What needs to receive and manipulate this data? These questions will guide you in determining the appropriate location for your application's state.

tktk Alternate definition: Lifting state is the practice of moving state up to a common ancestor of components that need access to that piece of state. 
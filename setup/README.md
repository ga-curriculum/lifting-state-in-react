# ![Lifting State In React Components - Setup](./assets/hero.png)

## Setup

```bash
npm create vite@latest
```

You'll be prompted to provide a project name.  Call the app `lifting-state-in-react-components`.

Next, you'll select a framework. Use the arrow keys to choose the `React` option, and hit `Enter`.

Again, use the arrow keys to choose the `JavaScript` variant and hit `Enter`.

Move into the project you just created and run `npm i` to install the dependencies:

```bash
cd lifting-state-in-react-components
npm i
```

Launch the app in VS Code:

```bash
code .
```

Open the `App.jsx` file in the `src` directory and replace the contents of it with the following:

```jsx
const App = () => {

  return (
    <h1>Hello world!</h1>
  );
}

export default App
```

Open `src/main.jsx` and remove the following line:

```js
import './index.css'
```

Run the dev server:

```bash
npm run dev
```
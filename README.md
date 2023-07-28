# React recaps
Recaps from react documentation https://react.dev/learn/state-a-components-memory#meet-your-first-hook

---

<br>

## Describing the UI

### Your First Component

You’ve just gotten your first taste of React! Let’s recap some key points.
- React lets you create components, **reusable UI elements for your app.**
    
- In a React app, every piece of UI is a component.
    
- React components are regular JavaScript functions except:
    
    1. Their names always begin with a capital letter.
    2. They return JSX markup.

*link: https://react.dev/learn/your-first-component*

<br>

### Importing and Exporting Components

On this page you learned:

- What a root component file is
- How to import and export a component
- When and how to use default and named imports and exports
- How to export multiple components from the same file

*link: https://react.dev/learn/importing-and-exporting-components*

<br>


### Writing Markup with JSX

Now you know why JSX exists and how to use it in components:

- React components group rendering logic together with markup because they are related.
- JSX is similar to HTML, with a few differences. You can use a [converter](https://transform.tools/html-to-jsx) if you need to.
- Error messages will often point you in the right direction to fixing your markup.

*link: https://react.dev/learn/writing-markup-with-jsx*

<br>


### JavaScript in JSX with Curly Braces

Now you know almost everything about JSX:

- JSX attributes inside quotes are passed as strings.
- Curly braces let you bring JavaScript logic and variables into your markup.
- They work inside the JSX tag content or immediately after `=` in attributes.
- `{{` and `}}` is not special syntax: it’s a JavaScript object tucked inside JSX curly braces.

*link: https://react.dev/learn/javascript-in-jsx-with-curly-braces*

<br>


### Passing Props to a Component

- To pass props, add them to the JSX, just like you would with HTML attributes.
- To read props, use the `function Avatar({ person, size })` destructuring syntax.
- You can specify a default value like `size = 100`, which is used for missing and `undefined` props.
- You can forward all props with `<Avatar {...props} />` JSX spread syntax, but don’t overuse it!
- Nested JSX like `<Card><Avatar /></Card>` will appear as `Card` component’s `children` prop.
- Props are read-only snapshots in time: every render receives a new version of props.
- You can’t change props. When you need interactivity, you’ll need to set state.

*link: https://react.dev/learn/passing-props-to-a-component*

<br>


### Conditional Rendering

- In React, you control branching logic with JavaScript.
- You can return a JSX expression conditionally with an `if` statement.
- You can conditionally save some JSX to a variable and then include it inside other JSX by using the curly braces.
- In JSX, `{cond ? <A /> : <B />}` means _“if `cond`, render `<A />`, otherwise `<B />`”_.
- In JSX, `{cond && <A />}` means _“if `cond`, render `<A />`, otherwise nothing”_.
- The shortcuts are common, but you don’t have to use them if you prefer plain `if`.

*link: https://react.dev/learn/conditional-rendering*

<br>


### Rendering Lists

On this page you learned:

- How to move data out of components and into data structures like arrays and objects.
- How to generate sets of similar components with JavaScript’s `map()`.
- How to create arrays of filtered items with JavaScript’s `filter()`.
- Why and how to set `key` on each component in a collection so React can keep track of each of them even if their position or data changes.

*link: https://react.dev/learn/rendering-lists*

<br>


### Keeping Components Pure

- A component must be pure, meaning:
    - **It minds its own business.** It should not change any objects or variables that existed before rendering.
    - **Same inputs, same output.** Given the same inputs, a component should always return the same JSX.
- Rendering can happen at any time, so components should not depend on each others’ rendering sequence.
- You should not mutate any of the inputs that your components use for rendering. That includes props, state, and context. To update the screen, [“set” state](https://react.dev/learn/state-a-components-memory) instead of mutating preexisting objects.
- Strive to express your component’s logic in the JSX you return. When you need to “change things”, you’ll usually want to do it in an event handler. As a last resort, you can `useEffect`.
- Writing pure functions takes a bit of practice, but it unlocks the power of React’s paradigm.

*link: https://react.dev/learn/keeping-components-pure*

---

<br>

## Adding Interactivity


### Responding to Events

- You can handle events by passing a function as a prop to an element like `<button>`.
- Event handlers must be passed, **not called!** `onClick={handleClick}`, not `onClick={handleClick()}`.
- You can define an event handler function separately or inline.
- Event handlers are defined inside a component, so they can access props.
- You can declare an event handler in a parent and pass it as a prop to a child.
- You can define your own event handler props with application-specific names.
- Events propagate upwards. Call `e.stopPropagation()` on the first argument to prevent that.
- Events may have unwanted default browser behavior. Call `e.preventDefault()` to prevent that.
- Explicitly calling an event handler prop from a child handler is a good alternative to propagation.

*link: https://react.dev/learn/responding-to-events*

<br>


### State: A Component's Memory

- Use a state variable when a component needs to “remember” some information between renders.
- State variables are declared by calling the `useState` Hook.
- Hooks are special functions that start with `use`. They let you “hook into” React features like state.
- Hooks might remind you of imports: they need to be called unconditionally. Calling Hooks, including `useState`, is only valid at the top level of a component or another Hook.
- The `useState` Hook returns a pair of values: the current state and the function to update it.
- You can have more than one state variable. Internally, React matches them up by their order.
- State is private to the component. If you render it in two places, each copy gets its own state.

*link: https://react.dev/learn/state-a-components-memory*

<br>

### Render and Commit

- Any screen update in a React app happens in three steps:
    1. Trigger
    2. Render
    3. Commit
- You can use Strict Mode to find mistakes in your components
- React does not touch the DOM if the rendering result is the same as last time

*link: https://react.dev/learn/render-and-commit*

<br>


### State as a Snapshot

- Setting state requests a new render.
- React stores state outside of your component, as if on a shelf.
- When you call `useState`, React gives you a snapshot of the state _for that render_.
- Variables and event handlers don’t “survive” re-renders. Every render has its own event handlers.
- Every render (and functions inside it) will always “see” the snapshot of the state that React gave to _that_ render.
- You can mentally substitute state in event handlers, similarly to how you think about the rendered JSX.
- Event handlers created in the past have the state values from the render in which they were created.

*link: https://react.dev/learn/state-as-a-snapshot*

<br>

### Queueing a Series of State Updates

- Setting state does not change the variable in the existing render, but it requests a new render.
- React processes state updates after event handlers have finished running. This is called batching.
- To update some state multiple times in one event, you can use `setNumber(n => n + 1)` updater function.

*link: https://react.dev/learn/queueing-a-series-of-state-updates*

<br>

### Updating Objects in State

- Treat all state in React as immutable.
- When you store objects in state, mutating them will not trigger renders and will change the state in previous render “snapshots”.
- Instead of mutating an object, create a _new_ version of it, and trigger a re-render by setting state to it.
- You can use the `{...obj, something: 'newValue'}` object spread syntax to create copies of objects.
- Spread syntax is shallow: it only copies one level deep.
- To update a nested object, you need to create copies all the way up from the place you’re updating.
- To reduce repetitive copying code, use Immer.

*link: https://react.dev/learn/updating-objects-in-state*

<br>


### Updating Arrays in State

- You can put arrays into state, but you can’t change them.
- Instead of mutating an array, create a _new_ version of it, and update the state to it.
- You can use the `[...arr, newItem]` array spread syntax to create arrays with new items.
- You can use `filter()` and `map()` to create new arrays with filtered or transformed items.
- You can use Immer to keep your code concise.

*link: https://react.dev/learn/updating-arrays-in-state*

---

<br>

## Managing State

### Reacting to Input with State

- Declarative programming means describing the UI for each visual state rather than micromanaging the UI (imperative).
- When developing a component:
    1. Identify all its visual states.
    2. Determine the human and computer triggers for state changes.
    3. Model the state with `useState`.
    4. Remove non-essential state to avoid bugs and paradoxes.
    5. Connect the event handlers to set state.

*link: https://react.dev/learn/reacting-to-input-with-state*

<br>

### Choosing the State Structure

- If two state variables always update together, consider merging them into one.
- Choose your state variables carefully to avoid creating “impossible” states.
- Structure your state in a way that reduces the chances that you’ll make a mistake updating it.
- Avoid redundant and duplicate state so that you don’t need to keep it in sync.
- Don’t put props _into_ state unless you specifically want to prevent updates.
- For UI patterns like selection, keep ID or index in state instead of the object itself.
- If updating deeply nested state is complicated, try flattening it.

*link: https://react.dev/learn/choosing-the-state-structure*

<br>


### Sharing State Between Components

- When you want to coordinate two components, move their state to their common parent.
- Then pass the information down through props from their common parent.
- Finally, pass the event handlers down so that the children can change the parent’s state.
- It’s useful to consider components as “controlled” (driven by props) or “uncontrolled” (driven by state).

*link: https://react.dev/learn/sharing-state-between-components*

<br>


### Preserving and Resetting State

- React keeps state for as long as the same component is rendered at the same position.
- State is not kept in JSX tags. It’s associated with the tree position in which you put that JSX.
- You can force a subtree to reset its state by giving it a different key.
- Don’t nest component definitions, or you’ll reset state by accident.

*link: https://react.dev/learn/preserving-and-resetting-state*

<br>


### Extracting State Logic into a Reducer

- To convert from `useState` to `useReducer`:
    1. Dispatch actions from event handlers.
    2. Write a reducer function that returns the next state for a given state and action.
    3. Replace `useState` with `useReducer`.
- Reducers require you to write a bit more code, but they help with debugging and testing.
- Reducers must be pure.
- Each action describes a single user interaction.
- Use Immer if you want to write reducers in a mutating style.

*link: https://react.dev/learn/extracting-state-logic-into-a-reducer*

<br>


### Passing Data Deeply with Context

- Context lets a component provide some information to the entire tree below it.
- To pass context:
    1. Create and export it with `export const MyContext = createContext(defaultValue)`.
    2. Pass it to the `useContext(MyContext)` Hook to read it in any child component, no matter how deep.
    3. Wrap children into `<MyContext.Provider value={...}>` to provide it from a parent.
- Context passes through any components in the middle.
- Context lets you write components that “adapt to their surroundings”.
- Before you use context, try passing props or passing JSX as `children`.

*link: https://react.dev/learn/passing-data-deeply-with-context*

<br>


### Scaling Up with Reducer and Context

## Recap[](https://react.dev/learn/scaling-up-with-reducer-and-context#recap "Link for Recap")

- You can combine reducer with context to let any component read and update state above it.
- To provide state and the dispatch function to components below:
    1. Create two contexts (for state and for dispatch functions).
    2. Provide both contexts from the component that uses the reducer.
    3. Use either context from components that need to read them.
- You can further declutter the components by moving all wiring into one file.
    - You can export a component like `TasksProvider` that provides context.
    - You can also export custom Hooks like `useTasks` and `useTasksDispatch` to read it.
- You can have many context-reducer pairs like this in your app.

*link: https://react.dev/learn/scaling-up-with-reducer-and-context*

<br>



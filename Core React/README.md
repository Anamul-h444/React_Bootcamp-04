- client side rendering
- react dom
- babel

# Composition in React

In React, composition is a way to combine multiple smaller components together to create a larger, more complex component. This allows you to break down a UI into smaller, more manageable pieces, making it easier to reason about and maintain.

Composition can be achieved in React in several ways, including:

    Props: You can pass down data or functions from a parent component to a child component through props. This allows you to customize the behavior or appearance of a child component based on the data passed down from its parent. For example, you could pass down a color or a font size to a child component as a prop.

    Children: You can also pass down components as children to another component. This allows you to build more complex components out of simpler components. For example, you could create a Card component that takes a Header component and a Body component as children to build a custom card layout.

    Higher-order components (HOCs): HOCs are functions that take a component and return a new component with enhanced functionality. This allows you to add or modify functionality of an existing component without having to modify its code directly. For example, you could create an HOC that adds authentication logic to a component.

    Render props: A render prop is a function that a component uses to render its children. This allows you to pass data or behavior from a component to its children in a more flexible way than using props. For example, you could create a DataProvider component that provides data to its children using a render prop.

Overall, composition is an important concept in React that helps you build complex UIs by combining smaller, reusable components together.

# imparative code vs declarative code in react

In React, imperative code and declarative code are two different programming paradigms that can be used to write code.

Imperative code is code that describes how to accomplish a task step-by-step, often using statements like if-else statements, for-loops, and other control flow statements. Imperative code is focused on the details of how to accomplish a task and can be difficult to understand and maintain, especially as the complexity of the code grows.

Declarative code, on the other hand, is code that describes what should be accomplished, rather than how to accomplish it. In declarative code, you describe the desired outcome and let the system figure out how to achieve it. Declarative code is often more concise and easier to read and understand than imperative code.

React is a declarative programming framework, which means that you define the desired state of your UI and React takes care of updating the DOM to match that state. You describe what your UI should look like based on the current state of your application, and React updates the DOM accordingly.

For example, consider the following imperative code that adds a new item to an array:

```js
const items = [1, 2, 3];
items.push(4);
console.log(items); // Output: [1, 2, 3, 4]
```

In this code, we are explicitly manipulating the items array by adding a new item to it using the push method.

In contrast, the following declarative code achieves the same outcome by creating a new array that includes the new item:

```js
const items = [1, 2, 3];
const newItems = [...items, 4];
console.log(newItems); // Output: [1, 2, 3, 4]
```

In this code, we are not directly modifying the items array. Instead, we are creating a new array that includes all the items from the original array, as well as the new item.

In React, we use declarative code to describe the UI based on the current state of the application. We define how our components should look based on the state of the application, and React takes care of updating the DOM to match that state. This makes it easier to reason about the code and maintain it as the complexity of the application grows.

# unidirectional data flow in React

In React, unidirectional data flow is a programming pattern that involves passing data down from parent components to child components through props, and allowing child components to communicate with their parent components through callback functions.

In this pattern, the data flows in a single direction, from parent components to child components. Parent components pass down data to their child components through props, which the child components can use to render their UI. If the child components need to communicate with the parent components, they can do so by calling a callback function that was passed down to them through props.

This pattern is sometimes referred to as the "top-down" or "one-way" data flow, because the data always flows from the top-level parent components down to the child components.

By using unidirectional data flow, React makes it easier to reason about the state of an application, because the data flow is predictable and easy to follow. When a component updates its state, it triggers a re-render of itself and all its child components, which ensures that the UI always reflects the current state of the application.

Here's an example of how unidirectional data flow might work in a simple React component (Parents to child):

```js
function Parent() {
  const [count, setCount] = useState(0);

  function handleIncrement() {
    setCount(count + 1);
  }

  return (
    <div>
      <h1>Count: {count}</h1>
      <Child onIncrement={handleIncrement} />
    </div>
  );
}

function Child({ onIncrement }) {
  return <button onClick={onIncrement}>Increment</button>;
}
```

In this example, the Parent component has a state variable count and a function handleIncrement that updates the count. It passes down the count state and the handleIncrement function to the Child component as props.

The Child component renders a button that calls the onIncrement callback function when it is clicked. When the button is clicked, the onIncrement function is called, which triggers the handleIncrement function in the parent component to update the count.

This is a simple example of how unidirectional data flow can be used in React to create a predictable data flow between parent and child components.

# Child to Parents

In React, child components can communicate with their parent components by passing data up through callback functions that the parent component has provided as props.

To allow a child component to communicate with its parent, the parent component passes down a callback function to the child component as a prop. The child component can then call this function and pass any necessary data as an argument, which allows the parent component to update its state or perform other actions based on the data provided by the child component.

Here's an example of how a child component can communicate with its parent in React:

```js
function Parent() {
  const [message, setMessage] = useState("");

  function handleMessage(message) {
    setMessage(message);
  }

  return (
    <div>
      <Child onMessage={handleMessage} />
      <p>Message from child: {message}</p>
    </div>
  );
}

function Child({ onMessage }) {
  function handleClick() {
    onMessage("Hello from child!");
  }

  return <button onClick={handleClick}>Send Message to Parent</button>;
}
```

In this example, the Parent component has a state variable message and a function handleMessage that updates the message. It passes down the handleMessage function to the Child component as a prop called onMessage.

The Child component renders a button that calls the onMessage callback function when it is clicked, passing the message "Hello from child!" as an argument. When the button is clicked, the onMessage function is called with the message argument, which triggers the handleMessage function in the parent component to update the message state variable.

When the message state variable is updated, the Parent component re-renders and the updated message is displayed on the page.

This is an example of how a child component can communicate with its parent component in React by passing data up through a callback function.

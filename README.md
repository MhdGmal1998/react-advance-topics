# React Advances Topics 
This documentation covers the most important topics in React.

1. **React.forwarsRef** : use when we want to pass the refs from the parent component to the child component
2. **React.portals** : use when we want to render component outside the root element 
3. **getDerivedStateFromError** : in this function we can catch the error boundary in the react render. But we must notice that react team make the error boudary is visible as a possible in dev mode and won't be visible in production mode

<br/>example :
```js
import "./styles.css";
import React from "react";

const Comp = ({ name }) => {
  if (name === "Ali") {
    throw new Error("naming errpr");
  }
  return <h1>{name}</h1>;
};
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      hasError: false
    };
  }
  static getDerivedStateFromError(error) {
    return {
      hasError: true
    };
  }

  render() {
    if (this.state.hasError) {
      return <h1>Unkown Error occured during render UI</h1>;
    }

    return this.props.children;
  }
}
export default function App() {
  return (
    <div className="App">
      <ErrorBoundary>
      <Comp name="Mohammed" />
        </ErrorBoundary>
        
        <ErrorBoundary>
        <Comp name="Sami" />
          </ErrorBoundary>
       <ErrorBoundary>
       <Comp name="Ali" />
      </ErrorBoundary>
    </div>
  );
}
```


### HOC

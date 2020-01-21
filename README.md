# React Hook - useGlobalState

[![NPM](https://badgen.net/npm/v/react-hook-use-global-state)](https://www.npmjs.com/package/react-hook-use-global-state)

Simple Global State Hook for React

## Install

```
npm i react-hook-use-global-state
```

## Usage

Add the provider to your layout or HoC and define your initial state and
your reducer.

**Demo:**

[![Edit Demo](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/react-hook-use-global-state-k159k)

**Layout.js**

```javascript
import React from "react"
import { StateProvider } from "react-hook-use-global-state"

const initialState = {
  counter: 0
}

const reducer = (state, action) => {
  switch (action.type) {
    case "counterInc":
      return {
        ...state,
        counter: state.counter + 1
      }
    case "counterDec":
      return {
        ...state,
        counter: state.counter - 1
      }
    default:
      return state
  }
}

export default function Layout({ children }) {
  return (
    <StateProvider initialState={initialState} reducer={reducer}>
      {children}
    </StateProvider>
  )
}
```

Use the global state in your component.

**SomeComponent.js**

```javascript
import React from "react"
import { useGlobalState } from "react-hook-use-global-state"

export default function SomeComponent() {
  const [{ counter }, dispatch] = useGlobalState()
  return (
    <div>
      Count: {counter}
      <br />
      <button onClick={() => dispatch({ type: "counterInc" })}>Inc</button>
      <button onClick={() => dispatch({ type: "counterDec" })}>Dec</button>
    </div>
  )
}
```

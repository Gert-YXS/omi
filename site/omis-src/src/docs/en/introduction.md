## What's Omis ？

Omis (pronounced /ˈomɪs/) is Functional Style, Easy Store and Hyperscript Component Framework in tiny size.

* Functional style but non-functional programming
* Structure-Style-Behavior Separation
* Hyperscript is visually more friendly
* Each component can have a store and be de-centralized
* Support global store to share data and update on demand
* Each component store has an update method that executes the method to customize local refresh components

[→ Omis Codepen Demos](https://codepen.io/collection/XjLaRo/)

## Add Omi in One Minute

```jsx
import { render, h } from 'omi'

const Counter = (props, store) => {
  return (
    <div>
      <button onClick={store.sub}>-</button>
      <span>{store.count}</span>
      <button onClick={store.add}>+</button>
    </div>
  )
}

Counter.store = _ => {
  return {
    count: 1,
    add() {
      this.count++
      this.update()
    },
    sub() {
      this.count--
      this.update()
    }
  }
}

Counter.css = `
span{
  color: red;
}
`

render(<Counter />, 'body')
```

You can also use hyperscript **with no build tooling**:

```js
const Counter = (props, store) => {
  return (
    h('div', {}, [
      h('button', { onClick: store.sub }, '-'),
      h('span', {}, store.count),
      h('button', { onClick: store.add }, '+')
    ])
  )
}
```

## Description of parameters

```jsx
const Comp = (props, store, _, $) => {

}

Comp.store = (_, $) => {

}
```

* `_` represents `component`
* `$` represents `globalStore`

You're already getting started! Congratulations!
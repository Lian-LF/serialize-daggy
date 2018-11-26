[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)](https://github.com/rametta/meatball/)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

# Currently only support taggedSum

> Stringify and parse your [Daggy](https://github.com/fantasyland/daggy)

<!-- ## Install
```sh
yarn add meatball
```

Meatball has a peer dependency on [fluture](https://github.com/fluture-js/Fluture)
```sh
yarn add fluture
```

## Usage examples
Listen to any redux action, perform side effect, return a new redux action to be fired
```js
// epics.js
import { searchRes, searchErr } from './reducer'
import { tryP, after } from 'fluture'

// Simple example
const simpleEpic = {
  type: 'SUBMIT_SEARCH', // listen for this action
  do: ({ payload }) => tryP(() => fetch(payload)) // fetch async data
    .map(res => res.json())
    .map(data => searchRes(data)) // redux action to save data
    .mapRej(e => searchErr(e)) // redux action for handling error
}

// Return multiple actions with an array
const multipleEpic = {
  type: 'SUBMIT_SEARCH', // listen for this action
  do: ({ payload }) => tryP(() => fetch(payload)) // fetch async data
    .map(res => res.json())
    .map(data => [searchRes(data), clearSidebar()]) // multiple actions
}

// Complex example
const complexEpic = {
  type: 'SUBMIT_SEARCH', // listen for this action
  latest: true, // Like rxjs switchMap, cancels previous action if not resolved
  do: ({ payload }) => after(200, payload) // delay fetching data for 200ms
    .chain(text => tryP(() => fetch(text)))
    .map(res => res.json())
    .map(data => [searchRes(data), clearSidebar()]) // multiple actions
    .mapRej(searchErr)
}

export default [ simpleEpic, multipleEpic, complexEpic ]

// index.js
import meatball from 'meatball'
import epics from './epics'

const store = createStore(
  reducers,
  applyMiddleware(meatball(epics))
)
```

[Real example](/example) -->
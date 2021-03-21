# redux-test-utils [![](https://github.com/RobTheFiveNine/redux-test-utils/actions/workflows/test.yml/badge.svg?branch=stable)](https://github.com/RobTheFiveNine/redux-test-utils/actions/workflows/test.yml) [![](https://coveralls.io/repos/github/RobTheFiveNine/redux-test-utils/badge.svg?branch=stable)](https://coveralls.io/github/RobTheFiveNine/redux-test-utils?branch=stable)

This is a fork of the [knegusen/redux-test-utils](https://github.com/knegusen/redux-test-utils) library, with added support for [thunks](https://github.com/reduxjs/redux-thunk).


## Install

In the terminal execute the following command:

```
$ npm install @robthefivenine/redux-test-utils --save-dev
```

or

```
$ yarn add -D @robthefivenine/redux-test-utils
```

## How to use

### createMockStore

```js
import { createMockStore } from '@robthefivenine/redux-test-utils';

describe('example', () => {
  it('works', () => {
    const state = 'state';
    const store = createMockStore(state);
    const action = {
      type: 'type',
      data: 'data'
    };
    store.dispatch(action);
    
    expect(store.getAction(action.type)).toEqual(action);
    expect(store.getActions()).toEqual([action]);
    expect(store.isActionDispatched(action)).toBe(true);
    expect(store.isActionTypeDispatched(action.type)).toBe(true);
    expect(store.getState()).toBe(state);
  });
});
```

### createMockDispatch

```js
import { createMockDispatch } from '@robthefivenine/redux-test-utils';

describe('example', () => {
  it('works', () => {
    const state = 'state';
    const dispatchMock = createMockDispatch();
    const action = {
      type: 'type',
      data: 'data',
    };
    dispatchMock.dispatch(action);

    expect(dispatchMock.getAction(action.type)).toEqual(action);
    expect(dispatchMock.getActions()).toEqual([action]);
    expect(dispatchMock.isActionDispatched(action)).toBe(true);
    expect(dispatchMock.isActionTypeDispatched(action.type)).toBe(true);
  });
});
```
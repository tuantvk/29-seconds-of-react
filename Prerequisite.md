### Prerequisites

To import a snippet into your project, you must import `React` and copy-paste the component's JavaScript code like this:

```js
import React from 'react';

function MyComponent(props) {
  /* ... */
}
```

If there is any CSS related to your component, copy-paste it to a new file with the same name and the appropriate extension, then import it like this:

```js
import './MyComponent.css';
```

To render your component, make sure there is a node with and id of `"root"` present in your element (preferrably a `<div>`) and that you have imported `ReactDOM`, like this:

```js
import ReactDOM from 'react-dom';
```
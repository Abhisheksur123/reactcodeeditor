# react-simple-code-editor

## Installation

```sh
npm install react-simple-code-editor
```

or

```sh
yarn add react-simple-code-editor
```

## Usage

You need to use the editor with a third party library which provides syntax highlighting. For example, it'll look like following with [`prismjs`](https://prismjs.com):

```js
import React from 'react';
import Editor from 'react-simple-code-editor';
import { highlight, languages } from 'prismjs/components/prism-core';
import 'prismjs/components/prism-clike';
import 'prismjs/components/prism-javascript';
import 'prismjs/themes/prism.css'; //Example style, you can use another

function App() {
  const [code, setCode] = React.useState(
    `function add(a, b) {\n  return a + b;\n}`
  );
  return (
    <Editor
      value={code}
      onValueChange={code => setCode(code)}
      highlight={code => highlight(code, languages.js)}
      padding={10}
      style={{
        fontFamily: '"Fira code", "Fira Mono", monospace',
        fontSize: 12,
      }}
    />
  );
}
```

Note that depending on your syntax highlighter, you might have to include additional CSS for syntax highlighting to work.

## Props

The editor accepts all the props accepted by `textarea`. In addition, you can pass the following props:

- `value` (`string`): Current value of the editor i.e. the code to display. This must be a [controlled prop](https://reactjs.org/docs/forms.html#controlled-components).
- `onValueChange` (`string => mixed`): Callback which is called when the value of the editor changes. You'll need to update the value prop when this is called.
- `highlight` (`string => string | React.Node`): Callback which will receive text to highlight. You'll need to return an HTML string or a React element with syntax highlighting using a library such as [`prismjs`](https://prismjs.com).
- `tabSize` (`number`): The number of characters to insert when pressing tab key. For example, for 4 space indentation, `tabSize` will be `4` and `insertSpaces` will be `true`. Default: `2`.
- `insertSpaces` (`boolean`): Whether to use spaces for indentation. Default: `true`. If you set it to `false`, you might also want to set `tabSize` to `1`.
- `ignoreTabKey` (`boolean`): Whether the editor should ignore tab key presses so that keyboard users can tab past the editor. Users can toggle this behaviour using `Ctrl+Shift+M` (Mac) / `Ctrl+M` manually when this is `false`. Default: `false`.
- `padding` (`number`): Optional padding for code. Default: `0`.
- `textareaId` (`string`): An ID for the underlying `textarea`, can be useful for setting a `label`.
- `textareaClassName` (`string`): A className for the underlying `textarea`, can be useful for more precise control of its styles.
- `preClassName` (`string`): A className for the underlying `pre`, can be useful for more precise control of its styles.


#Run
npm run example
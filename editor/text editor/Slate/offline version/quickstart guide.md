# Slate
## Intro
See [online version in Slate#Intro](https://github.com/40843245/tool/blob/main/editor/text%20editor/Slate/online%20version/quickstart%20guide.md#intro)

## Application
See [online version in Slate#Application](https://github.com/40843245/tool/blob/main/editor/text%20editor/Slate/online%20version/quickstart%20guide.md#application)

## Why to create slate?
See [online version in Slate#why-to-create-slate](https://github.com/40843245/tool/blob/main/editor/text%20editor/Slate/online%20version/quickstart%20guide.md#why-to-create-slate)

## Principle concept 
See [online version in Slate#principle-concept](https://github.com/40843245/tool/blob/main/editor/text%20editor/Slate/online%20version/quickstart%20guide.md#principle-concept)

## [Installation](https://docs.slatejs.org/walkthroughs/01-installing-slate)
Install these packages by running these commands.

```
yarn add slate slate-react
```

```
yarn add react react-dom
```

> [!NOTE]
> if you'd rather use a pre-bundled version of Slate, you can run these commands.
>
> ```
> yarn add slate
> ```
> 
> and then retrieve the bundled `dist/slate.js` file!

> [!TIP]
> Check out the [Using the Bundled Source](https://docs.slatejs.org/walkthroughs/xx-using-the-bundled-source) guide for more information.

### Demo
See the demo video at YT [How to install Slate?](https://youtu.be/u_uK3vbnUl8)

## [Startup](https://docs.slatejs.org/walkthroughs/01-installing-slate)
1. First, you need to import these packages.

```
// Import React dependencies.
import React, { useState } from 'react'
```

```
// Import the Slate editor factory.
import { createEditor } from 'slate'
```

```
// Import the Slate components and React plugin.
import { Slate, Editable, withReact } from 'slate-react'
```

2. Create an empty `<App>` Component.

```
// Define our app
const App = () => {
  return null
}
```

3. Create a new `Editor` object. We want the editor to be stable across renders, so we use the `useState` hook [without a setter](https://github.com/ianstormtaylor/slate/pull/3925#issuecomment-781179930).
   
```
const App = () => {
  // Create a Slate editor object that won't change across renders.
  const [editor] = useState(() => withReact(createEditor()))
  return null
}
```

> [!CAUTION]
> If you are using [`TypeScript`](https://docs.slatejs.org/concepts/12-typescript),
>
> you will also need to extend the `Editor` with `ReactEditor` and add annotations as per the documentation on `TypeScript`.
>
> The example below also includes the custom types required for the rest of this example.

```
// TypeScript users only add this code
import { BaseEditor, Descendant } from 'slate'
import { ReactEditor } from 'slate-react'

type CustomElement = { type: 'paragraph'; children: CustomText[] }
type CustomText = { text: string }

declare module 'slate' {
  interface CustomTypes {
    Editor: BaseEditor & ReactEditor
    Element: CustomElement
    Text: CustomText
  }
}
```

4.  Render a `<Slate>` context provider.

The provider component keeps track of your Slate editor, its plugins, its value, its selection, and any changes that occur. 

It must be rendered above any `<Editable>` components. But it can also provide the editor state to other components like toolbars, menus, etc. using the `useSlate` hook.

```
const initialValue = [
  {
    type: 'paragraph',
    children: [{ text: 'A line of text in a paragraph.' }],
  },
]

const App = () => {
  const [editor] = useState(() => withReact(createEditor()))
  // Render the Slate context.
  return <Slate editor={editor} initialValue={initialValue} />
}
```

5. Render the `<Editable>` component itself.

The component acts like contenteditable; 

anywhere you render it will render an editable richtext document for the nearest editor context.

```
const initialValue = [
  {
    type: 'paragraph',
    children: [{ text: 'A line of text in a paragraph.' }],
  },
]

const App = () => {
  const [editor] = useState(() => withReact(createEditor()))
  return (
    // Add the editable component inside the context.
    <Slate editor={editor} initialValue={initialValue}>
      <Editable />
    </Slate>
  )
}
```

6. That's done.

You can see a paragraph with the text -- `A line of text in a paragraph`. And when you type, you should see the text change!

## Demo
### CLI command

```
Microsoft Windows [Version 10.0.22631.3958]
(c) Microsoft Corporation. All rights reserved.

C:\Windows\System32>yarn add slate slate-react
➤ YN0000: · Yarn 4.4.0
➤ YN0000: ┌ Resolution step
➤ YN0000: └ Completed
➤ YN0000: ┌ Post-resolution validation
➤ YN0002: │ System32@workspace:. doesn't provide react (p12558), requested by slate-react.
➤ YN0002: │ System32@workspace:. doesn't provide react-dom (pab5ba), requested by slate-react.
➤ YN0086: │ Some peer dependencies are incorrectly met by your project; run yarn explain peer-requirements <hash> for details, where <hash> is the six-letter p-prefixed code.
➤ YN0000: └ Completed
➤ YN0000: ┌ Fetch step
➤ YN0000: └ Completed
➤ YN0000: ┌ Link step
➤ YN0000: │ ESM support for PnP uses the experimental loader API and is therefore experimental
➤ YN0000: └ Completed
➤ YN0000: · Done with warnings in 0s 98ms

C:\Windows\System32>yarn add react react-dom
➤ YN0000: · Yarn 4.4.0
➤ YN0000: ┌ Resolution step
➤ YN0085: │ + react-dom@npm:18.3.1, react@npm:18.3.1, js-tokens@npm:4.0.0, loose-envify@npm:1.4.0, and 1 more.
➤ YN0000: └ Completed in 2s 2ms
➤ YN0000: ┌ Fetch step
➤ YN0013: │ 5 packages were added to the project (+ 4.73 MiB).
➤ YN0000: └ Completed in 9s 899ms
➤ YN0000: ┌ Link step
➤ YN0000: │ ESM support for PnP uses the experimental loader API and is therefore experimental
➤ YN0000: └ Completed
➤ YN0000: · Done with warnings in 11s 964ms

C:\Windows\System32>yarn add slate
➤ YN0000: · Yarn 4.4.0
➤ YN0000: ┌ Resolution step
➤ YN0000: └ Completed
➤ YN0000: ┌ Fetch step
➤ YN0000: └ Completed
➤ YN0000: ┌ Link step
➤ YN0000: │ ESM support for PnP uses the experimental loader API and is therefore experimental
➤ YN0000: └ Completed
➤ YN0000: · Done with warnings in 0s 97ms

C:\Windows\System32>
```

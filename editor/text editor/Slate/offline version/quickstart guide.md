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


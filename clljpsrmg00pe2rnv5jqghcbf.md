---
title: "An incredibly simple toast notification system for React"
datePublished: Tue Aug 15 2023 00:31:00 GMT+0000 (Coordinated Universal Time)
cuid: clljpsrmg00pe2rnv5jqghcbf
slug: an-incredibly-simple-toast-notification-system-for-react-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692552061982/3c2efc5d-be04-4894-9cc8-1b6d93fe25b9.jpeg

---

---
title: An incredibly simple toast notification system for React
published: true
date: 2023-08-15 00:31:00 UTC
tags: Toasts,Notifications
canonical_url: https://reactjsexample.com/an-incredibly-simple-toast-notification-system-for-react/
---

# buttered-toast
 ![An incredibly simple toast notification system for React](https://cdn.hashnode.com/res/hashnode/image/upload/v1692552061982/3c2efc5d-be04-4894-9cc8-1b6d93fe25b9.jpeg)

An incredibly simple toast notification system for React.

- Only 894 byte (gzipped)
- No dependencies
- No styling, only logic
- No configuration
- No nonsense
- Render components
- No JSX during usage

This is a solution I’m using in several projects, so I decided to extract this into its own package. The existing libraries out there require you to add JSX elements to your React tree and render them based on conditions (controlled way). I never liked such solutions, I prefer a simple function call to show my toast.

## Installation

```
npm install buttered-toast
```

## Usage

### Add context provider

```
import { ToastContextProvider } from 'buttered-toast'

const App = ({ children }) => <ToastContextProvider>{children}</ToastContextProvider>
```

### `useToast` hook

```
import { useToast } from 'buttered-toast'

const Component = () => {
    const { show } = useToast()
    return <button onClick={() => show('Button clicked!')}>Click me!</button>
}
```

## API and Customization

### Exports

- `ToastContextProvider`
- `useToast`
- `defaultOptions`
- `ToastContext`

### `ToastContextProvider`

This is a React context provider that provides the state for `useToast` hooks. You must have this at least once in your React tree.

#### Props

- `options` – An object of options to override the default options. See `defaultOptions` for more information.

### `useToast`

This is a React hook that provides the `show` function to show a toast.

```
const { show } = useToast()
```

#### `show`

This function takes a two arguments argument. The content to show in the toast and an optional `options` object to override the options for this specific toast.

- `content` – The content to show in the toast. This can be anything that React can render as `children`.
- `options` _(optional)_ – An object of options to override the default options. See `defaultOptions` for more information.

```
show(<>Button clicked!</>)
show(<MyToastStyle>Button clicked!</MyToastStyle>)
```

### `defaultOptions`

An object of default options. These options can be overridden by passing an `options` object to the`ToastContextProvider`.

- `duration` – The duration in milliseconds to show the toast. Defaults to `3000`.
- `ref` – A ref to the toast element. Defaults to `null`. In case a `ref` is provided, React’s `createPortal` will be used to render the toast. If no `ref` is provided, the toast will be rendered in the `ToastContextProvider`.
- `Wrapper `– A wrapper component to wrap the toast in. Defaults to and “empty component”:`({ children }) => children`.
- `wrapperProps` – Props to pass to the wrapper component. Defaults to `{}`.

### `ToastContext`

This is the React context that is provided by the `ToastContextProvider`. You can use this context to create your own.

## Styling

This library does not provide any styling. You can style your toast by creating your own Toast component, and/or by styling your Wrapper element.

## Advanced example

```
import { ToastContextProvider, defaultOptions } from 'buttered-toast'

const App = ({ children }) => (
    <ToastContextProvider
        options={{
            ...defaultOptions,
            duration: 5000,
            Wrapper: ({ children, title }) => (
                <div className="my-wrapper">
                    <div className="my-title">{title}</div>
                    {children}
                </div>
            ),
            wrapperProps: { title: 'System notification' }
        }}
    >
        {children}
    </ToastContextProvider>
)

import { useToast } from 'buttered-toast'

const Component = () => {
    const { show } = useToast()
    return (
        <button
            onClick={() =>
                show(<ToastStyle>Button clicked!</ToastStyle>, {
                    duration: 10000,
                    wrapperProps: { title: 'What just happened?' }
                })
            }
        >
            Click me!
        </button>
    )
}
```

## GitHub

[View Github](https://github.com/wintercounter/buttered-toast?ref=reactjsexample.com)
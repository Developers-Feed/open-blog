---
title: "A Customizable toast component for React"
datePublished: Sun Oct 22 2023 00:39:00 GMT+0000 (Coordinated Universal Time)
cuid: clp1cxmrk00060alhaht71zk8
slug: a-customizable-toast-component-for-react

---

---
title: A Customizable toast component for React
published: true
date: 2023-10-22 00:39:00 UTC
tags: Toasts
canonical_url: https://reactjsexample.com/a-customizable-toast-component-for-react/
---

# Alert
 ![A Customizable toast component for React](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149192330/5872df55-ccf9-4f6c-a7f5-1d7af48af4d9.jpeg)

Customizable toast component for React.

## Installation

To start using the library, install it in your project:

```
npm install alert
```

Add the `<Toaster/>` component to your app, this component will take care of rendering all your toasts. After that, you can use the `toast()` function from anywhere in your app.

```
import { Toaster, toast } from 'alert';

// ...

const App = () => {
  return (
    <div>
      <Toaster />
      <button onClick={() => toast('This is a toast.')}>Create a toast</button>
    </div>
  );
}
```

## Documentation

You can find out more about the API and implementation soon.

## GitHub

[View Github](https://github.com/gxrsti/alert?ref=reactjsexample.com)
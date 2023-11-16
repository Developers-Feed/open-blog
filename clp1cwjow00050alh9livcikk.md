---
title: "Animated, lightweight expandable components for React"
datePublished: Sat Oct 28 2023 00:17:00 GMT+0000 (Coordinated Universal Time)
cuid: clp1cwjow00050alh9livcikk
slug: animated-lightweight-expandable-components-for-react

---

---
title: Animated, lightweight expandable components for React
published: true
date: 2023-10-28 00:17:00 UTC
tags: Toggle
canonical_url: https://reactjsexample.com/animated-lightweight-expandable-components-for-react/
---

# React Expandify 🚀

> ![Animated, lightweight expandable components for React](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149134476/80541c9b-fce1-40b4-ae8b-01a1c0a2a0b1.jpeg)
> 
> **Animated, lightweight expandable components for React. No extras, just effortless expand and collapse.**

## 📸 Demo

![Animated, lightweight expandable components for React](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149135841/6b534077-0285-4cc9-9e0c-006f887cd57b.gif)

* * *

## 🚀 Features

- 🎛 **Plug and Play** : Get started instantly, no complicated setup!
- 🌈 **Elemental Freedom** : Use any HTML element as your expandable container.
- 🎨 **Your Style, Your Rules** : Easy-to-add custom classes.
- ⏱ **Tick Tock Goes The Clock** : Control the expand and collapse speed to the millisecond!

* * *

## 📦 Installation

Add `React Expandify` to your project with npm:

```
npm install react-expandify
```

Or use yarn:

```
yarn add react-expandify
```

* * *

## 💡 Usage

Basic example:

```
import { Expandable } from 'react-expandify';
import 'react-expandify/dist/style.css';

const MyApp = () => (
  <Expandable expanded>
    <p>Your awesome content here!</p>
  </Expandable>
);
```

* * *

## 📚 Documentation

| Property | Type | Default | Description |
| --- | --- | --- | --- |
| `expanded` | `boolean` | `false` | Determines whether the content is expanded or not. |
| `children` | `ReactNode` | – | Children to be rendered inside the component. |
| `elementType` | `JSX.IntrinsicElements` | `'div'` | The HTML element type for the Expandable component. |
| `expandDuration` | `number` | `300` | Duration for the expand animation in milliseconds. |
| `collapseDuration` | `number` | `300` | Duration for the collapse animation in milliseconds. |
| `easing` | `string` | `ease-in-out` | Easing function for the expand and collapse animations. |
| `className` | `string` | – | Additional className for the Expandable component. |
| `onCollapse` | `() => void` | – | Callback when the content has collapsed. |
| `onExpand` | `() => void` | – | Callback when the content has expanded. |

* * *

## ✨ What You Can Create

| 
#### Tree view

![Animated, lightweight expandable components for React](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149137341/d1e3398d-c57a-4cdd-94e7-05eeadd6b838.gif)

 | 
#### Accordion component

![Animated, lightweight expandable components for React](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149139150/d3636b88-fb93-4328-81c8-bf503e46e3cc.gif)

 |
| 
#### Toggles

![Animated, lightweight expandable components for React](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149141027/23561b3e-bc65-4ac6-8e4f-86d754cdf02f.gif)

 | 
#### More examples coming soon…
 |

* * *

## 🙏 Contributing

Got ideas or bug reports? Open an issue or send a pull request!

## 📄 License

Licensed under the MIT License. See [LICENSE](https://github.com/armennersisyan/ReactExpandify/blob/main/LICENSE) for more details.

* * *

Crafted with 💖 by [Armen Nersisyan](https://github.com/armennersisyan)

## GitHub

[View Github](https://github.com/armennersisyan/ReactExpandify?ref=reactjsexample.com)
---
title: "A customizable tooltip component for React applications"
datePublished: Sun Aug 20 2023 00:49:00 GMT+0000 (Coordinated Universal Time)
cuid: clljppxf700mc1env3sadctcl
slug: a-customizable-tooltip-component-for-react-applications-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692551929577/f0bb3a3c-f6c3-4c5a-8bca-4bae201aa3df.jpeg

---

---
title: A customizable tooltip component for React applications
published: true
date: 2023-08-20 00:49:00 UTC
tags: Tooltip
canonical_url: https://reactjsexample.com/a-customizable-tooltip-component-for-react-applications/
---

# Get Tooltip React
 ![A customizable tooltip component for React applications](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551929577/f0bb3a3c-f6c3-4c5a-8bca-4bae201aa3df.jpeg)

A customizable tooltip component for React applications.

## Installation

You can install the `get-tooltip-react` package using npm:

```
npm install get-tooltip-react
```

## Usage

Import the Tooltip component and use it in your React application:

```
import React from "react";
import { Tooltip } from "get-tooltip-react";
import "get-tooltip-react/dist/style.css"; // Don't forget to import the CSS for styling

function App() {
  return (
    <div className="App">
      <h1>Tooltip React Component</h1>

      <div className="container">
        <Tooltip
          tooltiptext="This is a tooltip!"
          position="top"
          bg="#172554"
          textColor="#93c5fd"
          delay={500}
          arrow
        >
          <button className="tooltip-btn">Hover Me</button>
        </Tooltip>

        <Tooltip tooltipText="Another tooltip">
          <span>Hover over me too!</span>
        </Tooltip>
      </div>
    </div>
  );
}

export default App;
```

## Props

The Tooltip component accepts the following props:

- children: ReactNode (required) – The content that triggers the tooltip.
- tooltiptext: string (required) – The text to display in the tooltip.
- position: one of [“top”, “bottom”, “left”, “right”] – Position of the tooltip (default: “bottom”).
- bg: string – Background color of the tooltip (default: “black”).
- textColor: string – Text color of the tooltip (default: “white”).
- delay: number – Delay before showing the tooltip (in milliseconds, default: 0).
- arrow: boolean – Whether to show an arrow on the tooltip (default: false).

## GitHub

[View Github](https://github.com/khuranamanan/get-tooltip-react?ref=reactjsexample.com)
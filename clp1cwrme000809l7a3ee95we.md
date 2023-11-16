---
title: "A simple Visual Studio Code plugin that converts html text to React JSX"
datePublished: Thu Oct 26 2023 00:37:00 GMT+0000 (Coordinated Universal Time)
cuid: clp1cwrme000809l7a3ee95we
slug: a-simple-visual-studio-code-plugin-that-converts-html-text-to-react-jsx

---

---
title: A simple Visual Studio Code plugin that converts html text to React JSX
published: true
date: 2023-10-26 00:37:00 UTC
tags: Converter,HTML
canonical_url: https://reactjsexample.com/a-simple-visual-studio-code-plugin-that-converts-html-text-to-react-jsx/
---

# Convert HTML to React JSX
 ![A simple Visual Studio Code plugin that converts html text to React JSX](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149149430/d045c44d-8f19-41d4-9557-77c7889097f0.jpeg)

A simple Visual Studio Code plugin that converts html text to React JSX.

Just `ctrl + shift + P` -> `Convert HTML to React JSX` in the document you want to edit and run it.

![A simple Visual Studio Code plugin that converts html text to React JSX](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149151665/75707f8c-7550-4f4b-b1be-0f5ddff6c6ad.gif)

## How does it work

It simply replaces html tags with React ones.

Here’s the current list:

```
var mapObj = {
  "class=": "className=",
  "for=": "htmlFor=",
  "-rule": "Rule",
  "stroke-l": "strokeL",
  "stroke-w": "strokeW",
  "<!--": "{/\*",
  "-->": "\*/}",
  tabindex: "tabIndex",
};
```

[Open a pull request](https://github.com/PB2204/Html2React/compare) to add missing rules.

## GitHub

[View Github](https://github.com/PB2204/Html2React?ref=reactjsexample.com)
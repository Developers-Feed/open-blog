---
title: "Chrome Extension to preview markup in chat.openai.com"
datePublished: Sun Oct 22 2023 00:03:00 GMT+0000 (Coordinated Universal Time)
cuid: clp1cxuqp00070alhakpja3zk
slug: chrome-extension-to-preview-markup-in-chatopenaicom

---

---
title: Chrome Extension to preview markup in chat.openai.com
published: true
date: 2023-10-22 00:03:00 UTC
tags: ChatGPT
canonical_url: https://reactjsexample.com/chrome-extension-to-preview-markup-in-chat-openai-com/
---

# ChatGPT Markup Preview Extension (PoC)
 ![Chrome Extension to preview markup in chat.openai.com](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149199518/0a4006ae-d857-4791-84e4-56efab5c7e18.jpeg)

Chrome Extension to preview markup in chat.openai.com

This extension renders html preview by code block outputs.

- code block `html+preview` => preview html directly
- code block `tsx+preview` => renderToStaticMarkup as typescript react component
- Tailwind loaded
- Click 📎 to copy as an image (for image input)

Example.

![Chrome Extension to preview markup in chat.openai.com](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149201149/be259dcf-5305-4902-9c2b-0ca0d40ee9c0.png)

![Chrome Extension to preview markup in chat.openai.com](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149202761/cac4a7de-29e7-466d-8b3b-96ad398ce634.png)

## How it works

- Parse code blocks from chatgpt conversations
- Load Tailwind CDN [https://tailwindcss.com/docs/installation/play-cdn](https://tailwindcss.com/docs/installation/play-cdn)
- `html+preview`
  - Embed
- `tsx+preview`
  - Transpile code as typescript
  - Run in quickjs
  - renderToStaticMarkup with previewProps
  - Embed

## Install

- Download latest `chatgpt-markup-preview.zip` from [https://github.com/mizchi/chatgpt-markup-preview/releases](https://github.com/mizchi/chatgpt-markup-preview/releases)
- unzip
- Open chrome://extensions and load unpacked by developper mode [https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/)

## Prompt Example

### HTML + Tailwind

```
Generate a button element

- Describe it in html
- Use tailwind class for decoration
- Code block attributes should be ```html+preview
- Do not output anything but code

Output Example:

```html+preview
<div class="">Click Me</div>
```
```

### HTML + CSS Animation

```
Generate Loader

- Write it in html
- Code block attributes should be ```html+preview
- Do not output anything but code

Example output

```html+preview
<style>
.loader {}
</style>
<div class="loader"></div>
```
```

### React + Tailwind

```
Generate a button component.

Condition

- Use react+tsx to write the code. jsx: "react-jsx", so import is not required.
- Use tailwind for decoration. css import is not required.
- Code block attributes should be ```tsx+preview
- Do not output anything but code
- export previewProps that satisfy the type ``props

Example output

Example output: ```tsx+preview
type ButtonProps = { name: string }
export default function Button(props: Props) {
  return <></>
}
export const previewProps = {}
```
```

### Form

```
Generate form components.

FormProps = React.FormHTMLAttributes<HTMLFormElement> & {
  fields: Array<{label: string, value: string}>
}

Conditions

- Please write in react+tsx. jsx: "react-jsx" so import is not necessary.
- Use tailwind for decoration. css import is not required.
- Code block attributes should be ```tsx+preview
- Do not output anything but code
- export previewProps that satisfy the type ``props

Example output

```tsx+preview
type FormProps = { name: string }
export default function Form(props: Props) {
 return <></>
}
export const previewProps = {}
```
```

## Local Install

```
$ pnpm install
$ pnpm build

```

- Open chrome://extensions
- Load `dist` dir

## LICENSE

MIT

## GitHub

[View Github](https://github.com/mizchi/chatgpt-markup-preview?ref=reactjsexample.com)
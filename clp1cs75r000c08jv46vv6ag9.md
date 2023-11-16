---
title: "A toolkit for adopting LLM into your existing app"
datePublished: Tue Nov 14 2023 00:47:00 GMT+0000 (Coordinated Universal Time)
cuid: clp1cs75r000c08jv46vv6ag9
slug: a-toolkit-for-adopting-llm-into-your-existing-app

---

---
title: A toolkit for adopting LLM into your existing app
published: true
date: 2023-11-14 00:47:00 UTC
tags: Toolkit
canonical_url: https://reactjsexample.com/a-toolkit-for-adopting-llm-into-your-existing-app/
---

# Deep Grasp
 ![A toolkit for adopting LLM into your existing app](https://cdn.hashnode.com/res/hashnode/image/upload/v1700148937970/b0b6c162-37a8-4fcf-a8de-60a80d4a63ca.jpeg)

The goal of this project is to seamlessly integrate LLM into your current app. This means that users can retrieve and interact with a specific part of the user interface using natural language, without any intrusive measures.

NoteThis repo is still under heavy development, we welcome any idea and feedback.

## What is it

In the age of AI, we see increasing trend to adopt LLM into web applications, but for a large real world app, it is usually not easy to integrate AI feature into thousands lines of code.

Deep Grasp, aimed to non-intrusive integration to LLM, is able to do more by less code, as an example, we simply change a little code like:

```
+import {graspable} from '@deep-grasp/react';
+
-export default function Clock({timezone}: Props) {
+function Clock({timezone}: Props) {
     // ...
 }
+export default graspable(Clock, 'View clock in specified timezone');
```

As a result, we can get smooth and easy to use LLM features, a decorated component can be created and rendered automatically from user’s natural language query.

#

world-clock-demo.mp4

<video src="https://user-images.githubusercontent.com/639549/281655039-32fe1dfb-400c-40ea-b890-369500d91c0b.mp4" data-canonical-src="https://user-images.githubusercontent.com/639549/281655039-32fe1dfb-400c-40ea-b890-369500d91c0b.mp4" controls="controls" muted="muted" style="max-width:100%;min-height: 200px"></video>

## GitHub

[View Github](https://github.com/ecomfe/deep-grasp?ref=reactjsexample.com)
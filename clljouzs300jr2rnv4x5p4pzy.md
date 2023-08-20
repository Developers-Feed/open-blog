---
title: "A React library to create 9-slice image surfaces"
datePublished: Sat Aug 19 2023 00:39:00 GMT+0000 (Coordinated Universal Time)
cuid: clljouzs300jr2rnv4x5p4pzy
slug: a-react-library-to-create-9-slice-image-surfaces-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692550483786/45a0e8ae-1344-4e77-80aa-4ef67cb27bf1.jpeg

---

---
title: A React library to create 9-slice image surfaces
published: true
date: 2023-08-19 00:39:00 UTC
tags: Images
canonical_url: https://reactjsexample.com/a-react-library-to-create-9-slice-image-surfaces/
---

# REACT-9-SLICE
 ![A React library to create 9-slice image surfaces](https://cdn.hashnode.com/res/hashnode/image/upload/v1692550483786/45a0e8ae-1344-4e77-80aa-4ef67cb27bf1.jpeg)

![A React library to create 9-slice image surfaces](https://cdn.hashnode.com/res/hashnode/image/upload/v1692550486517/d6b79b0f-fef8-43ab-917b-90ce015ccb2a.png)

React library to create [9-slice image](http://rwillustrator.blogspot.com/2007/04/understanding-9-slice-scaling.html) surfaces. Check [the demo](https://dnbard.github.io/react-9-slice/)!

## Install

```
npm install react-9-slice --save
```

## Usage example

```
import React, { Component } from 'react';
import React9Slice from 'react-9-slice';

class MyComponent extends Component(){
    render(){
        return <React9Slice width={ 256 }
                            height={ 256 }
                            border={ 85 }
                            image="/images/myImage.png"
                            imageSize={{ x: 1024, y: 512 }}>
            HELLO WORLD!
        </React9Slice>
    }
}
```

## API

- `width`, `height` – size of the surface
- `border` – size of the non-scalable parts
- `image` – path to the image (you should provide it yourself)
- `imageSize` – initial size of the image
- `style` – styles for the `children`
- `children` – this element are going to be placed in the center of the surface

## GitHub

[View Github](https://github.com/kanazaya74Raccon/react-9-slice?ref=reactjsexample.com)
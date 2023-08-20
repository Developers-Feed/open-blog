---
title: "A React library allows you to take a snapshot of the webpage's screen or part of the screen"
datePublished: Thu Aug 10 2023 00:18:00 GMT+0000 (Coordinated Universal Time)
cuid: clljpw7v400n31env9ajp3gbl
slug: a-react-library-allows-you-to-take-a-snapshot-of-the-webpages-screen-or-part-of-the-screen-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692552222847/8ef95b60-2667-4a5d-812f-d03da1c4fb55.jpeg

---

---
title: A React library allows you to take a snapshot of the webpage's screen or part of the screen
published: true
date: 2023-08-10 00:18:00 UTC
tags: Screencapture
canonical_url: https://reactjsexample.com/a-react-library-allows-you-to-take-a-snapshot-of-the-webpages-screen-or-part-of-the-screen/
---

# react-screen-capture
 ![A React library allows you to take a snapshot of the webpage's screen or part of the screen](https://cdn.hashnode.com/res/hashnode/image/upload/v1692552222847/8ef95b60-2667-4a5d-812f-d03da1c4fb55.jpeg)

A tiny React library allows you to take a snapshot of the webpage’s screen or part of the screen.

### 💻 Live [Demo](https://codesandbox.io/s/react-screen-capture-i9f4d)

## 🎁 Features

- Easy to use
- Compatible with both JavaScript and TypeScript
- Take a snapshot of the webpage’s screen or part of the screen

## 🔧 Install

react-screen-capture is available on npm. It can be installed with the following command:

```
npm install react-screen-capture --save

```

react-screen-capture is available on yarn as well. It can be installed with the following command:

```
yarn add react-screen-capture

```

## 🔰 Callbacks

| Callback | Type | Description |
| --- | --- | --- |
| onStartCapture | `() => null` | To start capture webpage’s screen. |
| onEndCapture | `(base64Source: string) => null` | To end capture webpage’s screen and get base64 source. |

## 💡 Usage

```
import React from 'react';
import { ScreenCapture } from 'react-screen-capture';

class App extends React.Component {
  state = {
    screenCapture: '',
  };

  handleScreenCapture = screenCapture => {
    this.setState({screenCapture});
  };

  handleSave = () => {
    const screenCaptureSource = this.state.screenCapture;
    const downloadLink = document.createElement('a');
    const fileName = 'react-screen-capture.png';

    downloadLink.href = screenCaptureSource;
    downloadLink.download = fileName;
    downloadLink.click();
  };

  render() {
    const { screenCapture } = this.state;

    return (
      <ScreenCapture onEndCapture={this.handleScreenCapture}>
        {({ onStartCapture }) => (
          <div>
            <button onClick={onStartCapture}>Capture</button>
            <p>
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam
              distinctio exercitationem a tempore delectus ducimus necessitatibus
              dolor voluptatum aut est quaerat aspernatur, vero quod aperiam odio.
              Exercitationem distinctio in voluptates?
            </p>
            <p>
              Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ut molestiae
              deserunt voluptas, labore a expedita error eligendi sunt fugit, nesciunt
              ullam corrupti quas natus, officia rerum? Officia cum amet quidem.
            </p>
            <p>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quaerat, iusto
              repellat quae quos in rerum sunt obcaecati provident placeat hic saepe
              possimus eaque repellendus consequuntur quisquam nihil, sit ullam
              ratione.
            </p>
            <center>
              <img src={screenCapture} alt='react-screen-capture' />
              <p>
                {screenCapture && <button onClick={this.handleSave}>Download</button>}
              </p>
            </center>
          </div>
        )}
      </ScreenCapture>
    );
  }
};

export default App;
```

## GitHub

[View Github](https://github.com/marsinlegend/React-Screen-Capture?ref=reactjsexample.com)
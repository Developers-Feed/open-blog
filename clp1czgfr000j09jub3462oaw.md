---
title: "A React application made for hobbists/enthusiasts of playing piano"
datePublished: Thu Oct 12 2023 00:26:00 GMT+0000 (Coordinated Universal Time)
cuid: clp1czgfr000j09jub3462oaw
slug: a-react-application-made-for-hobbistsenthusiasts-of-playing-piano

---

---
title: A React application made for hobbists/enthusiasts of playing piano
published: true
date: 2023-10-12 00:26:00 UTC
tags: PianoKeyboard,Apps
canonical_url: https://reactjsexample.com/a-react-application-made-for-hobbists-enthusiasts-of-playing-piano/
---

# React Piano Player/Visualizer/Analyzer
 ![A React application made for hobbists/enthusiasts of playing piano](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149275991/7071542d-386a-489f-aecc-725e63ee2347.jpeg)

PianoBlocksApp is a web application made for hobbists/enthusiasts of playing piano. This app provides a very simple way to visualize a persons piano playing, by reading his midi File.

**Link to latest version [https://react-piano-player-63qjc9wca-tzmcion.vercel.app/](https://react-piano-player-63qjc9wca-tzmcion.vercel.app/)**

###### Github version is not always up-to-date.

### Last Update 5/05/2023

## Description

### What does this app do ?

I always wanted to create piano Tutorials like big youtubers, but I didn’t want to pay for professional software, so I created it myself :). This app makes it super easy to create piano tutorials, it delivers some basic effects, basic sound, and if you can’t record a midi file with softwares, you can record it there. Also with recording app gives you basic (super basic) sheet music. On top of that, app gives you plenty of ways to customize effects, colors, spped of playing. With this app you can learn and have fun.

### Technologies used

- **React**
- **Typescript**
- **HTML/CSS**
- **Sass (scss)**
- **Redux (a little)**
- **NPM library**

### How does the app work ?

![A React application made for hobbists/enthusiasts of playing piano](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149277590/2101c5c7-720e-48b1-9f43-27c4fb693a65.jpeg)

1. **User input** User Drags/chooses Midi file. He can configure options before that, or he can play demo file, then the Midi file is automatically imported 
2. **Website proceses it** Website saves the file to localstorage and it procesess it. It uses a “/helpers/getNoteEventsJSON.ts” file (function) to remove all unnecesarry events. 
3. **Website creates canvas animation** Canvas animation is created, frame rate is 60fps or 144 fps (depends on the screen type). 

## Installation

Just like every other github repo

```
git init
git pull https://github.com/tzmcion/ReactPianoPlayer
npm i 

```

Or git clone

```
git clone https://github.com/tzmcion/ReactPianoPlayer

```

## Note !

- In Official version you can find Donation page, but I deleted it here
- Some dependencies in `package.lock` are not used
- Please report every issue and bug
- If you’d like to work on this app, I will explain how every file works to you with pleasure, just write 🙂

## Resources

- **soundfont-player**
- **midi-parser-js**
- **react-youtube**
- **rgb-hex**
- **sass**

## License

**MIT** license

## GitHub

[View Github](https://github.com/luckydevn16/react-piano-player?ref=reactjsexample.com)
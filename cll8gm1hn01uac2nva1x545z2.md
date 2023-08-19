---
title: "Responsive image carousel with automatic and manual navigation, built using React"
datePublished: Fri Aug 11 2023 00:32:00 GMT+0000 (Coordinated Universal Time)
cuid: cll8gm1hn01uac2nva1x545z2
slug: responsive-image-carousel-with-automatic-and-manual-navigation-built-using-react
canonical: https://dev.to/mohammadtaseenkhan/responsive-image-carousel-with-automatic-and-manual-navigation-built-using-react-2mca
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691871504475/cc192038-d7cf-4abd-b1ac-814d5e0fed1c.png
tags: carousel, navigator

---

🎠 Image Carousel
=================

[![Responsive image carousel with automatic and manual navigation, built using React](https://cdn.hashnode.com/res/hashnode/image/upload/v1691871498906/21cd2acf-34ce-4657-873a-543174acef6c.jpeg)](https://res.cloudinary.com/practicaldev/image/fetch/s--w_hzMt----/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://reactjsexample.com/content/images/2023/08/code_2023-09-22-27-20.jpg)

This project demonstrates a responsive image carousel that displays three images in a slideshow format. The carousel transitions automatically every three seconds and allows manual navigation between images.

📦 Installation
---------------

1.  Clone the repository to your local machine using:
    
2.  Navigate to the project directory:
    
3.  Install the required dependencies:
    
4.  Start the development server:
    

🚀 Features
-----------

*   Displays three images in a slideshow format.
*   Transitions automatically between images every three seconds.
*   Allows manual navigation to the next or previous image.
*   Implements an infinite loop so that after reaching the last image, the carousel starts again with the first image.
*   Provides a reusable carousel component that supports independent instances.
*   Fetches images from a provided API ([https://jsonplaceholder.typicode.com/albums/1/photos](https://jsonplaceholder.typicode.com/albums/1/photos)).

🪄 Technologies
---------------

*   `CSS`
*   `React`
*   `Vite`

🐊 Usage
--------

1.  Open the web application in your browser after starting the development server.
2.  You will see two carousels side by side, each displaying three random images.
3.  The carousels transition automatically every three seconds.
4.  Use the “Previous” and “Next” buttons to navigate manually between images.
5.  Indicator dots below the carousel indicate the current image index. These dots are equipped with ARIA attributes for enhanced accessibility.

📷 Screenshot
-------------

[![Responsive image carousel with automatic and manual navigation, built using React](https://cdn.hashnode.com/res/hashnode/image/upload/v1691871500282/f05fd426-5dd4-4a4f-83fd-4d0bf070be2d.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--C9dQdLq1--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://github.com/mirayatech/image-carousel-test/raw/main/public/demo.png)

🤓 Future Improvements
----------------------

If I had more time, I could think about making the following things better:

*   Adding swipe gestures for devices you can touch.
*   Making the transitions between pictures smoother for a nicer experience.
*   Putting in options to change how the picture slideshow works, like how fast pictures change and if they change by themselves.
*   Adding e2e tests to double-check that the image carousel works perfectly in all situations and is super reliable. These tests will make sure the carousel does what it’s supposed to do without any problems.

GitHub
------

[View Github](https://github.com/mirayatech/image-carousel-test?ref=reactjsexample.com)
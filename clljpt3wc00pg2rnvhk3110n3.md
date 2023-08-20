---
title: "React share track or split bills platform"
datePublished: Tue Aug 15 2023 00:22:00 GMT+0000 (Coordinated Universal Time)
cuid: clljpt3wc00pg2rnvhk3110n3
slug: react-share-track-or-split-bills-platform-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692552073907/ac448bb6-bb53-4ada-81d8-5d045c0c769f.jpeg

---

---
title: React share track or split bills platform
published: true
date: 2023-08-15 00:22:00 UTC
tags: Split
canonical_url: https://reactjsexample.com/react-share-track-or-split-bills-platform/
---

 ![React share track or split bills platform](https://cdn.hashnode.com/res/hashnode/image/upload/v1692552073907/ac448bb6-bb53-4ada-81d8-5d045c0c769f.jpeg)

      

# TruPaid

[![React share track or split bills platform](https://cdn.hashnode.com/res/hashnode/image/upload/v1692552076105/2d738125-7273-4a47-8c89-2576920ac677.png)](https://github.com/kkumarcodes/Trupaid/blob/main/screenshots/ss1.png)

[![React share track or split bills platform](https://cdn.hashnode.com/res/hashnode/image/upload/v1692552077870/fbad6dbf-2675-433e-b4b3-ff7909c7f322.png)](https://github.com/kkumarcodes/Trupaid/blob/main/screenshots/ss2.png)

## Introduction

TruPaid is a automation for sharing. Roommates, tenants, landlords, and couples can share track or split bills together.

## Available Scripts

In the project directory, you can run:

### `yarn lint`

Runs typescript project files through a linter.

### `yarn format`

Attempt to lint and fix typescript project files using prettier.

### `yarn start`

Runs the app in the development mode. Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits. You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode. See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder. It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes. Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

## Folder Structure

```
src/
┣ api/ # Centralizes API calling based on data type
┃ ┣ api.ts
┃ ┣ index.ts
┃ ┗ user.ts
┣ assets/ # Handles images and theming support
┃ ┣ images/
┃ ┗ theme/
┣ components/ # Collection of UI components like button, custom input field, modal, etc that will be shared and used across files in the project.
┣ features/ # Each folder exports and handles it's own routes. Can be nested and have it's own components folder to be used by child routes.
┃ ┗ Onboarding/
┃ ┣ AccountCreation/
┃ ┃ ┃ ┣ Astra/
┃ ┃ ┃ ┣ Plaid/
┃ ┃ ┃ ┣ Register/
┃ ┃ ┃ ┗ index.tsx
┃ ┣ components/
┃ ┗ index.tsx
┃ ┣ components/
┃ ┗ index.tsx
┣ hooks/ # Reusable hooks. Mainly unused, but when you need it you will know.
┃ ┗ store.ts
┣ store/ # Each slice handles it's own actions, reducers, and selectors. Each slice is specific to a single resource.
┃ ┣ index.ts
┃ ┗ usersSlice.ts
┣ types/ # Typescript types and interfaces. Props types are the only exemption. They get declared above the components themselves.
┃ ┣ entities/
┃ ┣ request/
┃ ┗ response/
┣ utils/ # Files in the utils folder should only contain some functions like date formatting, string conversion, etc.
┗ index.tsx

```

## Technolgies and resources

- Typescript support
- State management[https://github.com/reduxjs/redux-toolkit](https://github.com/reduxjs/redux-toolkit)
- Routing[https://reactrouter.com/web/guides/quick-start](https://reactrouter.com/web/guides/quick-start)
- Styling Framework[https://github.com/mui-org/material-ui](https://github.com/mui-org/material-ui)
- Debugging Tools support:[https://github.com/zalmoxisus/redux-devtools-extension](https://github.com/zalmoxisus/redux-devtools-extension)
- Support for making HTTP requests[https://github.com/axios/axios](https://github.com/axios/axios)
- Visual tools for seeing and interacting with our custom component libraries.[https://github.com/storybookjs/storybook](https://github.com/storybookjs/storybook)

## GitHub

[View Github](https://github.com/kkumarcodes/Trupaid?ref=reactjsexample.com)
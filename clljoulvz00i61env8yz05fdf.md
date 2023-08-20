---
title: "Responsive masonry layout for React"
datePublished: Sun Aug 20 2023 00:56:00 GMT+0000 (Coordinated Universal Time)
cuid: clljoulvz00i61env8yz05fdf
slug: responsive-masonry-layout-for-react
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692550468358/2ee9ad9b-3fc8-46dc-99d8-76674e27bb91.jpeg

---

---
title: Responsive masonry layout for React
published: true
date: 2023-08-20 00:56:00 UTC
tags: Layout,Masonry
canonical_url: https://reactjsexample.com/responsive-masonry-layout-for-react/
---

# React Layout Masonry

> ![Responsive masonry layout for React](https://cdn.hashnode.com/res/hashnode/image/upload/v1692550468358/2ee9ad9b-3fc8-46dc-99d8-76674e27bb91.jpeg)
> 
> React Layout Masonry is a flexible and customizable React component for creating dynamic and fixed/responsive masonry layouts.

[View Demo](https://sibiraj-s.github.io/react-layout-masonry/)[View Github](https://github.com/sibiraj-s/react-layout-masonry?ref=reactjsexample.com)

## Installation

You can install React Layout Masonry using npm, pnpm or yarn:

```
npm install react-layout-masonry
```

or

```
pnpm install react-layout-masonry
```

or

```
yarn add react-layout-masonry
```

## Usage

### Fixed Columns Layout

Here’s an example of how to use React Layout Masonry with a fixed number of columns in your React application:

```
import Masonry from 'react-layout-masonry';

const FixedColumnsMasonry = () => {
  return (
    <Masonry columns={3} gap={16}>
      {items.map((item) => {
        return <Item {...item}>
      })}
    </Masonry>
  );
};

export default FixedColumnsMasonry;
```

### Responsive Columns Layout

Here’s an example of how to use React Layout Masonry with responsive columns in your React application:

```
import Masonry from 'react-layout-masonry';

const ResponsiveColumnsMasonry = () => {
  return (
    <Masonry columns={{ 640: 1, 768: 2, 1024: 3, 1280: 5 }} gap={16}>
        {items.map((item) => {
        return <Item {...item}>
      })}
    </Masonry>
  );
};

export default ResponsiveColumnsMasonry;
```

### Column Props

The `columnProps` prop allows you to apply additional props to the container of each column. Here’s an example:

```
<Masonry
  columns={3}
  gap={16}
  columnProps={{
    className: 'custom-column',
    style: { backgroundColor: 'lightgray' },
  }}
>
  {/\* ... \*/}
</Masonry>
```

## Props

- `columns` (number or object, required): The number of columns in the masonry layout, or an object with breakpoints and corresponding column counts.
- `gap` (number, optional): The spacing between columns and rows in pixels. Defaults to 0.
- `columnProps` (object, optional): Additional props to be applied to each column, such as className for styling.

## Examples

For examples, usage and customization options, please refer to the [stories](https://github.com/sibiraj-s/react-layout-masonry/blob/master/stories) directory in this repository.
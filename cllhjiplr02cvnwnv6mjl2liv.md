---
title: "React components for resizable panel groups/layouts"
datePublished: Wed Aug 09 2023 00:49:00 GMT+0000 (Coordinated Universal Time)
cuid: cllhjiplr02cvnwnv6mjl2liv
slug: react-components-for-resizable-panel-groupslayouts
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692420581242/737c938e-45da-48e3-9d21-92be310ad964.jpeg

---

---
title: React components for resizable panel groups/layouts
published: true
date: 2023-08-09 00:49:00 UTC
tags: Layout
canonical_url: https://reactjsexample.com/react-components-for-resizable-panel-groups-layouts/
---

 ![React components for resizable panel groups/layouts](https://cdn.hashnode.com/res/hashnode/image/upload/v1692420581242/737c938e-45da-48e3-9d21-92be310ad964.jpeg)

[![React components for resizable panel groups/layouts](https://cdn.hashnode.com/res/hashnode/image/upload/v1692420582880/ad8c0115-31df-471f-b7e1-be11a4635ea4.png)](https://user-images.githubusercontent.com/29597/210075327-faeb4ca8-31df-4dc8-a649-01d0ee3cd315.png)

## react-resizable-panels

React components for resizable panel groups/layouts.

- [View the website](https://react-resizable-panels.vercel.app/)
- [Try it on CodeSandbox](https://codesandbox.io/s/react-resizable-panels-zf7hwd)
- [Read the documentation](https://github.com/bvaughn/react-resizable-panels/tree/main/packages/react-resizable-panels)
- [View the changelog](https://github.com/bvaughn/react-resizable-panels/blob/main/packages/react-resizable-panels/CHANGELOG.md)

Supported input methods include mouse, touch, and keyboard (via [Window Splitter](https://www.w3.org/WAI/ARIA/apg/patterns/windowsplitter/)).

* * *

## FAQ

### How can I fix layout/sizing problems with conditionally rendered panels?

The `Panel` API doesn’t _require_ `id` and `order` props because they aren’t necessary for static layouts. When panels are conditionally rendered though, it’s best to supply these values.

```
<PanelGroup direction="horizontal">
  {renderSideBar && (
    <>
      <Panel id="sidebar" minSize={25} order={1}>
        <Sidebar />
      </Panel>
      <PanelResizeHandle />
    </>
  )}
  <Panel minSize={25} order={2}>
    <Main />
  </Panel>
</PanelGroup>
```

### How can I use persistent layouts with SSR?

By default, this library uses `localStorage` to persist layouts. With server rendering, this can cause a flicker when the default layout (rendered on the server) is replaced with the persisted layout (in `localStorage`). The way to avoid this flicker is to also persist the layout with a cookie like so:

##### Server component

```
import ResizablePanels from "@/app/ResizablePanels";
import { cookies } from "next/headers";

export function ServerComponent() {
  const layout = cookies().get("react-resizable-panels:layout");

  let defaultLayout;
  if (layout) {
    defaultLayout = JSON.parse(layout.value);
  }

  return <ClientComponent defaultLayout={defaultLayout} />;
}
```

##### Client component

```
"use client";

import { Panel, PanelGroup, PanelResizeHandle } from "react-resizable-panels";

export function ClientComponent({
  defaultLayout = [33, 67]
}: {
  defaultLayout: number[] | undefined
}) {
  const onLayout = (sizes: number[]) => {
    document.cookie = `react-resizable-panels:layout=${JSON.stringify(sizes)}`;
  };

  return (
    <PanelGroup direction="horizontal" onLayout={onLayout}>
      <Panel defaultSize={defaultLayout[0]}>
        {/\* ... \*/}
      </Panel>
      <PanelResizeHandle className="w-2 bg-blue-800" />
      <Panel defaultSize={defaultLayout[1]}>
        {/\* ... \*/}
      </Panel>
    </PanelGroup>
  );
}
```

A demo of this is available [here](https://github.com/bvaughn/react-resizable-panels-demo-ssr).

## GitHub

[View Github](https://github.com/nicolestandifer3/resizable-panels-react?ref=reactjsexample.com)
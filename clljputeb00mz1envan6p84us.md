---
title: "Preview Geometry Nodes on web using React"
datePublished: Sat Aug 12 2023 00:14:00 GMT+0000 (Coordinated Universal Time)
cuid: clljputeb00mz1envan6p84us
slug: preview-geometry-nodes-on-web-using-react-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692552156753/71499c62-315a-4b5d-873c-83b78dd26529.jpeg

---

---
title: Preview Geometry Nodes on web using React
published: true
date: 2023-08-12 00:14:00 UTC
tags: Graph
canonical_url: https://reactjsexample.com/preview-geometry-nodes-on-web-using-react/
---

 ![Preview Geometry Nodes on web using React](https://cdn.hashnode.com/res/hashnode/image/upload/v1692552156753/71499c62-315a-4b5d-873c-83b78dd26529.jpeg)

![Preview Geometry Nodes on web using React](https://cdn.hashnode.com/res/hashnode/image/upload/v1692552158110/96a02356-3678-43b8-8bd2-decf830f8236.png)

# Geometry Node Graph

Preview Geometry Nodes on web using React

## Getting Started

1. Clone this project: `git clone https://github.com/whoisryosuke/geometry-node-graph.git`
2. Install dependencies: `yarn`
3. Start the dev server: `yarn dev`

Open the app in your web browser, you should see a node graph.

## Previewing your nodes

This app works by using JSON files with geometry node data exported from Blender using a custom plugin (TBD). But I included the WIP script below, it should work to export some basic graphs (haven’t tested stuff like custom nodes, groups, etc).

1. Save your file somewhere.
2. Select the object with the geometry nodes modifier.
3. Go to the Scripting tab in Blender (or change one of the windows to scripting)
4. Create a new script (click the “New” button on top of window)
5. Paste in [the script from here](https://github.com/whoisryosuke/geometry-node-graph/blob/main/scripts/export-geometry-nodes.py)
6. Run the script.
7. Look inside the folder where your file is saved, you should a JSON file
8. Copy and paste that JSON file into the `src/data/` folder of this app.
9. Open up the `src/App.tsx` and swap your JSON filename for the one imported in there.
10. Hard refresh the browser/app to see changes.

## How it works

This app uses react-flow to display the node graph. It provides a lot of nice stuff out of the box, like the zooming and panning.

The nodes are generated from a JSON file that is exported from Blender using a custom Python script. It basically reads the geometry node data and creates a JSON file with the data.

> Interested in learning more? [Check out my blog](https://whoisryosuke.com/blog), where I break down how this works.

## Release

1. Bump version in `package.json`
2. `yarn build`
3. `npm publish`

## GitHub

[View Github](https://github.com/whoisryosuke/geometry-node-graph?ref=reactjsexample.com)
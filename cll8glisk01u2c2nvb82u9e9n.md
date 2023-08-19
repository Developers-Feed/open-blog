---
title: "Preview Geometry Nodes on web using React"
datePublished: Sat Aug 12 2023 00:14:00 GMT+0000 (Coordinated Universal Time)
cuid: cll8glisk01u2c2nvb82u9e9n
slug: preview-geometry-nodes-on-web-using-react
canonical: https://dev.to/mohammadtaseenkhan/preview-geometry-nodes-on-web-using-react-3ic
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691871479595/ff177c2d-51e5-4a41-b9ce-4013f65526f3.png
tags: graph

---

[![Preview Geometry Nodes on web using React](https://cdn.hashnode.com/res/hashnode/image/upload/v1691871475731/1155ec57-0e64-42ab-b6a5-8ed524e70ad9.jpeg)](https://res.cloudinary.com/practicaldev/image/fetch/s--dYXAeMih--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://reactjsexample.com/content/images/2023/08/code_2023-08-23-08-46.jpg)

[![Preview Geometry Nodes on web using React](https://cdn.hashnode.com/res/hashnode/image/upload/v1691871477122/8f4551e1-4659-436c-89d2-bd62194c930e.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--YHWj1aTR--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://github.com/whoisryosuke/geometry-node-graph/raw/main/docs/screenshot.png)

Geometry Node Graph
===================

Preview Geometry Nodes on web using React

Getting Started
---------------

1.  Clone this project: `git clone https://github.com/whoisryosuke/geometry-node-graph.git`
2.  Install dependencies: `yarn`
3.  Start the dev server: `yarn dev`

Open the app in your web browser, you should see a node graph.

Previewing your nodes
---------------------

This app works by using JSON files with geometry node data exported from Blender using a custom plugin (TBD). But I included the WIP script below, it should work to export some basic graphs (haven’t tested stuff like custom nodes, groups, etc).

1.  Save your file somewhere.
2.  Select the object with the geometry nodes modifier.
3.  Go to the Scripting tab in Blender (or change one of the windows to scripting)
4.  Create a new script (click the “New” button on top of window)
5.  Paste in [the script from here](https://github.com/whoisryosuke/geometry-node-graph/blob/main/scripts/export-geometry-nodes.py)
6.  Run the script.
7.  Look inside the folder where your file is saved, you should a JSON file
8.  Copy and paste that JSON file into the `src/data/` folder of this app.
9.  Open up the `src/App.tsx` and swap your JSON filename for the one imported in there.
10.  Hard refresh the browser/app to see changes.

How it works
------------

This app uses react-flow to display the node graph. It provides a lot of nice stuff out of the box, like the zooming and panning.

The nodes are generated from a JSON file that is exported from Blender using a custom Python script. It basically reads the geometry node data and creates a JSON file with the data.

> Interested in learning more? [Check out my blog](https://whoisryosuke.com/blog), where I break down how this works.

Release
-------

1.  Bump version in `package.json`
2.  `yarn build`
3.  `npm publish`

GitHub
------

[View Github](https://github.com/whoisryosuke/geometry-node-graph?ref=reactjsexample.com)
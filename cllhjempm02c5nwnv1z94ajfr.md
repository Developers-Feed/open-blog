---
title: "A library that simplifies the process of generating PDF files from JSON configurations"
datePublished: Wed Aug 16 2023 00:33:00 GMT+0000 (Coordinated Universal Time)
cuid: cllhjempm02c5nwnv1z94ajfr
slug: a-library-that-simplifies-the-process-of-generating-pdf-files-from-json-configurations-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692420392819/a1aad6e1-ccc6-4314-bd81-784b277fe988.jpeg

---

---
title: A library that simplifies the process of generating PDF files from JSON configurations
published: true
date: 2023-08-16 00:33:00 UTC
tags: PDF
canonical_url: https://reactjsexample.com/a-library-that-simplifies-the-process-of-generating-pdf-files-from-json-configurations/
---

# Easy React PDF

## Overview
 ![A library that simplifies the process of generating PDF files from JSON configurations](https://cdn.hashnode.com/res/hashnode/image/upload/v1692420392819/a1aad6e1-ccc6-4314-bd81-784b277fe988.jpeg)

The Easy React PDF is a library that simplifies the process of generating PDF files from JSON configurations. With this library, you can easily create complex PDF documents with various styles, layouts, and content. and make it easy for templating PDF files.

## Installation

You can install the library using npm:

```
npm install easy-react-pdf
```

### Note

you need install react, react-pdf and react-dom in your project

```
npm install react react-dom @react-pdf/renderer
```

## Usage

### Node js

#### Stream File

```
import { createStreamPDF, IPDFPage } from "easy-react-pdf";

async function main(template: IPDFPage) {
  const stream = await createStreamPDF(template);
  return stream.pipe(fs.createWriteStream("output.pdf"));
}
```

#### Create File

```
import { createFilePDF, IPDFPage } from "easy-react-pdf";

async function main(template: IPDFPage) {
  await createFilePDF(template, "path/to/file.pdf");
}
```

### React

```
import { PDFViewer } from "@react-pdf/renderer";
import { Document } from "easy-react-pdf";

function Main(template: IPDFPage) {
  return (
    <PDFViewer>
      <Document {...template} />
    </PDFViewer>
  );
}
```

## Example Template

```
const contents: IPDFPage = {
  contents: [
    {
      type: "views",
      style: {
        width: "100%",
        height: "100%",
        alignItems: "center",
        justifyContent: "center",
        display: "flex",
      },
      contents: [
        {
          type: "text",
          text: "Hello World",
          style: {
            fontSize: 20,
            fontWeight: "bold",
          },
        },
      ],
    },
  ],
  document: {
    title: "Payment Schedules",
  },
  pages: {
    size: "A4",
  },
};
```

## GitHub

[View Github](https://github.com/barared28/easy-react-pdf?ref=reactjsexample.com)
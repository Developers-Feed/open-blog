---
title: "Getting Started with WebSockets in Deno: Tutorial and Examples"
datePublished: Sun Aug 20 2023 15:19:39 GMT+0000 (Coordinated Universal Time)
cuid: clljpac5800m72rnvfll21mbn
slug: getting-started-with-websockets-in-deno-tutorial-and-examples
canonical: https://dev.to/franciscomendes10866/getting-started-with-websockets-in-deno-tutorial-and-examples-4e5i
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692551202481/38c738fb-9503-4af9-adc1-83a45a961453.jpeg
tags: tutorial, javascript, webdev, deno

---

Nowadays it is quite natural to take advantage of WebSockets, either with an in-app notification system, facilitating real-time chats, allowing collaborative tools, among many other cases.

In some programming languages or runtime environments, websockets are a real challenge. People often take advantage of community-created solutions or use services to deal with this challenge, but with Deno, it's refreshingly easy.

Introduction
============

In this article, we are going to create a REST API with two endpoints, one of which will be responsible for issuing an event, which in this case will correspond to a document that contains the message data. And another one that will establish the WebSocket connection that will send messages from the server to the client.

To give you a little more context, in this article we are going to use the following technologies:

*   [oak](https://github.com/oakserver/oak) - web framework
*   [evt](https://github.com/garronej/evt) - event emmiter replacement

Before starting this article, I recommend that you have Deno installed and that you have a brief experience using Node.

Set up project
==============

To get started, navigate to the directory of your choice and run the following command:  

    deno init .
    

Enter fullscreen mode Exit fullscreen mode

The above command is expected to have created a set of files in the workspace, with this we have initialized a Deno project and are going to make some changes to the `deno.jsonc` file.

Starting by defining some of the commands that we are going to run with task runner `deno task`:  

    {
      "tasks": {
        "dev": "deno run --watch main.ts"
      }
    }
    

Enter fullscreen mode Exit fullscreen mode

Next, let's define some dependencies that need to be imported into the project:  

    {
      // ...
      "imports": {
        "oak": "https://deno.land/x/oak@v12.5.0/mod.ts",
        "evt": "https://deno.land/x/evt@v2.4.22/mod.ts"
      }
    }
    

Enter fullscreen mode Exit fullscreen mode

With this last change in `deno.jsonc` we can consider the project's configuration as finalized and now it's time to get our hands dirty!

WebSocket Example
=================

### EventEmitter's Setup

The next step will be to instantiate the event emitter that will be used in the API, when we use the dependency [evt](https://github.com/garronej/evt) we can create a totally typesafe client and the only thing we need is define a type and pass it as a generic in the `.create()` method, like this:  

    // @/common/emitter.ts
    import { Evt } from "evt";
    
    export interface Todo {
      title: string;
      isDone: boolean;
      createdBy: string;
    }
    
    export const todoEmitter = Evt.create<Todo>();
    

Enter fullscreen mode Exit fullscreen mode

### Router Definition

Considering the previous point, we can now define each of the routes mentioned in the introduction to this article.

First, we need to import the event emitter that we just created in the previous point. Then we will create the route with the HTTP verb `POST`, this route is intended to obtain the message data (which in this case is the Todo). Without forgetting to mention that we need to access the `CreatedBy` header, so that later we will have the necessary data to emit an event.  

    // @/router.ts
    import { Router } from "oak";
    
    import { todoEmitter } from "./common/emitter.ts";
    
    export const router = new Router();
    
    router.post("/todos", async (ctx) => {
      const createdBy = ctx.request.headers.get("CreatedBy");
      if (!createdBy) ctx.throw(400);
    
      const { value } = ctx.request.body({ type: "json" });
      const data = await value;
    
      try {
        await todoEmitter.postAndWait({ ...data, createdBy });
        ctx.response.status = 200;
        ctx.response.body = { isSuccessful: true };
      } catch {
        ctx.throw(400);
      }
    });
    
    // ...
    

Enter fullscreen mode Exit fullscreen mode

Now that we've emitted an event whenever a new Todo is created, we can now create the `GET` route. First we have to check if the connection can be upgraded, if not we return an error. Next, we'll access the `CreatedBy` header to filter the messages that are sent to the client.

In fact, the `todoEmitter` is also an Async Iterator, we can iterate directly the instance and then send the WebSocket message if the creator of the Todo is exactly the same as the one in the `CreatedBy` header.  

    // @/router.ts
    import { Router } from "oak";
    
    import { todoEmitter } from "./common/emitter.ts";
    
    export const router = new Router();
    
    // ...
    
    router.get("/todos-ws", async (ctx) => {
      if (!ctx.isUpgradable) ctx.throw(501);
    
      const createdBy = ctx.request.headers.get("CreatedBy");
      if (!createdBy) ctx.throw(400);
    
      const ws = ctx.upgrade();
    
      for await (const todo of todoEmitter) {
        if (todo.createdBy === createdBy) {
          ws.send(JSON.stringify(todo));
        }
      }
    });
    

Enter fullscreen mode Exit fullscreen mode

Now we can say that we have each of the routes registered, which allows us to go to the next and last step.

### Server Definition

In this step, we will import the routes created in the previous point and make a basic configuration of the API. Like this:  

    // @/main.ts
    import { Application } from "oak";
    
    import { router } from "./router.ts";
    
    const app = new Application({ logErrors: false });
    
    app.use(router.routes());
    app.use(router.allowedMethods());
    
    app.listen({ port: 8000 });
    

Enter fullscreen mode Exit fullscreen mode

To start the process just run this command:  

    deno task dev
    

Enter fullscreen mode Exit fullscreen mode

Conclusion
==========

I hope you found this article helpful, whether you're using the information in an existing project or just giving it a try for fun.

Please let me know if you notice any mistakes in the article by leaving a comment. And, if you'd like to see the source code for this article, you can find it on the github repository linked below.

[Github Repo](https://github.com/FranciscoMendes10866/deno-oak-ws/tree/main)
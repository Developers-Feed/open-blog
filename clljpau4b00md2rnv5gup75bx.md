---
title: "React Hook: useGlobalState"
datePublished: Sun Aug 20 2023 14:35:37 GMT+0000 (Coordinated Universal Time)
cuid: clljpau4b00md2rnv5gup75bx
slug: react-hook-useglobalstate
canonical: https://dev.to/perssondennis/react-hook-useglobalstate-3c9b
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692551225433/a0ebae8a-4ece-4a84-83a6-887004726728.jpeg
tags: javascript, react, webdev, typescript

---

Sharing state between React components is crucial in most applications. With useGlobalState you can quickly share a state between multiple components without using a context provider or external lib. The hook is useful for small projects when a React context provider is not desired.

In This Article
---------------

*   [How To Use](https://dev.to/#how-to-use)
*   [Share State Between Components](https://dev.to/#share-state-between-components)
*   [useGlobalState Hook Explained](https://dev.to/#useglobalstate-hook-explained)
*   [When Not To Use](https://dev.to/#when-not-to-use)
*   [Redux and Contexts May Not Be Necessary](https://dev.to/#redux-and-contexts-may-not-be-necessary)
*   [Use Cases](https://dev.to/#use-cases)
*   [Server Rendering Support](https://dev.to/#server-rendering-support)
*   [TypeScript Version](https://dev.to/#typescript-version)
*   [PubSub Implementation](https://dev.to/#pubsub-implementation)

How To Use
----------

useGlobalState is just as easy to use as React's useState hook, only difference is that useGlobalState takes an object as first argument instead of the initial state.

The object has a required property _shareKey_ which is used to identify the data which should be shared globally. All components which uses the same shareKey will share the same data.  

    import useGlobalState from "hooks/useGlobalState";
    
    const SHARED_COUNT_KEY = "someUniqueKey";
    
    const ComponentOne = () => {
      const [count, setCount] = useGlobalState<number>({
        initialState: 0,
        shareKey: SHARED_COUNT_KEY
      });
    
      return (
        <div>
          <h2>Component one</h2>
          <div>Count: {count}</div>
          <button onClick={() => setCount(count + 1)}>Add 1</button>
        </div>
      );
    };
    
    export default ComponentOne;
    

Enter fullscreen mode Exit fullscreen mode

Share State Between Components
------------------------------

If you have multiple components, each component can use one or more of this useGlobalState hook to share state with one or multiple other component. An example with two components sharing the same state can be found on [CodeSandbox](https://codesandbox.io/s/useglobalstate-26n6kz?file=/src/useGlobalState.ts).

If you want to test the hook while reading about it, it's available to try out there on CodeSandbox or downloadable from [GitHub](https://github.com/PerssonDennis/examples/tree/main/useGlobalState).

[![Sharing is caring](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551220283/84529beb-14c6-4c7c-99d5-dbf2cb2d1e98.jpeg)](https://res.cloudinary.com/practicaldev/image/fetch/s--0FOL_ob9--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://www.perssondennis.com/images/articles/react-hook-use-global-state/sharing-is-caring.webp)  
_Why not share this article with a friend?_

useGlobalState Hook Explained
-----------------------------

Let's take a look at the implementation of the hook, and later we look at some use cases.  

    import { pubSub } from "lib/pubsub"
    import { useCallback, useEffect, useState } from "react"
    
    const useGlobalState = ({
      initialState,
      onStateUpdated,
      shareKey
    }) => {
      const [state, setState] = useState(initialState)
    
      const onStateUpdate = useCallback(
        (data) => {
          setState(data)
          onStateUpdated?.(data)
        },
        [onStateUpdated]
      )
    
      useEffect(() => {
        pubSub.subscribe(shareKey, onStateUpdate)
    
        return () => pubSub.unsubscribe(shareKey, onStateUpdate)
      }, [onStateUpdate, shareKey])
    
      const setSharedState = useCallback(
        (data) => {
          pubSub.emit(shareKey, data)
        },
        [shareKey]
      )
    
      return [state, setSharedState]
    }
    
    export default useGlobalState
    

Enter fullscreen mode Exit fullscreen mode

First thing first, the hook depends on a pubsub import. In short, the pubsub import is what is actually used to share the state between components with the help of subscription and events. No React context needed. You can find the implementation of it at [GitHub](https://github.com/PerssonDennis/examples/blob/main/useGlobalState/src/pubsub.ts) or [at the end of this article](https://dev.to/#pubsub-implementation), together with [TypeScript](https://dev.to/#typescript-version) versions of the useGlobalState hook.

Second thing to notice, the hook takes an object with three properties. As can be seen in the TypeScript version a bit further down, _shareKey_ is the only required property. That is the key used to identify the data you share. Components which uses this hook with the same shareKey will share the same state. If different shareKeys are used, they will not share the state. Simple as that.

_initialState_ is an optional property you can use to use to set an initial state. If you use this one, make sure to use the same initial state for all components using the same shareKey. Providing different values when you want to share a state doesn't make sense.

Last argument property is _onStateUpdate_. It's a callback that can be used to listen at state updates if that would be of interest.

The rest of the code is just to subscribe and unsubscribe to the pubsub, and to emit new values to it when setting a new state.

[

![perssondennis](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551221282/656d1058-b243-4b9b-9130-97b29a0a5d69.png)

](https://dev.to/perssondennis)[

React Anti-Patterns and Best Practices - Do's and Don'ts
--------------------------------------------------------

### Dennis Persson ・ Feb 5

#react #javascript #webdev #programming



](https://dev.to/perssondennis/react-anti-patterns-and-best-practices-dos-and-donts-3c2g)

When Not To Use
---------------

Before talking about when to use this hook, I want to discuss when not to use it. As a developer, you should never just go with first available solution without consider the alternatives. You can read [this article about proactive vs reactive developers](https://www.perssondennis.com/articles/why-you-should-not-be-a-reactive-developer) to understand why that is important.

If the project you are coding on already uses a state handling solution like Redux or MobX, you likely have no need for this hook. Better option would be to continue on that path. In fact, if you plan to store a good amount of data, Redux is still a good option to consider for that.

Another tough concurrent to this hook is regular React contexts. Let's face it, contexts are built for React and default option to store small states. It's perfect to use if you need to add some small functions to fake a small store, like a Redux store.

Remember though, a context combined with a reducer which many people promote as a replacement for Redux [is NOT a good option](https://www.perssondennis.com/articles/how-to-avoid-react-context-trap#contexts-is-not-always-the-solution) if you need to store states larger than tiny. In that article, I just linked, you can find [five reasons to why Redux is to prefer over reducer-context solution](https://www.perssondennis.com/articles/how-to-avoid-react-context-trap#how-can-redux-save-us-from-the-context-trap).

Redux and Contexts May Not Be Necessary
---------------------------------------

Did I just convince you Redux and Contexts are more viable options than the hook in this article? Or did I scare you from using contexts? Either way, let's continue the discussion with some actual use cases and benefits of this hook.

React projects can be of any kind and any size. New hooks, libraries and frameworks are coming every day. Some of the hooks from the latest years are [RTK Query](https://redux-toolkit.js.org/rtk-query/overview#use-hooks-in-components) and some other popular hooks like [useSWR](https://swr.vercel.app/) and [useQuery](https://tanstack.com/query/v4/docs/react/reference/useQuery). With hooks like that, it's definitely not an obvious choice to use Redux as it used to be.

Hooks like useSWR work by caching your requests. You share the state between components by a cache which is built into the hook. The interesting thing here, is that useSWR hook does not require a context provider, it relies on a [global cache unless you opt in for a context for manual cache control](https://swr.vercel.app/docs/advanced/cache).

The useGlobalState is a concise example of what the cache control for a hook like useSWR could look like internally. And in fact, I'm very glad useSWR went for a solution without a context. Not because it's cumbersome to add a context provider, but because contexts are [more complex to architect than you may think](https://www.perssondennis.com/articles/how-to-avoid-react-context-trap). In general, moving them further up in the component tree means more rerenders, while moving them down leads to isolated contexts which are more difficult to keep synced with each other.

[![When to use react hook](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551222172/a0900bf1-70d0-4c46-b68d-5d2f9be8c7af.jpeg)](https://res.cloudinary.com/practicaldev/image/fetch/s--V7u6RNz2--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://www.perssondennis.com/images/articles/react-hook-use-global-state/when-to-use-react-hook.webp)  
_Easy Lenny, it's time now_

Use Cases
---------

With the previous chapters in mind, about usages of Redux and contexts, we can now tell a few cases when this hook could be suitable to use.

**1\. Library Without a Need For a Context Provider**

As discussed earlier, we can use this hook when implementing a small library which needs a global state. With this hook, there's no need to use a context provider for the lib user.

**2\. Singleton Hook**

You can use this hook in another hook to make that hook a singleton hook. Normally, each component which uses a hook gets a new state for that hook. The state of the hook is not shared with other components using the same hook.

In some cases, you want a hook which can share the state between all usages of the same hook. In that case, you can use this hook within you implemented hook to share its state, basically making it a singleton hook.

**3\. One Time Usages for Small Projects**

Some projects are small. Adding Redux or a context or whatever you need may not be necessary. A small project with a single or a few pages can likely be small enough to just need a single shared state. Maybe it's even a proof of concept project. This hook may come in handy in that case.

[

![perssondennis](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551223410/8a97181b-a3ab-4b34-99bc-de7e69dbf242.png)

](https://dev.to/perssondennis)[

Why Server Components - A Brief History of Web
----------------------------------------------

### Dennis Persson ・ Jul 9

#react #nextjs #webdev #javascript



](https://dev.to/perssondennis/why-server-components-a-brief-history-of-web-198h)

Server Rendering Support
------------------------

When you are using Next.js or other solutions where server side rendering may occur, you must as usual remember that component and hook states calculated on the server isn't available on the client. Not with this hook, not with React contexts and not with Redux. The states are stored one the client.

That doesn't mean that this hook cannot be used when server rendering exists. The hook does work with server rendering, it's just that the state will not be propagated to the server, it will stay on the client.

TypeScript Version
------------------

Even though I'm pretty sure TypeScript haters know TypeScript well enough to spot the types and remove them on their own, I still used the JavaScript implementation above, just because it's easy to overview. The TypeScript hook uses TypeScript generics to let you use use it with any type, custom or built in.  

    import { pubSub } from "lib/pubsub"
    import { useCallback, useEffect, useState } from "react"
    
    interface UseGlobalStateProps<T> {
      shareKey: string
      initialState?: T
      onStateUpdated?: (data?: T) => void
    }
    
    const useGlobalState = <T>({
      initialState,
      onStateUpdated,
      shareKey
    }: UseGlobalStateProps<T>) => {
      const [state, setState] = useState<T>(initialState as T)
    
      const onStateUpdate = useCallback(
        (data: T) => {
          setState(data)
          onStateUpdated?.(data)
        },
        [onStateUpdated]
      )
    
      useEffect(() => {
        pubSub.subscribe(shareKey, onStateUpdate)
    
        return () => pubSub.unsubscribe(shareKey, onStateUpdate)
      }, [onStateUpdate, shareKey])
    
      const setSharedState = useCallback(
        (data: T) => {
          pubSub.emit(shareKey, data)
        },
        [shareKey]
      )
    
      return [state, setSharedState] as [T, (data: T) => void]
    }
    
    export default useGlobalState
    

Enter fullscreen mode Exit fullscreen mode

PubSub Implementation
---------------------

The pubsub TypeScript implementation the hook depends on is quite standard. It keeps a record of subscribers and provides functions for subscribing and unsubscribing to events. It is possible to subscribe to different events by calling the _subscribe_ function with different values for _event_ argument.

The PubSub object also has an _emit_ function which can be used to submit events which will be propagated to all subscribers. If a subscriber would subscribe after some events already has been emitted, the last event for each event is stored and can optionally be emitted with the _emitLatestOnSubscribe_ option passed in as an argument to the _subscribe_ function.

The _emitLatestOnSubscribe_ option is recommended to be used when React components are rendered conditionally. In that way, components can receive the latest state whenever they are mounted.  

    type PubSubCallback = (data: any) => void;
    
    interface PubSubSubscribeOptions {
      emitLatestOnSubscribe?: boolean;
    }
    
    interface PubSub {
      emit: (event: string, data: unknown) => void;
      latestEvents: Record<string, unknown>;
      subscribe: (
        event: string,
        callback: PubSubCallback,
        options?: PubSubSubscribeOptions
      ) => void;
      subscribers: Record<string, PubSubCallback[]>;
      unsubscribe: (event: string, callback: PubSubCallback) => void;
    }
    
    export const pubSub: PubSub = {
      latestEvents: {},
      subscribers: {},
    
      subscribe: (event, callback, options = { emitLatestOnSubscribe: true }) => {
        const { emitLatestOnSubscribe } = options;
    
        if (!pubSub.subscribers[event]) {
          pubSub.subscribers[event] = [];
        }
    
        pubSub.subscribers[event].push(callback);
    
        if (
          emitLatestOnSubscribe &&
          Object.prototype.hasOwnProperty.call(pubSub.latestEvents, event)
        ) {
          callback(pubSub.latestEvents[event]);
        }
      },
    
      unsubscribe: (event, callback) => {
        if (pubSub.subscribers[event]) {
          pubSub.subscribers[event] = pubSub.subscribers[event].filter(
            (cb) => cb !== callback
          );
        }
      },
    
      emit: (event, data) => {
        if (pubSub.subscribers[event]) {
          pubSub.latestEvents[event] = data;
          pubSub.subscribers[event].forEach((callback) => {
            callback(data);
          });
        }
      },
    };
    

Enter fullscreen mode Exit fullscreen mode

[

![perssondennis image](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551224313/2a408c1b-3b1d-470b-9248-ea92e952ed5f.png)

](https://dev.to/perssondennis)

[Dennis Persson](https://dev.to/perssondennis)Follow
----------------------------------------------------

[I'm a former teacher writing articles about software development and everything around it. My ambition is to provide people all around the world with free education and humorous reading.](https://dev.to/perssondennis)
---
title: "Use PHP code right within your React / Next.js App"
datePublished: Tue Nov 07 2023 00:33:00 GMT+0000 (Coordinated Universal Time)
cuid: clp1cumqq00030alhhgepcb15
slug: use-php-code-right-within-your-react-nextjs-app

---

---
title: Use PHP code right within your React / Next.js App
published: true
date: 2023-11-07 00:33:00 UTC
tags: Nextjs, php
canonical_url: https://reactjsexample.com/use-php-code-right-within-your-react-next-js-app/
---

## Next.js `use php`
 ![Use PHP code right within your React / Next.js App](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149051271/2871f648-c01e-4870-81df-c52caab24315.jpeg)

Use PHP right inside of your Next.js project. Just like `use server` (not really).

**You can watch how i made it [here](http://www.youtube.com/watch?v=EGOkjmyfL6E)**

[![Use PHP code right within your React / Next.js App](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149052555/35ccc56e-8c7d-45d3-860e-6622aa0cafd0.jpeg)](http://www.youtube.com/watch?v=EGOkjmyfL6E "Write PHP in Next.js/React Components")

You can use it in React Server Components just like this:

```
return (
    <button
        formAction={async () => {
            'use php'
            (new PDO('mysql:host=localhost:3306;dbname=public', 'root', 'root'))
                ->prepare("INSERT INTO Bookmarks (slug) VALUES (?)")
                ->execute(array('new'));
            }}>
        Insert Bookmark
    </button>
)
```

And if you want to it can even work with React Client Components

```
// actions.js
'use server'

export async function phpHelloWorld() {
    'use php'
    print "Hello from PHP";
}

// page.tsx
import {phpHelloWorld} from "../actions";
```

Yes this actually works. Trust me I wish it wouln’t too.

## Build

You can build the implementation by

```
npm run build
npm run start
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

If you want to try out the Database Example, you can use the docker-compose file provided in the repository. after `docker-compose up -d` you need to create the database and table you want to insert into manually.

## Roadmap (Things that should be fixed but realistically it will never happen)

- There is a probably a way to fix that nasty preprocess step with [SWC Plugins](https://swc.rs/docs/plugin/ecmascript/getting-started) which are still in Beta with Next.js and also I think they will switch builder anyways soon so what’s the point really? But hey if anyone wants to do it feel free.
- I guess there is some hacky way to make props binding possible.

## Credits

Check out the original implementations by elnardu for C and Rust:

- [https://github.com/elnardu/react-use-c](https://github.com/elnardu/react-use-c)
- [https://github.com/elnardu/react-use-rust](https://github.com/elnardu/react-use-rust)

## Disclaimer

_I hope I don’t have to say this but: If you even in the slightest consider to use this in any application at all you are an absolute madperson and and should be locked out of the internet for the rest of your life, I hope you find some other fun activity, maybe gardening or woodwork._

## Self-Promo

If you enjoyed this project and want to see more silly web development projects, you can follow me on [Twitter](https://twitter.com/bufferhead_), [Bluesky](https://bsky.app/profile/bufferhead.bsky.social) and [Youtube](https://www.youtube.com/@bufferhead_).

## GitHub

[View Github](https://github.com/bufferhead-code/nextjs-use-php?ref=reactjsexample.com)
---
title: "What is REST or REST API ? in easy language"
datePublished: Sun Aug 20 2023 12:36:47 GMT+0000 (Coordinated Universal Time)
cuid: clljpc5fo00ki1envfvipf09a
slug: what-is-rest-or-rest-api-in-easy-language
canonical: https://dev.to/diwakarkashyap/what-is-rest-or-rest-api-in-easy-language-5a8m
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692551287286/e517b622-4e1c-4e49-be12-86c18dab6644.png
tags: programming, webdev, beginners, restapi

---

> First i Start with Easy approach then move forward to traditional approach

Imagine a restaurant.

1.  **Restaurant (The Server)**: The restaurant has a kitchen where food is prepared.
2.  **Menu (API Endpoints)**: The menu lists all the dishes you can order. Just like the menu has different dishes, an API has different endpoints or functions you can request.
3.  **Waiter (The Middleman or Interface)**: To order food, you give your order to the waiter. The waiter is like the API. You ask it for something, and it goes to the kitchen (the server) to get it for you.
4.  **Ordering (Making a Request)**: You ask the waiter for a specific dish from the menu. Similarly, with an API, you make a specific request to get certain information.
5.  **Receiving Your Food (Getting a Response)**: The waiter brings back your dish from the kitchen. Similarly, after you make a request to an API, it gives back the information (response) you asked for.

Now, the word "REST" in "REST API" is just a set of rules or guidelines for how this ordering and delivering process should work. It's like saying, "the waiter should always be polite, always write down the order, and always bring the dish from the kitchen in a certain way."

In the digital world, a REST API is a way for different software applications to talk to each other using these guidelines. So when you're using an app on your phone, and it shows you the weather, it might be using a REST API to ask a weather server for the current temperature. The server responds, and then the app displays the temperature to you.

> Let's Move to Traditional approach

let's dive a bit deeper.

A REST API (Representational State Transfer Application Programming Interface) is a set of rules and conventions for building and interacting with web services. The core ideas behind a RESTful approach are:

1.  **Resources**: In REST, every piece of information or data is considered a resource, and each resource should have a unique identifier, usually a URL. For example, in a book store API, each book could be a resource and might have a unique URL like `https://api.bookstore.com/books/1`.
    
2.  **HTTP Methods**: RESTful services use standard HTTP methods to perform operations on resources:
    
    *   **GET**: Retrieve information. E.g., fetching details of a book.
    *   **POST**: Create a new resource. E.g., adding a new book to the store.
    *   **PUT**: Update an existing resource. E.g., updating details of a book.
    *   **DELETE**: Remove a resource. E.g., deleting a book from the store.
3.  **Statelessness**: Every request from a client to a server must contain all the information needed to understand and process the request. The server should not store anything about the client's session between requests. This makes the system more scalable and robust.
    
4.  **JSON or XML**: While RESTful APIs can use any format for sending data, JSON (JavaScript Object Notation) and XML (eXtensible Markup Language) are the most common formats used for transferring data.
    
5.  **Communication**: In REST, communication is typically done over HTTP/HTTPS, and the API responses are fast because of their stateless nature.
    
6.  **Status Codes**: REST uses standard HTTP status codes to indicate the success or failure of an API request. For example, "200 OK" means the request was successful, while "404 Not Found" means the requested resource was not found.
    

Benefits of REST API:

1.  **Interoperability**: Can be used across any platform or device that understands HTTP.
2.  **Scalability**: Due to its stateless nature, RESTful systems can be easily scaled.
3.  **Standardized**: Uses standard HTTP methods and status codes which makes it easier to understand.
4.  **Performance**: Efficient communication using standard web protocols.

To sum up, a REST API provides a set of rules and conventions for how web services should be designed and accessed. When you use websites or apps that fetch data from the internet (like seeing tweets on Twitter, posts on Facebook, or products on Amazon), behind the scenes, they're likely using REST APIs to request and receive that data.

Thank you for reading. I encourage you to follow me on Twitter where I regularly share content about JavaScript and React, as well as contribute to open-source projects and learning golang. I am currently seeking a remote job or internship.

Twitter: [https://twitter.com/Diwakar\_766](https://twitter.com/Diwakar_766)

GitHub: [https://github.com/DIWAKARKASHYAP](https://github.com/DIWAKARKASHYAP)

Portfolio: [https://diwakar-portfolio.vercel.app/](https://diwakar-portfolio.vercel.app/)
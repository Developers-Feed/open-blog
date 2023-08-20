---
title: "How to work with OpenAI APIs"
datePublished: Sun Aug 20 2023 14:02:25 GMT+0000 (Coordinated Universal Time)
cuid: clljpc0qf00mz2rnv82bf72za
slug: how-to-work-with-openai-apis
canonical: https://dev.to/godopetza/how-to-work-with-openai-apis-1478
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692551281390/da819bad-cbdd-451f-9f4a-a0b67c372e28.png
tags: api, openai

---

If you are confused about how OpenAI APIs work, this post will give you a high overview and explain to you how you can utilize the Basic Chat Completion API.

Just like any other RESTful APIs you have worked with before, all we do is setup a request from our client and send the payload to OpenAI’s server and we will receive a response back from them based on the query we sent.

[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551279193/ac5761e2-32fd-4655-b189-1c4fa97339c8.jpeg)](https://res.cloudinary.com/practicaldev/image/fetch/s--6UwyTHKO--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/t637s1yazyyxfl31ymmq.jpg)

But what do you put in the client request?

The client request is composed of the instructions that we want OpenAI to process and then send back a response based off this payload. For OpenAI, the payload will consist of the model we want to use, messages (prompt, assistant and user messages) and temperature.

[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551280388/39ff3b0a-525a-499b-9085-374bc8b216b3.jpeg)](https://res.cloudinary.com/practicaldev/image/fetch/s--6BZ6Wq2D--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/y77s1gg7nph5jieoweog.jpg)

As seen above, messages will contain three sets of roles, system, assistant, and user. All the messages should be added to this list if you are working with a chatbot that needs to have the memory of previous chats between user and assistant.

For the temperature, the lower the temperature the more predictable and repetitive the responses returned will be. 0.7 is the recommended temperature but tune it to fit your needs.

I hope you have learned something new!

Don’t forget to follow my socials for more of these short tutorials.

[Twitter](https://twitter.com/godopetza)

[LinkedIn](https://www.linkedin.com/in/benard-andrew-5b29069b/)
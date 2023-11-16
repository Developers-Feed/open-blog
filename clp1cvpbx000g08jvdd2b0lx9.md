---
title: "Simple implementation of Autogen with FastApi backend and React frontend"
datePublished: Thu Nov 02 2023 00:09:00 GMT+0000 (Coordinated Universal Time)
cuid: clp1cvpbx000g08jvdd2b0lx9
slug: simple-implementation-of-autogen-with-fastapi-backend-and-react-frontend

---

---
title: Simple implementation of Autogen with FastApi backend and React frontend
published: true
date: 2023-11-02 00:09:00 UTC
tags: FastAPI
canonical_url: https://reactjsexample.com/simple-implementation-of-autogen-with-fastapi-backend-and-react-frontend/
---

# Autogen with FastApi backend and React frontend
 ![Simple implementation of Autogen with FastApi backend and React frontend](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149102419/214680bf-e5dc-4694-9f3a-275bfcdca8cf.jpeg)

This is a simple implementation of Autogen Agents using FastApi as backend and a frontend client using React

1. **FastApi Backend** : A FastApi application running autogen.
2. **Webapp** : React webapp using websocket to communicate with FastApi.

## Running demo

1. **Clone this repo**

```
git clone https://github.com/bonadio/autogenwebdemo.git
cd autogenwebdemo

```

1. **Configure backend**

Configure python deps

```
cd backend
pip install -r ./requirements.txt 

```

Add your Openai key to .env inside src folder

```
cd backend/src (edit .env and add your key)

```

Start backend server inside src folder

```
python main.py

```

You should see

```
INFO: Started server process [85614]
INFO: Waiting for application startup.
INFO: Application startup complete.
INFO: Uvicorn running on http://0.0.0.0:8000 (Press CTRL+C to quit)

```

1. **Configure frontend**

Open a new terminal and go to the react-frontend folder (you need to have nodejs installed and npm >= v14 )

```
cd autogenwebdemo/react-frontend
npm install
npm run dev

```

Open you browser on [http://localhost:5173/](http://localhost:5173/) or the port shown

Send the following messages:

```
-> Hi
<- Hello! How can I assist you today?

-> What the status of my order?
<- Sure, I can help you with that. Could you please provide me with your order number and customer number?

-> Order 222
<- Thank you for providing the order number. Could you also please provide me with your customer number?

-> customer 333
<- The status of your order with order number 222 and customer number 333 is "delivered". Is there anything else I can assist you with?

```

![Simple implementation of Autogen with FastApi backend and React frontend](https://github.com/bonadio/autogenwebdemo/raw/main/chat.png "Chat")

Have fun!

## GitHub

[View Github](https://github.com/bonadio/autogenwebdemo?ref=reactjsexample.com)
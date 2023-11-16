---
title: "An email client built with the Next.js App Router and Postgres as the database"
datePublished: Wed Nov 08 2023 00:57:00 GMT+0000 (Coordinated Universal Time)
cuid: clp1cugdd000d08jv8orr9i7n
slug: an-email-client-built-with-the-nextjs-app-router-and-postgres-as-the-database

---

---
title: An email client built with the Next.js App Router and Postgres as the database
published: true
date: 2023-11-08 00:57:00 UTC
tags: Email,Nextjs
canonical_url: https://reactjsexample.com/an-email-client-built-with-the-next-js-app-router-and-postgres-as-the-database/
---

# Next.js Email Client
 ![An email client built with the Next.js App Router and Postgres as the database](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149041637/7aa7b7e5-defd-4817-82ee-bf5ded0c71c4.jpeg)

This is a simple email client built with Next.js and Postgres. It’s built to show off some of the features of the App Router, which enable you to build products that:

- Navigate between routes in a column layout while maintaining scroll position (layouts support)
- Submit forms without JavaScript enabled (progressive enhancement)
- Navigate between routes extremely fast (prefetching and caching)
- Retain your UI position on reload (URL state)

The first version of the UI was built with [v0](https://v0.dev/t/RPsRRQilTDp).

[![An email client built with the Next.js App Router and Postgres as the database](https://cdn.hashnode.com/res/hashnode/image/upload/v1700149043314/a3187cec-decf-4fa8-8fd0-e73838fea4d9.png)](https://user-images.githubusercontent.com/9113740/280543133-1e33ad53-832f-410e-a4d6-7bd40f666aa8.png)

## Tech

- [Next.js](https://nextjs.org/)
- [Vercel Postgres](https://vercel.com/docs/storage/vercel-postgres)
- [Tailwind CSS](https://tailwindcss.com/)
- [TypeScript](https://www.typescriptlang.org/)
- [React Aria Components](https://react-spectrum.adobe.com/react-aria/index.html)

## Known Issues

- Forward / reply / search aren’t hooked up yet
- Need to add a way to manage folders
- Need to add a way to manage users
- Fix to/from to pull sender/recipient everywhere
- Error handling for form submissions

## Schema

```
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(255) UNIQUE NOT NULL
);

CREATE TABLE emails (
    id SERIAL PRIMARY KEY,
    sender_id INTEGER REFERENCES users(id),
    recipient_id INTEGER REFERENCES users(id),
    subject VARCHAR(255),
    body TEXT,
    sent_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE folders (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50) NOT NULL
);

CREATE TABLE user_folders (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id),
    folder_id INTEGER REFERENCES folders(id)
);

CREATE TABLE email_folders (
    id SERIAL PRIMARY KEY,
    email_id INTEGER REFERENCES emails(id),
    folder_id INTEGER REFERENCES folders(id)
);

```

## Sample Data

```
INSERT INTO users (first_name, last_name, email)
VALUES ('John', 'Doe', 'john.doe@example.com'),
       ('Jane', 'Doe', 'jane.doe@example.com'),
       ('Alice', 'Smith', 'alice.smith@example.com'),
       ('Bob', 'Johnson', 'bob.johnson@example.com');

INSERT INTO emails (sender_id, recipient_id, subject, body, sent_date)
VALUES (1, 2, 'Meeting Reminder', 'Don''t forget about our meeting tomorrow at 10am.', '2022-01-10 09:00:00'),
       (1, 3, 'Hello', 'Just wanted to say hello.', '2022-01-09 08:00:00'),
       (2, 1, 'Re: Meeting Reminder', 'I won''t be able to make it.', '2022-01-10 10:00:00'),
       (3, 1, 'Re: Hello', 'Hello to you too!', '2022-01-09 09:00:00'),
       (4, 1, 'Invitation', 'You are invited to my party.', '2022-01-11 07:00:00'),
       (1, 2, 'Work Project', 'Let''s discuss the new work project.', '2022-01-12 07:00:00'),
       (1, 4, 'Expenses Report', 'Please find the expenses report attached.', '2022-01-13 07:00:00'),
       (4, 1, 'Personal Note', 'Let''s catch up sometime.', '2022-01-14 07:00:00');

INSERT INTO folders (name)
VALUES ('Inbox'),
       ('Flagged'),
       ('Sent'),
       ('Work'),
       ('Expenses'),
       ('Personal');

INSERT INTO user_folders (user_id, folder_id)
VALUES (1, 1), (1, 2), (1, 3), (1, 4), (1, 5), (1, 6),
       (2, 1), (2, 2), (2, 3), (2, 4), (2, 5), (2, 6),
       (3, 1), (3, 2), (3, 3), (3, 4), (3, 5), (3, 6),
       (4, 1), (4, 2), (4, 3), (4, 4), (4, 5), (4, 6);

INSERT INTO email_folders (email_id, folder_id)
VALUES (1, 1),
       (2, 1),
       (3, 3),
       (4, 1),
       (5, 1),
       (6, 4),
       (7, 5),
       (8, 6);

```

## Database Relationships

- Users can send and receive emails (users.id -> emails.sender\_id and emails.recipient\_id)
- Users can have multiple folders (users.id -> user\_folders.user\_id)
- Folders can contain multiple emails (folders.id -> email\_folders.folder\_id)
- An email can be in multiple folders (emails.id -> email\_folders.email\_id)

## GitHub

[View Github](https://github.com/leerob/nextjs-postgres-email-client?ref=reactjsexample.com)
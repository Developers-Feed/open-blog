---
title: "A React App that interfaces with the Spotify API to allow users to search for artist"
datePublished: Thu Aug 10 2023 00:10:00 GMT+0000 (Coordinated Universal Time)
cuid: clljozbbj00kq2rnvh5fv5r89
slug: a-react-app-that-interfaces-with-the-spotify-api-to-allow-users-to-search-for-artist-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692550685545/65de15e6-04f3-44dc-8e42-561a666f6202.jpeg

---

---
title: A React App that interfaces with the Spotify API to allow users to search for artist
published: true
date: 2023-08-10 00:10:00 UTC
tags: Spotify,Apps
canonical_url: https://reactjsexample.com/a-react-app-that-interfaces-with-the-spotify-api-to-allow-users-to-search-for-artist/
---

# DiscographyBrowser
 ![A React App that interfaces with the Spotify API to allow users to search for artist](https://cdn.hashnode.com/res/hashnode/image/upload/v1692550685545/65de15e6-04f3-44dc-8e42-561a666f6202.jpeg)

![A React App that interfaces with the Spotify API to allow users to search for artist](https://cdn.hashnode.com/res/hashnode/image/upload/v1692550687141/6cd8ace2-04ce-401b-9018-f817ef7ebd7a.png)

DiscoBrowser is a React.js application that interfaces with the Spotify API to allow users to search for an artist and view their albums. Key functionalities include:

- **Authentication**
  - Client credentials stored in a secure .env file are read into the React application, which then utilizes them to authenticate with the Spotify API, fetching an access token for further requests.
- **Searching for an artist**
  - Users can input an artist’s name in a search bar, and the application fetches the artist’s ID.
- **Displaying albums**
  - Once the artist’s ID is retrieved, the application fetches all the albums related to that artist and displays them in a grid format using Bootstrap cards.
  - Within the card, the album artwork is displayed, as well as the album’s title, # of tracks, and release date.
- **Navigation to Spotify**
  - Upon clicking on the album’s artwork (per Spotify’s Developer agreement mandate), the user is brought to the Spotify page for that album.

## Dev Process

This project was developed using Visual Studio Code as the code editor. The application utilizes Node Project Manager, as well as React.js, React hooks (useState, useEffect), React-bootstrap components, and Bootstrap CSS. All Spotify API calls were written manually, without the use of wrapper libraries.

## Testing

While I wish I could say that I followed best-practices and used a unit testing suite such as Jest, that simply was not the case. This project had significant time constraints, and thus testing was limited to manual tests with console logging. Errors are handled via console logs, as well as catch blocks around any fetch operations that eliminate main failure points.

## GitHub

[View Github](https://github.com/nxrada/DiscographyBrowser?ref=reactjsexample.com)
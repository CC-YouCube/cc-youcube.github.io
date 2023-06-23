# Spotify Support

In order to enable Spotify support, you need to create a Spotify application, you can do this by following [this guide](https://developer.spotify.com/documentation/web-api/concepts/apps). After that, you need to set the environment variables `SPOTIPY_CLIENT_ID` and `SPOTIPY_CLIENT_SECRET`.

???+ info
    The application cannot access features such as your playlists, follows, or likes. It is solely designed to interact with the Spotify API. Additionally, the application will provide statistics on your YC server's Spotify usage.

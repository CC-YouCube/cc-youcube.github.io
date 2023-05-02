# Home

YouCube is a service for accessing media providers in ComputerCraft, the popular Minecraft mod that allows players to program in-game computers using the Lua programming language. With YouCube, you can easily stream media from your favorite providers, all from the comfort of your in-game computer.

Whether you're looking to listen to music, watch movies, or catch up on the latest TV shows, YouCube has you covered. Simply install YouCube, enter a URL or search term, and start exploring all that YouCube has to offer.

So why wait? Start enjoying the best in media entertainment with YouCube today!

## Examples

<iframe width="560" height="315" src="https://www.youtube.com/embed/bgUDokOr38M" title="YouCube Example 1" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/dz96Y4mo0GI" title="YouCube Example 2" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Supported Sites

YouCube is optimized for [YouTube]. It supports [Spotify], but only when the YouCube server has it enabled. It supports [all sites from yt-dlp], as well as yt-dlp's generic downloader. So, if you can find a direct link to a media file, YouCube will probably be able to play it.

[YouTube]: https://www.youtube.com
[Spotify]: https://www.spotify.com
[all sites from yt-dlp]: https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md

## How it works

```mermaid
sequenceDiagram
    autonumber
    actor Client
    box rgb(33,66,99) Server
        participant Sanic
        participant YT-DLP
        participant Cache
        participant FFmpeg
        participant Sanjuuni
    end
    Note over Cache: Folder on server
    Note over Sanic: Web server
    Client-)Sanic: Sends a media request
    Note over Sanic: If the media is from spotify<br/>use spotipy to get information to<br/>create a serch term
    Sanic--)YT-DLP: Get information about the media
    Sanic-)Client: Tells the client<br/>inforamtion about the media
    Sanic--)YT-DLP: Downloads media
    YT-DLP-)Cache: Stores media in cache
    Sanic--)FFmpeg: Convert audio to dfpwm
    FFmpeg-)Cache: Stores audio in cache
    Sanic--)Sanjuuni: Convert video to 32vid
    Sanjuuni-)Cache: Stores video in cache
    Cache->Cache: Deletes original downloaded media
    loop Streaming
        Client-)Sanic: Request video and audio chunks
        Cache-)Sanic: Reads video and audio chunks
        Sanic-)Client: Sends video and audio chunks
        Note over Client: Receives and displays the media
    end
```

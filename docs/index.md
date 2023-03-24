# Home

YouCube is a service for accessing media providers in ComputerCraft, the popular Minecraft mod that allows players to program in-game computers using the Lua programming language. With YouCube, you can easily stream media from your favorite providers, all from the comfort of your in-game computer.

Whether you're looking to listen to music, watch movies, or catch up on the latest TV shows, YouCube has you covered. Simply install YouCube, enter a URL or search term, and start exploring all that YouCube has to offer.

So why wait? Start enjoying the best in media entertainment with YouCube today!

## Examples

<iframe width="560" height="315" src="https://www.youtube.com/embed/bgUDokOr38M" title="YouCube Example 1" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/dz96Y4mo0GI" title="YouCube Example 2" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## How it works

<!---
add this when Mermaid has been upgraded
https://github.com/squidfunk/mkdocs-material/issues/5251

    box rgb(33,66,99) Server
        participant Sanic
        participant YT-DLP
        participant Cache
        participant FFmpeg
        participant Sanjuuni
    end
-->

```mermaid
sequenceDiagram
    autonumber
    actor Client
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

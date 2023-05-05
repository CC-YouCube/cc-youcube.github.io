# Server Installtion guide

## Docker

The YC [docker] iamge can be pulled from [ghcr.io/cc-youcube/youcube:latest](https://github.com/CC-YouCube/server/pkgs/container/youcube)

```shell
docker pull ghcr.io/cc-youcube/youcube:latest
```

You can also build the Image your self buy using YouCube's [Dockerfile]

### Docker Compose

This is an example of using the image with docker-compose

```yaml
version: "2.0"
services:
  youcube:
    image: ghcr.io/cc-youcube/youcube:latest
    restart: always
    hostname: youcube
    ports:
      - 5000:5000
```

## Manual Installtion

!!! warning
    **Firstly, It is not recommended to install YC manually.
    If there is some security issue with handling files, then your server might be at risk.
    You still want to install YC server manually, then it is recommended to run it with a user that has almost no permissions.**

Firstly clone [the repository].

=== "HTTPS"

    ```shell
    git clone https://github.com/CC-YouCube/server.git
    ```

=== "SSH"

    ```shell
    git clone git@github.com:CC-YouCube/server.git
    ```
=== "Github CLI"

    ```shell
    gh repo clone CC-YouCube/server
    ```
=== "ZIP"

    [Download](https://github.com/CC-YouCube/server/archive/refs/heads/main.zip)

=== "Visual Studio"

    [Open with Visual Studio](git-client://clone?repo=https%3A%2F%2Fgithub.com%2FCC-YouCube%2Fserver)

=== "GitHub Desktop"

    [Open with GitHub Desktop](x-github-client://openRepo/https://github.com/CC-YouCube/server)
    
    ???+ note
        
        If nothing happens, [download GitHub Desktop](https://desktop.github.com/) and try again. 

Then you'll need to install the following dependencies to install the YouCube server:

- [FFmpeg] ([Compilation Guide](https://trac.ffmpeg.org/wiki/CompilationGuide))
- [sanjuuni] ([Compilation Guide](https://github.com/MCJack123/sanjuuni#building))
- [Python 3.7+]
- ???+ info "[YC's Python requirements]"

        ```shell
        pip install -r src/requirements.txt
        ```

[FFmpeg]: https://ffmpeg.org/download.html
[sanjuuni]: https://github.com/MCJack123/sanjuuni#installation
[YC's Python requirements]: https://github.com/CC-YouCube/server/blob/main/src/requirements.txt
[Python 3.7+]: https://www.python.org/downloads
[docker]: https://www.docker.com
[the repository]: https://github.com/CC-YouCube/server

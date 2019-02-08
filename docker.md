# Docker commands

## Containers

Pull a container: `docker container pull <image>`

Run a container and show output: `docker container run <image>`

Run a container in interactive mode: `docker container run -it <image>`

Run a container in detached mode: `docker container run -d <image>`

Bash on a running container: `docker exec -it <container> bash`

## Dockerfile

Build a Dockerfile:

```bash
# In the Dockerfile directory
docker build . -t <image_name>
```

Example:

```Dockerfile
FROM microsoft/dotnet:sdk AS build
COPY src /app
WORKDIR /app
RUN dotnet build -c Release

FROM microsoft/dotnet
COPY --from=build /app/bin/Release/netcoreapp2.2 /app
WORKDIR /app
ENTRYPOINT ["dotnet", "FilesApi.dll"]
```

## docker-compose

`docker-compose.yml`

Example:

```yml
version: "3"

services:
  filesapi:
    image: filesapi
  converterapi:
    image: converterapi
  notesapi:
    image: notesapi
    ports:
      - "5000:80"
```

## Tutorials

1. [Running &amp; Inspecting Containers](https://gist.github.com/remilapeyre/b74878d81a234156fbc73312124ed4b6)
2. [Interactive Containers](https://gist.github.com/remilapeyre/bc9f903ffecb50288e70be4a3db7082a)
3. [Detached Containers and Logging](https://gist.github.com/remilapeyre/9423750e66c9bffc1d510dac45f070c6)
4. [Starting, Stopping, Inspecting and Deleting Containers](https://gist.github.com/remilapeyre/3d47dd76c36ff03e213ea4d679ee5630)
5. [Interactive Image Creation](https://gist.github.com/remilapeyre/362116cb465fa9fcf324b113b4708e83)
6. [Creating Images with Dockefiles](https://gist.github.com/remilapeyre/82d5a51c43a93e7472ff2111f382d81d)
7. [Creating Images with Dockerfiles 2](https://gist.github.com/remilapeyre/27673be52375a34b27bea831a93fc5e1)
8. [Multi-Stage Build](https://gist.github.com/remilapeyre/71874264d18656540217d0d8d4986bee)
9. [Database Volumes](https://gist.github.com/remilapeyre/78b0cb77e8df23a156fb5ba0a9e1d430)
10. [Introduction to Container Networking](https://gist.github.com/remilapeyre/1091c586f4707ad35a0d73f160b4c53f)
11. [Container Port Mapping](https://gist.github.com/remilapeyre/11f4084ce9ffb11966099c165d18c1e6)
12. [Starting a Compose App](https://gist.github.com/remilapeyre/584a901a680cc7caada5510292899087)
13. [Scaling a Compose App](https://gist.github.com/remilapeyre/feae3487329802d424e320a37c7e185c)
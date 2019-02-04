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
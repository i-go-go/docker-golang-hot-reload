# Docker for Go Development with Hotreload

This repo contains `Dockerfile` for image containing Go v1.13 and [Air](https://github.com/cosmtrek/air) reloader.

## How to Use

Docker image: `docker.pkg.github.com/i-go-go/docker-golang-hot-reload/devbox:1.13`

```
app:
    image: docker.pkg.github.com/i-go-go/docker-golang-hot-reload/devbox:1.13
    volumes:
      - /path/to/your/application:/app

    # Optional
    environment:
      HOTRELOAD_APP_CMD: "command --params"
```

Image version is equal used Golang version in `Dockerfile`. Directory with source code of your application should
be mapped to internal directory `/app` in container. You can add special environment variable `HOTRELOAD_APP_CMD`
for passing custom commands and params to your Go application.

Also you can use this image as base for your own `Dockerfile`:
```
FROM docker.pkg.github.com/i-go-go/docker-golang-hot-reload/devbox:1.13
```

## Image Publishing
```
docker login -u <USERNAME> -p <GITHUB_TOKEN> docker.pkg.github.com
docker build -t docker-golang-hot-reload ./1.13/
docker tag docker-golang-hot-reload docker.pkg.github.com/i-go-go/docker-golang-hot-reload/devbox:1.13
docker push docker.pkg.github.com/i-go-go/docker-golang-hot-reload/devbox:1.13
```

## Licence
The MIT License (MIT). Please see [License File](./LICENSE.md) for more information.

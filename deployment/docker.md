# Docker

Firstly install docker, on a mac you can use [Homebrew](https://brew.sh) `brew cask install docker` on any other platform just follow [these instructions](https://docs.docker.com/install/).

> Please note that Boost Docker image doesn't come with a PostgreSQL database so you need to have one at hand in order for the system to work. For more information oh how to install PostgreSQL please refer to the following [page](https://www.postgresql.org/download/).
>
> To build Boost and test everything compiles as it supposed to, you can do `make build`

The basic setup to run Boost using docker could be as follows:

```bash
docker run \
    -e DB_HOST=postgre.example.com \
    -e DB_PASSWORD=MySup3rS3cr£tP4ssword \
    liveui/boost
```

All parameters available are listed on [Custom app configuration](https://github.com/LiveUI/Boost/wiki/Custom-app-configuration) page.

## Docker on macOS

It is very easy to run Boost from a Docker on macOS. If you have your PostgreSQL database hosted locally you can run something like:

```bash
docker run \
    -e DB_HOST=docker.for.mac.host.internal \
    -e DB_USER=boost \
    -e DB_PASSWORD=aaaaaa \
    -e DB_NAME=boost \
    -p 80:8080 \
    liveui/boost
```

where `docker.for.mac.host.internal` points to the IP address of your host, whatever it is while `-p 80:8080` exposes internal port 8080 \(used by Boost\) to your port 80. Try `http://localhost/ping` to test.

For the full set of available environmental variables please refer to the [Configuration](https://github.com/LiveUI/Boost/wiki/Custom-app-configuration#environmental-variables).


[![Docker Image CI](https://github.com/daiyeqi/docker-tengine/actions/workflows/docker.yml/badge.svg)](https://github.com/daiyeqi/docker-tengine/actions/workflows/docker.yml)
[![License: Apache 2.0](https://img.shields.io/badge/license-Apache_2.0-blue.svg)](LICENSE)

# docker-tengine

```console
$ docker pull ghcr.io/daiyeqi/tengine
$ docker run -p 80:80 \
    -v /host/path/nginx.conf:/etc/nginx/nginx.conf:ro \
    --name tengine -d ghcr.io/daiyeqi/tengine
```

## License
This project is licensed under the [Apache-2.0 License](LICENSE).
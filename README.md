[![build](https://github.com/daiyeqi/docker-tengine/actions/workflows/docker.yml/badge.svg)](https://github.com/daiyeqi/docker-tengine/actions/workflows/docker.yml)
[![Docker pulls](https://img.shields.io/docker/pulls/daiyeqi/tengine.svg)](https://hub.docker.com/r/daiyeqi/tengine/)
[![GitHub release](https://img.shields.io/github/release/daiyeqi/docker-tengine.svg)](https://github.com/daiyeqi/docker-tengine/releases)
[![GitHub License](https://img.shields.io/github/license/daiyeqi/docker-tengine)
](https://github.com/daiyeqi/docker-tengine/blob/main/LICENSE)

# docker-tengine

```console
$ docker pull ghcr.io/daiyeqi/tengine
$ docker run -p 80:80 \
    -v /host/path/nginx.conf:/etc/nginx/nginx.conf:ro \
    --name tengine -d ghcr.io/daiyeqi/tengine
```

## Tengine

  
<a href="https://tengine.taobao.org" target="_blank">
<img alt="Tengine" src="https://github.com/alibaba/tengine/raw/master/docs/image/tengine-logo.png">
</a>
<br>

[![GitHub CI](https://github.com/alibaba/tengine/actions/workflows/ci.yml/badge.svg)](https://github.com/alibaba/tengine/actions/workflows/ci.yml)
[![GitHub Releases](https://img.shields.io/github/release/alibaba/tengine.svg)](https://github.com/alibaba/tengine/releases)
[![GitHub Issues or Pull Requests](https://img.shields.io/github/issues/alibaba/tengine)](https://github.com/alibaba/tengine/issues)
[![GitHub License](https://img.shields.io/github/license/alibaba/tengine)](https://github.com/alibaba/tengine/blob/master/LICENSE)


[**Tengine**](https://github.com/alibaba/tengine) 是由淘宝发起的Web服务器项目。它在Nginx的基础上，针对大访问量网站的需求，添加了很多高级功能和特性。Tengine的性能和稳定性已经在大型的网站如淘宝，天猫，优酷，全球速卖通，Lazada，阿里云等得到了很好的检验。Tengine将向通用API网关方向持续演进和发展，在HTTP应用流量入口网关的基础上，逐步支持4/7层TLS，TCP，UDP和GRPC多协议路由能力，适配不同终端和不同应用，打造全场景通用网关，持续保持Tengine业界领先地位。

## Tongsuo

<a href="https://www.tongsuo.net/" target="_blank">
<img alt="Tengine" src="https://github.com/Tongsuo-Project/Tongsuo/raw/master/tongsuo.png" width=300px>
</a>
<br>
<br>

[![GitHub CI](https://github.com/Tongsuo-Project/Tongsuo/workflows/GitHub%20CI/badge.svg)](https://github.com/Tongsuo-Project/Tongsuo/actions?query=workflow%3A%22GitHub+CI%22)
[![GitHub Releases](https://img.shields.io/github/release/Tongsuo-Project/Tongsuo.svg)](https://github.com/Tongsuo-Project/Tongsuo/releases)
[![GitHub Issues or Pull Requests](https://img.shields.io/github/issues/Tongsuo-Project/Tongsuo)](https://github.com/Tongsuo-Project/Tongsuo/issues)
[![GitHub License](https://img.shields.io/github/license/Tongsuo-Project/Tongsuo)](https://github.com/Tongsuo-Project/Tongsuo/blob/master/LICENSE.txt)

[**铜锁/Tongsuo**](https://github.com/Tongsuo-Project/Tongsuo) 是一个提供现代密码学算法和安全通信协议的开源基础密码库，为存储、网络、密钥管理、隐私计算等诸多业务场景提供底层的密码学基础能力，实现数据在传输、使用、存储等过程中的私密性、完整性和可认证性，为数据生命周期中的隐私和安全提供保护能力。


## License
This project is licensed under the [Apache-2.0 License](LICENSE).
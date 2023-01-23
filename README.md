# Envoy

![](diagram.drawio.svg)


## Install

```
brew install envoy
```

## Getting Started

request -> envoy (running on local) -> www.envoyproxy.io

```
envoy -c envoy-demo.yaml
```

```
curl -v localhost:10000
```

### Submodules

1. [envoy](https://github.com/envoyproxy/envoy): this is part of [Setup the sandbox environment](https://www.envoyproxy.io/docs/envoy/latest/start/sandboxes/setup#start-sandboxes-setup)
## Contents

1. [helloworld](helloworld)
1. [internal listener](internal-listener)
1. [grpc-json](grpc-json)
1. [healthcheck](healthcheck)
1. [OpenTelemetry](opentelemetry)

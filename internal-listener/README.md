# [Internal listener](https://www.envoyproxy.io/docs/envoy/latest/configuration/other_features/internal_listener)

[simple chain](https://github.com/envoyproxy/envoy/blob/main/configs/internal_listener_proxy.yaml)

## Config
1. bootstrap extensions

    ```yaml
    bootstrap_extensions:
    - name: envoy.bootstrap.internal_listener
      typed_config:
        "@type": type.googleapis.com/envoy.extensions.bootstrap.internal_listener.v3.InternalListener
    ```
1. add a listener with `internal_listener`

    ```yaml
    - name: internal
      internal_listener: {}
      filter_chains:
        - filters:
            - name: tcp
              typed_config:
                "@type": type.googleapis.com/envoy.extensions.filters.network.tcp_proxy.v3.TcpProxy
                stat_prefix: encap
                cluster: helloworld
    ```
1. Add cluster `internal_listener`

    ```yaml
    - name: internal_listener
      load_assignment:
        cluster_name: internal_listener
        endpoints:
          - lb_endpoints:
              - endpoint:
                  address:
                    envoy_internal_address:
                      server_listener_name: internal
    ```
## Run

1. Run

    ```
    go run ../shared/main.go
    ```

1. Curl

    ```
    curl localhost:8090/hello
    hello
    ```
1. Run envoy
    ```
    envoy -c envoy.yaml
    ```
1. Access via envoy
    ```
    curl localhost:10000/hello
    hello
    ```

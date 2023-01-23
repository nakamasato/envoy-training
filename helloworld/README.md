# Hello World


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

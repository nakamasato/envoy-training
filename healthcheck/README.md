# Healthcheck

## Config

```yaml
          http_filters:
          - name: envoy.filters.http.health_check
            typed_config:
              "@type": type.googleapis.com/envoy.extensions.filters.http.health_check.v3.HealthCheck
              pass_through_mode: false
              headers:
                name: ':path'
                string_match: { exact: '/health' }
```


## Run

```
envoy -c envoy.yaml
```

```
curl -s -o /dev/null -w "%{http_code}" http://localhost:51051/health
200
```

# Instruction

## Action
```bash
docker run --name agent --network grafanet -e AGENT_MODE=flow -v $(pwd)/config.river:/etc/agent/config.river -p 9999:9999 -p 12345:12345 grafana/agent run --server.http.listen-addr=0.0.0.0:12345 /etc/agent/config.river
```
**Or temporary configuration**
```bash
docker run --name agent --rm --network grafanet -e AGENT_MODE=flow -v $(pwd)/config.river:/etc/agent/config.river -p 4318:4318 -p 12345:12345 grafana/agent run --server.http.listen-addr=0.0.0.0:12345 /etc/agent/config.river
```

```bash
docker run --name loki --network grafanet -d -v $(pwd)/loki.yaml:/mnt/config/loki.yaml -p 3100:3100 grafana/loki:2.9.1 -config.file=/mnt/config/loki.yaml
```

**RAW Log**
```
cart {"level":"info","time":"2023-12-05T13:08:05.302+0700","file":"middleware/request_logger.go:354","message":"GET /ready
z 200 OK 2.730857ms","time":"2023-12-05T13:08:05.299+0700","method":"GET","uri":"/readyz","status":"200 OK","latency":"2.7
30857ms","userAgent":"kube-probe/1.21"}
cart {"level":"info","time":"2023-12-05T13:08:15.299+0700","file":"middleware/request_logger.go:354","message":"GET /livez
 200 OK 44.887µs","time":"2023-12-05T13:08:15.299+0700","method":"GET","uri":"/livez","status":"200 OK","latency":"44.887µ
s","userAgent":"kube-probe/1.21"}
cart {"level":"info","time":"2023-12-05T13:08:15.302+0700","file":"middleware/request_logger.go:354","message":"GET /ready
z 200 OK 2.526692ms","time":"2023-12-05T13:08:15.299+0700","method":"GET","uri":"/readyz","status":"200 OK","latency":"2.5
26692ms","userAgent":"kube-probe/1.21"}
```

**JSON**
Endpoint: `http://localhost:4318/v1/<matrics / traces / logs>
POSTMAN Header via bulk edit: `Content-Type:application/json`
```json
Please use postman collection
```

## Receiver
https://grafana.com/docs/agent/latest/flow/reference/components/otelcol.receiver.otlp/#http-block 

## Postman Payload Example
https://github.com/open-telemetry/opentelemetry-proto/tree/main/examples
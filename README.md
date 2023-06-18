```sh
docker compose exec consul-server consul members
docker compose exec consul-server /bin/sh -c "echo '{\"service\": {\"name\": \"counting\", \"tags\": [\"go\"], \"port\": 9001}}' >> /consul/config/counting.json"
docker compose exec consul-server consul reload
dig +short @127.0.0.1 -p 8600 counting.service.consul
```

```sh
curl 127.0.0.1:8500/v1/catalog/services
```

# KONG db-less acme example
- start
```
docker-compose up -d
```
- update config using [`HTTPIe`](https://httpie.io/)
```
http :8001/config config=@kong.yaml

```
- trigger force renews certs
```
curl -i localhost:8001/acme -d host=your-domain.name
```
```
HTTP/1.1 201 Created
Date: Fri, 10 Sep 2021 06:47:07 GMT
Content-Type: application/json; charset=utf-8
Connection: keep-alive
Access-Control-Allow-Origin: *
Content-Length: 63
X-Kong-Admin-Latency: 492
Server: kong/2.5.0

{"message":"certificate for host your-domain.name is created"}
```

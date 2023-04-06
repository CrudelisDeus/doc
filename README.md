# Doc service (docker-example)

## Service example

[<img src="./docs/img/logo/logo.png" alt="Link my doc site" width="150" height="150" style="display:block; margin:auto;">](https://satan.com.ua/)

## Run service

```bash
docker-compose up -d
```

## Change port

To change the port, go to docker-compose.yaml and change 8000:8000 to your port, for example 80:8000

```yaml
services:
    ports:
      - "80:8000"
```
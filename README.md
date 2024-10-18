# Setup

```bash
$ sudo systemctl start docker
$ ./scripts/init_db.sh
```

## Cargo

```bash
$ RUST_LOG=trace cargo run | bunyan
```

## Docker

```bash
$ docker buildx build --tag zero2prod --file Dockerfile .
$ docker run --rm --name zero2prod --network zero2prod -e APP_ENVIRONMENT=docker -e RUST_LOG=trace -p 8000:8000 zero2prod | bunyan
```

# Usage

```bash
$ xh -v http://127.0.0.1:8000/health_check
$ xh -v --form post http://127.0.0.1:8000/subscriptions name=me
email=example@mine.mail
```


# Build and Push demo

## Setup

```sh
python3 -m venv .venv
. .venv/bin/activate
pip install -r requirements.txt 
```

## Test it

```sh
flask --app hello run
```

## Build and run docker image

```sh
docker buildx build --platform linux/amd64 --no-cache -t build-and-push:1.0.0 -f Dockerfile .
docker tag build-and-push:1.0.0 build-and-push:latest
docker run -p 5001:5001 build-and-push
```

Demo app should now be accessible at `http://localhost:5001` from your browser.
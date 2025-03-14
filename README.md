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

Demo app should now be accessible at `http://localhost:5000` from your browser.

## Build and run docker image locally

```sh
docker buildx build --platform linux/amd64 --no-cache -t build-and-push:1.0.0 -f Dockerfile .
docker tag build-and-push:1.0.0 build-and-push:latest
docker run -p 5001:5001 build-and-push
```

Demo app should now be accessible at `http://localhost:5001` from your browser.

## Automatic build and publish to Docker Hub

When a change is committed to main, github actions will automatically build and publish this image.

You can run it locally:

```sh
* docker run -p 5001:5001 inbleric/build-and-push:latest
```

Demo app should now be accessible at `http://localhost:5001` from your browser.
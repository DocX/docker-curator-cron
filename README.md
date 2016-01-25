# Curator CRON task in Docker 

Dockerized version of Elasticsearch Curator run as CRON daily task. Useful for production deployment to manage time-based indices.

## Why this image

This image allows you to deploy scheduled Curator task as Docker container in fraction of second. There are couple of good 
images that run the command just once. But if you use infrastructure like AWS ECS, Kubernetes and similar, you may want to 
start one container that runs as a service and keeps your Elasticsearch indices tidy.

## Usage

Image entrypoint is set to curator script wrapper, that creates daily CRON task and starts `crond`. Use transparently as 
you would run `curator` command directly:

```
docker run --rm docx/curator-cron:3.4.0 --host 1.2.3.4 --port 80 delete indices --older-than 1 --time-unit days 
--timestamp '%Y.%m.%d'
```


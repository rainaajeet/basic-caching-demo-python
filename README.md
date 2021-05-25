
<div style="position: absolute; top: 0px; right: 0px;">
    <img width="200" height="200" src="https://redislabs.com/wp-content/uploads/2020/12/RedisLabs_Illustration_HomepageHero_v4.svg">
</div>

<div style="height: 150px"></div>

# Django(python) Redis caching Example

Show how the redis works with Django(Python).

# Overview video

Here's a short video that explains the project and how it uses Redis:

[![Watch the video on YouTube](docs/YTThumbnail.png)](https://youtube.com/watch?v=x4dwTM97tBM)

# Redis rate-caching example front

![How it works](docs/screenshot001.png)

# Redis rate-caching example (command line)

![How it works](docs/radis-ching.png)

## Try it out
<p>
    <a href="https://heroku.com/deploy" target="_blank">
        <img src="https://www.herokucdn.com/deploy/button.svg" alt="Deploy to Heorku" width="200px"/>
    <a>
</p>
<p>
    <a href="https://vercel.com/new/git/external?repository-url=https://github.com/deliveryweb/redis-caching-python/tree/dev&env=REDIS_HOST,REDIS_PORT,REDIS_PASSWORD" target="_blank">
        <img src="https://vercel.com/button" alt="Deploy with Vercel" width="200px" height="50px"/>
    </a>
</p>
<p>
    <a href="https://deploy.cloud.run/?dir=google-cloud-run" target="_blank">
        <img src="https://deploy.cloud.run/button.svg" alt="Run on Google Cloud" width="200px"/>
    </a>
    (See notes: How to run on Google Cloud)
</p>

## How to run on Google Cloud
<p>
    After successful deployment, you need to manually enable the vpc connector as shown in the pictures:
</p>

1. Open link google cloud console.
![1 step](docs/1.png)
2. Click "Edit and deploy new revision" button.
![2 step](docs/2.png)
3. Select vpc-connector and deploy application.
![3 step](docs/3.png)

<a href="https://github.com/GoogleCloudPlatform/cloud-run-button/issues/108#issuecomment-554572173">
Problem with unsupported the flags when deploying google cloud run button
</a>

---

## How to run it locally?

### Run docker compose or install redis manually
Install docker (on mac: https://docs.docker.com/docker-for-mac/install/)

```sh
docker network create global
docker-compose up -d --build
```

#### If you install redis manually open django-backend/configuration folder and copy `.env.example` to create `.env`. And provide the values for environment variables
    - REDIS_HOST: Redis server host
    - REDIS_PORT: Redis server port
    - REDIS_DB: Redis server db index
    - REDIS_PASSWORD: Redis server password

#### Setup and run backend
Install python, pip and venv (on mac: https://installpython3.com/mac/)

Use python version: 3.8
``` sh
python3 -m venv venv
source ./venv/bin/activate
pip3 install -r requirements.txt
python3 manage.py collectstatic
gunicorn configuration.asgi:application -b 127.0.0.1:5000 -k uvicorn.workers.UvicornWorker
```

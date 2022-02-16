---
description: How to install RadioPanel via Docker.
---

# Installing RadioPanel

{% hint style="info" %}
Make sure you have docker installed before setting up radiopanel: [https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script](https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script)
{% endhint %}

### Step 1: Setting Up docker-compose.yaml

Create a new file called `docker-compose.yaml` within an empty directory and load in the following content.

{% hint style="warning" %}
Make sure to change the appropriate variables (keys, password, etc...)
{% endhint %}

```yaml
version: "2.4"
services:
    api:
        image: radiopanel/radiopanel-api:1.0.0-rc.14
        container_name: radiopanel-api
        volumes:
            - ./uploads:/home/node/uploads:delegated
        env_file:
            - .env
        depends_on:
            database:
                condition: service_healthy

    app:
        image: radiopanel/radiopanel-app:1.0.0-rc.14
        container_name: radiopanel-app
        volumes:
            - ./certbot/conf:/etc/letsencrypt
        ports:
            - 80:80
            - 443:443
        env_file:
            - .env
        depends_on:
            - api

    database:
        image: postgres:12.3-alpine
        container_name: radiopanel-postgres
        environment:
            POSTGRES_DB: radiopanel
            POSTGRES_USER: localuser
            POSTGRES_PASSWORD: CHANGE_ME
            PGDATA: /data/db
        volumes:
            - ./data:/data/db
        healthcheck:
            test: ["CMD-SHELL", "pg_isready -U localuser -d radiopanel"]
            interval: 10s
            timeout: 5s
            retries: 5

    redis:
        image: redis:6.0.6-alpine
        container_name: redis
        command: ["redis-server", "--appendonly", "yes"]
        volumes:
            - redis-data:/data

volumes:
    redis-data:
```

{% hint style="info" %}
Once postgres is started once with the `POSTGRES_PASSWORD`set, you can not change the password again!
{% endhint %}

### Step 2: Setting Up .env

In the same directory create a `.env` file with the following content and change the needed variables:

```yaml
PORT=80
NODE_ENV=production

DOMAIN=yourdomain.com
SSL=false
FRONTEND_BASEURL=http://yourdomain.com
UPSTREAM=api

TYPEORM_CONNECTION=postgres
TYPEORM_HOST=database
TYPEORM_PORT=5432
TYPEORM_USERNAME=localuser
TYPEORM_PASSWORD=CHANGE_ME
TYPEORM_DATABASE=radiopanel
TYPEORM_LOGGING=false
TYPEORM_LOGGER=advanced-console
TYPEORM_SSL=false

MAIL_HOST=CHANGE_ME
MAIL_PORT=CHANGE_ME
MAIL_SECURE=CHANGE_ME
MAIL_USER=CHANGE_ME
MAIL_PASSWORD=CHANGE_ME

JWT_PRIVATE=CHANGE_ME

REDIS_HOST=redis
REDIS_PORT=6379
```

### Step 3: Starting RadioPanel

Now use the command `docker-compose up -d` and visit your domain to continue the installation. It can take up to 5 minutes for RadioPanel to setup.

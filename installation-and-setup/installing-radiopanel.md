---
description: How to install RadioPanel via Docker.
---

# Installing RadioPanel

{% hint style="info" %}
Make sure you have Docker installed before setting up RadioPanel: [https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script](https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script)
{% endhint %}

### Step 1: Setting Up docker-compose.yml

Create a new file called `docker-compose.yml` within an empty directory and load in the following content.

{% hint style="warning" %}
Make sure to change the appropriate variables (keys, password, etc...)
{% endhint %}

```yaml
version: "2.4"
services:
    api:
        image: radiopanel/radiopanel-api:1.0.0-rc.15
        container_name: radiopanel-api
        volumes:
            - ./uploads:/home/node/uploads:delegated
        env_file:
            - .env
        depends_on:
            database:
                condition: service_healthy

    app:
        image: radiopanel/radiopanel-app:1.0.0-rc.15
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

{% hint style="warning" %}
Change `POSTGRES_PASSWORD` to a suitable secure value.

Once RadioPanel has been started for the first time with this value set, it **cannot** be changed.
{% endhint %}

### Step 2: Setting Up .env

In the same directory create a `.env` file with the following content and change the needed variables:

```shell
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

#### .env Variable Help

* `DOMAIN` should be the domain your RadioPanel instance will be accessible on. This is used for certificate provisioning via [Lets Encrypt](https://letsencrypt.org). For localhost installs, set this to `localhost`
* `FRONTEND_BASEURL` should be set to the actual web address your RadioPanel instance will be accessible on, including the protocol. For localhost installs, set this to `http://localhost:[port]`
* `TYPEORM_PASSWORD` must match the value of `POSTGRES_PASSWORD` specified earlier in the `docker-compose.yml` file
* The `MAIL_` variables are used as settings so RadioPanel can send emails to users.  You can use your own mail server, or even send emails from your own email address through your email provider's SMTP services.
  * `MAIL_HOST` and `MAIL_PORT`should be set to the SMTP server hostname and port respectively
    * Common ports include **25**, **465** and **587** depending on the service.
  * `MAIL_SECURE` should be set to `true` or `false` based on whether to use SSL/TLS
  * `MAIL_USER` and `MAIL_PASS` correspond to the username and password to use for authentication.
* `JWT_PRIVATE` is used as the secret for many sensitive operations. Ensure this variable is set to a secure, unique string.

{% hint style="warning" %}
Failure to set the `MAIL_` variables correctly may result in errors when inviting users or when sending password reset emails. Setting up an SMTP service is outside the scope of this guide.
{% endhint %}

{% hint style="info" %}
The email address emails are sent from can be changed. See [Customising RadioPanel](setting-up-radiopanel/customising-radiopanel.md)
{% endhint %}

### Step 3: Starting RadioPanel

Now use the command `docker-compose up -d` and visit your domain to continue the installation. It can take up to 5 minutes for RadioPanel to setup.

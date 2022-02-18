# How to update RadioPanel?

### Step One: Update your docker-compose

In your `docker-compose.yaml` file, edit the images for `app` and `api`.

The latest images are:

* `api`: `radiopanel/radiopanel-api:1.0.0-rc.18`
* `app`: `radiopanel/radiopanel-app:1.0.0-rc.18`

### Step Two: Restart your Docker containers

You do this by running `docker-compose down` followed by `docker-compose up -d`.

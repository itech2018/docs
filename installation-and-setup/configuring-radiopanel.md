---
description: Setting up RadioPanel's settings from the website after install.
---

# Configuring RadioPanel

{% hint style="info" %}
All of these settings can be changed in the RadioPanel settings after RadioPanel has been setup.
{% endhint %}

### Step 1: Setting up your Admin Account

In this step you will provide your email address, username and password for your RadioPanel account. You will be using your email address and password to login. Your username is what shows on your RadioPanel profile.

### Step 2: Creating your Station

In this step you will provide the station name and station URL. The station name will be shown on the panel.

### Step 3: Setting up your Stream Information

#### AzuraCast:

* AzuraCast Base URL: This is the URL to your AzuraCast installation. It should look this this: `http://<IP>:<PORT>`. This URL should **NOT** not end with a `/`.
* AzuraCast Station ID: The number representing your AzuraCast station. This can be found in the URL when on your AzuraCast dashboard for your station.
* AzuraCast API key, a full length working API key from AzuraCast. This can be created from the AzuraCast Dashboard.

#### **Manual Configuration |** Icecast:

For Icecast streams you would append /status-json.xsl to the end of your URL. For example: `http://<IP>:<PORT>/status-json.xsl`

#### **Manual Configuration |** Shoutcast:

For Shoutcast streams you would append /status-json.xsl to the end of your URL. For example: `http://<IP>:<PORT>/stats?json=1`

#### **Manual Configuration |** Zeno.FM:

Zeno.FM streams need to grab data from their API. You will need your Station ID. It can be found by looking at the end part of your stream URL. For example: `http://stream.zeno.fm/<STATION_ID>`

You will need to change out that ID into their API link, ex: `https://proxy.zeno.fm/api/stations/<STATION_ID>/now_playing/`

### Step 4: Setting up Song Matching

Here you can setup how RadioPanel should find the correct metadata for playing songs. You have following options:

* Deezer
* Apple Music
* Spotify

It is recommend to use Spotify as it is the most accurate and has high limits with API keys.

To use Spotify you will need to create a Spotify developers account. Go to [https://developer.spotify.com/](https://developer.spotify.com) and click on _Dashboard_ Once you are there, press "Create an App" Name it whatever you want. It doesn't matter.

After you filled these things in correctly and saved your changes you should start to see your song history fill up after a minute.

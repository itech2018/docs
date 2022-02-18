---
description: >-
  This page contains some small code snippets to interact with the Radiopanel
  api through Python
---

# Python

## Get the live DJ

```python
import requests
headers = {
    "Authorization": "YOUR_AUTHORIZATION_HEADER"
}

j = requests.get("https://api.radiopanel.co/api/v1/slots/live", headers=headers)

if j.text == "":
    # This function gets triggered when no one is live.
    t = "Auto DJ"
else:
    # This function gets triggered when someone is live.
    json = j.json()
    t = str(json["user"]["username"])
```

Thanks to Destinyyy#4581 for this example

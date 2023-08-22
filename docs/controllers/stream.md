# Stream Controller

**Necessary imports**
```python
from mediaApiClient import *
```

## Get stream by filter

**Initialization proxy class**

```python
contentApi = ClientStreamControllerV2(DOMEN, AUTHORIZATION_TOKEN)

response = contentApi.get_stream_for_content(episode_id, account_id, manifest, use_https)
```

manifest (str) : "all", "hls", "dash", "mss"

its optional field (have default value = "all", may be **None** or not setting) 

use_https (bool)

its optional field (have default value = true, may be **None** or not setting) 

episode_id

this id you can take from episode of film or episode of serial

account_id

this unique account id that created by client

**Examples**

```python
contentApi = ClientStreamControllerV2(DOMEN, AUTHORIZATION_TOKEN)

response = contentApi.get_stream_for_content(episode_id, account_id)
response = contentApi.get_stream_for_content(episode_id, account_id, "mss", None)
response = contentApi.get_stream_for_content(episode_id, account_id, None, False)
```

```json
{
  "thumbUrl": null,
  "streams": [
    {
      "type": "dash",
      "name": "Playready",
      "url": "https://vb4.uma.media/***"
    },
    {
      "type": "mss",
      "name": "Playready",
      "url": "https://vb4.uma.media/***"
    }
  ]
}
```

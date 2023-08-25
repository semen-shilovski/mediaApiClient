# Service Controller

**Necessary imports**
```python
from mediaApiClient import *
```

## Get all services

**Initialization proxy class**

```python
contentApi = ClientServiceControllerV1(DOMEN, AUTHORIZATION_TOKEN)

response = contentApi.get_services()
```

Response type List[LightWeightService]

example :
```json
[
  {
    "id": 1,
    "name": "amediateka",
    "description": "Amediateka"
  },
  {
    "id": 2,
    "name": "start",
    "description": "Start"
  },
  {
    "id": 3,
    "name": "premier",
    "description": "Premier"
  }
]
```

# Account Controller

**Necessary imports**
```python
from mediaApiClient import *
```

## Get all accounts

**Initialization proxy class**

```python
contentApi = ClientAccountControllerV1(DOMEN, AUTHORIZATION_TOKEN)

response = contentApi.get_all_accounts()
```

return type List[LightWeightAccount]

example of json :
```json
[
  {
    "id": 12,
    "accountId": "account_from_library",
    "status": {
      "id": 1,
      "title": "ACTIVE",
      "description": "Пользователь активен"
    },
    "created": "2023-08-25T12:00:32.616618",
    "services": [
      "start",
      "amediateka"
    ]
  }
]
```

## Get account by id

**Initialization proxy class**

```python
contentApi = ClientAccountControllerV1(DOMEN, AUTHORIZATION_TOKEN)

response = contentApi.get_account_by_id("account_from_library")
```

return type AccountFullInfo

example of json :
```json
{
  "accountId": "account_from_library",
  "connectedServices": [
    {
      "id": 1,
      "name": "amediateka",
      "description": "Amediateka"
    },
    {
      "id": 2,
      "name": "start",
      "description": "Start"
    }
  ]
}
```

## Create account

**Initialization proxy class**

```python
contentApi = ClientAccountControllerV1(DOMEN, AUTHORIZATION_TOKEN)

account_to_create = AccountToCreate(
    accountId="test_account_01",
    servicesIds=[1, 2, 3]
)
response = contentApi.create_account_by_request("account_from_library")
```

return type AccountFullInfo

example of json:
```json
{
  "accountId": "test_account_01",
  "connectedServices": [
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
}
```

## Delete account by id

**Initialization proxy class**

```python
contentApi = ClientAccountControllerV1(DOMEN, AUTHORIZATION_TOKEN)

response = contentApi.delete_account_by_id("test_account_01")
```

Nothing return to you,but if failed -> method throw Exception

## Add service to account by account_id and service_id

**Initialization proxy class**

```python
contentApi = ClientAccountControllerV1(DOMEN, AUTHORIZATION_TOKEN)

response = contentApi.add_service_for_account("test_account_01", 1)
```

Nothing return to you,but if failed -> method throw Exception

## Delete service for account by account_id and service_id

**Initialization proxy class**

```python
contentApi = ClientAccountControllerV1(DOMEN, AUTHORIZATION_TOKEN)

response = contentApi.disable_service_for_account("test_account_01", 1)
```

Nothing return to you,but if failed -> method throw Exception


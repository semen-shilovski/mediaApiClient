# Compilation Controller

**Necessary imports**
```python
from mediaApiClient import *
```

## Get all compilations

**Initialization proxy class**

```python
contentApi = ClientCompilationControllerV2(DOMEN, AUTHORIZATION_TOKEN)

response = contentApi.get_all_compilations()
```

return type List[LightWeightCompilation]

example of json:
```json
[
  {
    "id": "de2866fa-868d-40d2-8253-07812a559940",
    "title": "My first compilation",
    "description": "it's compilation created with help of library",
    "provider": "anything",
    "tags": [
      "first tag",
      "second tag",
      "third tag"
    ],
    "contentIds": [
      "3755dbfd82f34c19b72d45602073cb0c"
    ]
  }
]
```

## Get full compilation by id and page

**Initialization proxy class**

```python
contentApi = ClientCompilationControllerV2(DOMEN, AUTHORIZATION_TOKEN)

response = contentApi.get_full_compilation_by_id(compilation_id, number, size)
response = contentApi.get_full_compilation_by_id(compilation_id)
```

number : its optional field (have default value = 0, may be **None** or not setting) 

size : its optional field (have default value = 10, may be **None** or not setting) 

compilation id you can get after create, or getting all

return type PageCompilationWithContents

example of json:
```json
{
  "id": "de2866fa-868d-40d2-8253-07812a559940",
  "title": "My first compilation",
  "description": "it's compilation created with help of library",
  "provider": "anything",
  "tags": [
    "first tag",
    "second tag",
    "third tag"
  ],
  "contents": [
    {
      "id": "3755dbfd82f34c19b72d45602073cb0c",
      "title": "Голубоглазый японец",
      "originalTitle": "Голубоглазый японец",
      "description": "Документальный фильм об удивительной истории жизни уроженца Нижнего Тагила Виктора Старухина. Пройдя через ад гражданской войны и выжив в китайском лагере беженцев, он оказался в предвоенной Японии, где стал национальным героем вопреки расовой дискриминации. Он одержал великие победы в составе первой сборной Японии над звездами американского бейсбола и стал кумиром молодежи.",
      "type": "film",
      "provider": "premier",
      "releaseDate": 2023,
      "ageRating": 18,
      "slug": "goluboglazyj-yaponets_tnt_premier_748aabdc",
      "ratingList": [],
      "genreList": [
        {
          "id": 1,
          "name": "Документальный"
        }
      ],
      "countryList": [
        {
          "id": 1,
          "name": "Россия"
        }
      ],
      "studioList": null,
      "horizontalPoster": null,
      "verticalPoster": {
        "url": "https://pic.uma.media/pic/video/11/90/11904bd3f403a9b174d9229c9764a3da.jpg",
        "resizeable": false
      },
      "episode": {
        "id": "9bcecd6da8704b03866d65a57aba62ab",
        "title": "Голубоглазый японец",
        "originalTitle": "Голубоглазый японец",
        "description": "Документальный фильм об удивительной истории жизни уроженца Нижнего Тагила Виктора Старухина. Пройдя через ад гражданской войны и выжив в китайском лагере беженцев, он оказался в предвоенной Японии, где стал национальным героем вопреки расовой дискриминации. Он одержал великие победы в составе первой сборной Японии над звездами американского бейсбола и стал кумиром молодежи.",
        "duration": 5001
      }
    }
  ],
  "number": 0,
  "size": 10,
  "totalPages": 1,
  "totalElements": 1,
  "hasNext": false,
  "hasPrevious": false
}
```

## Create compilation

**Initialization proxy class**

```python
contentApi = ClientCompilationControllerV2(DOMEN, AUTHORIZATION_TOKEN)

compilation_to_create = CompilationRequest(
    title="My first compilation",
    description="it's compilation created with help of library",
    provider="anything",
    tags=["first tag", "second tag", "third tag"],
    contentIds=["3755dbfd82f34c19b72d45602073cb0c"]
)
response = contentApi.create_compilation(compilation_to_create)
```

return type LightWeightCompilation

example of json:
```json
{
  "id": "de2866fa-868d-40d2-8253-07812a559940",
  "title": "My first compilation",
  "description": "it's compilation created with help of library",
  "provider": "anything",
  "tags": [
    "first tag",
    "second tag",
    "third tag"
  ],
  "contentIds": [
    "3755dbfd82f34c19b72d45602073cb0c"
  ]
}
```

## Update compilation

**Initialization proxy class**

```python
contentApi = ClientCompilationControllerV2(DOMEN, AUTHORIZATION_TOKEN)

compilation_to_create = CompilationRequest(
    title="updated_title"
)
response = contentApi.update_compilation_by_id(compilation_id, compilation_to_create)
```

you set in request fields, that you want to update. Others fields will not be updated

compilation id you can get after create, or getting all

return type LightWeightCompilation

example of json:
```json
{
  "id": "de2866fa-868d-40d2-8253-07812a559940",
  "title": "updated_title",
  "description": "it's compilation created with help of library",
  "provider": "anything",
  "tags": [
    "first tag",
    "second tag",
    "third tag"
  ],
  "contentIds": [
    "3755dbfd82f34c19b72d45602073cb0c"
  ]
}
```

## Delete compilation by id

**Initialization proxy class**

```python
contentApi = ClientCompilationControllerV2(DOMEN, AUTHORIZATION_TOKEN)

response = contentApi.delete_compilation_by_id(compilation_id)
```

Nothing return to you,but if failed -> method throw Exception




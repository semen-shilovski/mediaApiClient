# Content Controller

## Get content by filter

**Necessary imports**
```python
from mediaApiClient import *
```

**Initialization proxy class**

```python
contentApi = ClientContentControllerV2(DOMEN, AUTHORIZATION_TOKEN)
```

**RequestBody for filter content**

```json
{
  "type": "ALL",
  "intervalFilter": "ALL",
  "serviceId": "ALL",
  "dateFrom": "2023-08-01",
  "dateTo": "2023-08-29"
}
```

**In python code**

in next fields : type, intervalFilter, serviceId - use value of enum

dateFrom, dateTo - optional fields and reading by API only where intervalFilter = IntervalFilter.OTHER.value 
```python
filter_entity = ContentFilter(
    type=ContentType.ALL.value,
    intervalFilter=IntervalFilter.ALL.value,
    serviceId=Service.ALL.value,
    dateFrom=date(2023, 8, 1),
    dateTo=date(2023, 8, 29)
)
```
ContentType enums : _ALL, FILM, SERIAL, SHOW_

Service enums : _ALL, AMEDIATEKA, START, PREMIER_

IntervalFilter enums : _ALL, OTHER, TODAY, YESTERDAY, WEEK, MONTH_

**Get content with filter_entity**

```python
response = contentApi.get_content_by_filter(filter_instance, number, size)
```

number (have default value, may be **None**) : number of page (default 0)

size (have default value, may be **None**)  : size of page (default 10)

**Example of response**

```python
T = TypeVar('T')

class PageWithElements(BaseModel, Generic[T]):
    number: Optional[int] = Field(..., alias="number")
    size: Optional[int] = Field(..., alias="size")
    total_pages: Optional[int] = Field(..., alias="totalPages")
    total_elements: Optional[int] = Field(..., alias="totalElements")
    first: Optional[bool] = Field(..., alias="first")
    last: Optional[bool] = Field(..., alias="last")
    next: Optional[bool] = Field(..., alias="next")
    previous: Optional[bool] = Field(..., alias="previous")
    elements: Optional[List[T]] = Field(..., alias="elements")
```

```json
{
    "number": 0,
    "size": 1,
    "totalPages": 2350,
    "totalElements": 2350,
    "first": true,
    "last": false,
    "next": true,
    "previous": false,
    "elements": [
        {
            "id": "4f44b7f0671340e0895ed05eb8d97580",
            "title": "Телохранители",
            "originalTitle": "Телохранители",
            "description": "Комедийный сериал от режиссера «Жуков» и «Девушек с Макаровым» о трех боксерах из Челябинска, которые по воле случая становятся телохранителями московского адвоката. Ящер, Юрок и Туча перед вылетом на Чемпионат мира решают заработать на коммерческом турнире по боям без правил, из-за чего их исключают из сборной. Боксеры ужинают в столичном ресторане, где между ними и охраной влиятельного адвоката завязывается конфликт. Продемонстрировав свои профессиональные навыки, герои оказываются в полиции. Впечатлившийся их мастерством адвокат предлагает боксерам сделку: отправиться в тюрьму или стать его телохранителями.",
            "type": "serial",
            "provider": "premier",
            "releaseDate": 2023,
            "ageRating": 16,
            "slug": "telohraniteli_tnt_premier_3d495bda",
            "ratingList": [],
            "genreList": [
                {
                    "id": 1,
                    "name": "Комедия"
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
                "url": "https://pic.uma.media/pic/video/44/8b/448b91680dd8417e97f66e60fb9b684d.jpg",
                "resizeable": false
            },
            "seasons": [
                {
                    "id": "ee5179c205414130adc8a35411c265f4",
                    "title": "1 Сезон",
                    "originalTitle": "1 Сезон",
                    "description": null,
                    "number": 1,
                    "episodes": [
                        {
                            "id": "c33d6a3dc6df4d2da282f9e5334a154a",
                            "title": "1 серия",
                            "originalTitle": "1 серия",
                            "description": "Боксеры из Челябинска Юрок, Ящер и Туча перед вылетом на Чемпионат мира решают заработать на коммерческом турнире. Узнав о нарушении спортивного режима, главный тренер исключает их из сборной. За ужином в столичном ресторане парни невольно становятся участниками конфликта с охраной известного адвоката. Чтобы избежать тюремного срока, им приходится согласиться на предложение юриста.",
                            "number": 1,
                            "duration": 1520
                        },
                        {
                            "id": "76082d8ec89e4b3299edd0370caaf536",
                            "title": "2 серия",
                            "originalTitle": "2 серия",
                            "description": "Из тюрьмы выходит Циклоп — давний оппонент адвоката. Он зол и готов мстить. Адвокат решает откупится, но у Циклопа есть собственные условия. Благодаря своему обаянию Юрок находит общий язык с дочерью адвоката Вероникой.",
                            "number": 2,
                            "duration": 1522
                        }
                    ]
                }
            ]
        }
    ]
}
```

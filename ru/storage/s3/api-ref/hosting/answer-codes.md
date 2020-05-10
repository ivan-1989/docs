# Коды ответов статического сайта

Если бакет сконфигурирован для хостинга статических сайтов, то при обращении к нему пользователь может получить ответы с кодами, описанными в таблице ниже.

Код | Описание
-----------|---------
`200 OK` | Успешный ответ.
`302 Found`  | Если в {{ objstorage-name }} поступил запрос к ресурсу `http://{{ s3-web-host }}/bucket/x` без конечного `/`, то сначала {{ objstorage-name }} попытается найти объект `x` и, если объекта не существует, но существует `x/index.html`, который установлен как главная страница сайта, то пользователь получит ответ с кодом 302 и редиректом к ресурсу `http://{{ s3-web-host }}/bucket/x/`.
`304 Not Modified` | {{ objstorage-name }} использует заголовки запроса `If-Modified-Since`, `If-Unmodified-Since`, `If-Match`, `If-None-Match` чтобы определить изменился ли объект по отношению к ранее закэшированному на стороне клиента. Если объект не изменился, то пользователь получит ответ `304 Not Modified`.
`403 Forbidden` | Возвращается, если для бакета, к которому направлен запрос, не настроен публичный доступ.<br/><br/>[{#T}](../../../operations/buckets/bucket-availability.md).
`404 Not Found` | Возвращается, если ресурс, к которому направлен запрос не существует, или бакет, в котором находится запрошенный ресурс, не сконфигурирован для хостинга статических сайтов.<br/><br/>[{#T}](../../../operations/hosting/setup.md).
`500 Service Error` | Внутренняя ошибка {{ objstorage-name }}.
`503 Service Unavailable` | Слишком высокая нагрузка на сервис. Необходимо снизить частоту запросов.
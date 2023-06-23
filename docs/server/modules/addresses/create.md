# Создать адрес

## Эндпоинт

`POST` `/api/addresses`

## Тело запроса

| Поле       | Тип      | Описание             |
| ---------- | -------- | -------------------- |
| `city`     | `Guid`   | Идентификатор города |
| `street`   | `string` | Название улицы       |
| `building` | `string` | Номер здания         |

## Ответы

??? success "200"

    Адрес уже существует, новый не был создан. В теле запроса вернётся объект `Address`

    {%
        include-markdown "../../models/address.md"
    %}

??? success "201"

    Был успешно создан новый адрес. В теле возвращается объект `Address`

    {%
        include-markdown "../../models/address.md"
    %}

??? warning "400"

    Было передано некорректное тело запроса. Возвращается объект `ProblemDetails`

    {%
        include-markdown "../../models/problemDetails400.md"
    %}

??? warning "404"

    Был передан идентификатор несуществующего города. Возвращается объект `ProblemDetails`

    {%
        include-markdown "../../models/problemDetails404.md"
    %}

??? failure "500"

    Непредвиденная ошибка. Возвращается объект `ProblemDetails`

    {%
        include-markdown "../../models/problemDetails500.md"
    %}


## Примеры

`curl -XPOST -H "Content-type: application/json" -d '{"city": "8d7f0433-49a0-4b3d-a17c-58741ca44af5", street: "улица Мира", "building": "123"}' '/api/addresses'`
---
title: Referência Completa da API - Nenety Eventos

language_tabs:
  - php
  - json

toc_footers:
  - <a href='https://bizideias.com.br'>Documentação desenvolvida <br>por Biz Ideias</a>

includes:
  - errors

search: true
---

# Introdução

O objetivo desta documentação é orientar o desenvolvedor sobre como integrar com a API do sistema de venda de ingressos da Nenety Eventos, nas atividades de desenvolvimento e/ou manutenção de aplicativos e site.

O mecanismo de integração com a API é simples, de modo que apenas conhecimentos intermediários em linguagem de programação para Web, requisições HTTP/HTTPS e manipulação de arquivos JSON, são necessários.

Nesse manual você encontrará a referência sobre todas as operações disponíveis na API [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer). Estas operações devem ser executadas utilizando sua chave específica nos respectivos endpoints dos ambientes:

**Ambiente Produção:** https://api.nenety.com.br/1/

**Ambiente Homologação:** https://dev-api.nenety.com.br/1/

# Autenticação

Todos os *endpoints* da API utilizam o método de autenticação [OAuth2](https://oauth.net/2/). Todas as suas respostas são em [JSON](http://www.json.org/).

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Eventos

## Retornando eventos

Retorna um array contendo objetos de eventos, ordenados a partir da data de realização mais recente.

```php
<?php
    require("pagarme-php/Pagarme.php");

    Pagarme::setApiKey("SUA_API_KEY");

    $transaction = PagarMe_Transaction::all(3, 3)
```

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

### HTTP Request

`GET http://api.nenety.com.br/1/events`

### Query Params

Parameter | Default | Description
--------- | ------- | -----------
count | 10 | Retorna n objetos de eventos
page | 1 | Útil para implementação de uma paginação de resultados
id | | Filtro de id
event_date_after | | Retorna eventos realizados após a data especificada
event_date_before | | Retorna eventos realizados anterior a data especificada

#Destaques

## Retornando destaques

Retorna um array contendo objetos de banners destaque , ordenados a partir da ordem de apresentação.

```php
<?php
    require("pagarme-php/Pagarme.php");

    Pagarme::setApiKey("SUA_API_KEY");

    $transaction = PagarMe_Transaction::all(3, 3)
```

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

### HTTP Request

`GET http://api.nenety.com.br/1/featured_events`

### Query Params

Parameter | Default | Description
--------- | ------- | -----------
count | 10 | Retorna n objetos de eventos
page | 1 | Útil para implementação de uma paginação de resultados
id | | Filtro de id
event_date_after | | Retorna eventos realizados após a data especificada
event_date_before | | Retorna eventos realizados anterior a data especificada

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve


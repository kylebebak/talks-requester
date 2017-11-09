# Requester: HTTP Client for Humans
## 2017-11-08

Crear y consumir web APIs es fundamental para desarrollo web y mobile. Existen varios clientes HTTP que ayudan con esto. A grandes rasgos se dividen entre clientes GUI como Postman, Insomnia y Paw, y clientes CLI como cURL y HTTPie.

Requester es un cliente HTTP para Sublime Text. Combina elementos de managed UI propios de clientes GUI como colecciones, historial de peticiones, env vars y pruebas automatizadas, con la ligereza y rápidez de clientes CLI. Todo se trabaja con texto, lo cual hace trivial compartir y versionar colecciones de peticiones. Su sintaxis es poderoso y [muy bien documentado](http://docs.python-requests.org/en/master/).


## Preparación
- Instalar [Sublime Text 3](https://www.sublimetext.com/)
- Instalar [Package Control](https://packagecontrol.io/installation)
- Instalar Requester

Abre el command palette usando <kbd>shift+cmd+p</kbd>, busca __Package Control: Install Package__, luego busca __Requester__ (no ~~Http Requester~~) e instálalo.

Para estar seguro que se instaló bien, reinicia Sublime Text (ciérrala y ábrela de nuevo). Corre __Requester: Show Interactive Tutorial__.


### Resumen
- Features básicos y sintaxis
  + Request Body, Query Params, Custom Headers, Cookies
  + Variables de ambiente
  + Sintaxis (Requests), Parser, y convenience methods
- UI y UX
  + Colecciones de peticiones y navegación
  + Pestañas de respuesta
  + Historial de peticiones
- Pruebas
  + Test Runner
    + Sintaxis
    + JSON Schema
    + Integración con build process (generar scripts de pruebas)
  + Métricas (Benchmarking Tool)
- Portabilidad y Equipos
  + Exportar a cURL, HTTPie
  + Importar de cURL
    * Debugging peticiones AJAX/XHR mandados por tu browser
    * <https://www.nytimes.com/>, `commentData.json`, `commentCount`
- Autenticación: Twitter API
  + Extensiones a Requester, `requests-oauthlib`
  + <https://developer.twitter.com/en/docs/api-reference-index>
  + Explorando hyperlinked APIs (HATEOAS)
- Bonus: GraphQL support
  + Guardando peticiones a su requester file

~~~py
## test runner
###env
base_url = 'https://jsonplaceholder.typicode.com'
prop = 'status_code'
###env

# first request
get(base_url + '/posts')
assert {prop: 200, 'encoding': 'utf-8'}

# second request, with no assertion
get(base_url + '/profile')

# third request
get(base_url + '/comments')
assert {'status_code': 500}


get('https://jsonplaceholder.typicode.com/posts')
assert {
    'json_schema': {
        "type": "array",
        "items": {
            "type": "object",
            "properties": {
                "body": {"type": "string"},
                "id": {"type": "number"},
                "title": {"type": "string"},
                "userId": {"type": "string"}
            }
        }
    }
}



## twitter
get('https://api.twitter.com/1.1/statuses/user_timeline.json?screen_name=stackoverflow&count=1000', auth=auth)


## graphql
get('ipinfo.io/ip')

requests.get('https://api.graphloc.com/graphql', gql="""
{

}
""")
~~~


## Preguntas

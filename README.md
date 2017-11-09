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
  + Guardando peticiones a su requester file
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

~~~py
###env
from requests_oauthlib import OAuth1
auth = OAuth1(API_KEY, API_SECRET, ACCESS_TOKEN, ACCESS_TOKEN_SECRET)
###env

get('https://api.twitter.com/1.1/statuses/user_timeline.json?screen_name=stackoverflow&count=1000', auth=auth)
~~~

~~~py
requests.get('https://api.graphloc.com/graphql')
# curl ipinfo.io/ip
~~~


## Preguntas

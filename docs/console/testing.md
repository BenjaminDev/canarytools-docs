---
endpoints:
  ping:
    name: Ping
    url: /api/v1/ping
    method: GET
    description: A simple endpoint to test if the API is reachable.
    params:
      - name: auth_token
        required: true
        type: string
        description: A valid auth token
    response: A JSON message with a response indicator.
---
# Testing

These are a collection of endpoints that allow you to test connectivity with your Console.

<APIEndpoints :endpoints="$page.frontmatter.endpoints" :path="$page.regularPath"/>

## Ping

<APIDetails :endpoint="$page.frontmatter.endpoints.ping"/>

#### Example

:::: tabs :options="{ useUrlFragment: false }"

::: tab "cURL"

``` bash
DOMAIN=my_domain
AUTH_TOKEN=test_auth_token

curl "https://${DOMAIN}.canary.tools/api/v1/ping?auth_token=${AUTH_TOKEN}"
```

:::


::: tab "Python"

``` python
import requests

DOMAIN = 'my_domain'
AUTH_TOKEN = 'test_auth_token'

r = requests.get(
    'https://{DOMAIN}.canary.tools/api/v1/ping?auth_token={AUTH_TOKEN}'.format(
        DOMAIN=DOMAIN, AUTH_TOKEN=AUTH_TOKEN
    )
)
print(r.json())

```

:::

::::


::: api-response
```json
{
  "result": "success"
}
```
:::
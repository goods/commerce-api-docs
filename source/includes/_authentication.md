# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Bearer api_key"
```

> Make sure to replace `api_key` with your API key.

Goods uses API keys to allow access to the Commerce API. You can register a new API key for a shop by logging in to [Goods Platform](http://www.goods.co.uk), going to the shop, then `Settings` and then `Users`.

Goods expects the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer api_key`

<aside class="notice">
You must replace <code>api_key</code> with your API key.
</aside>

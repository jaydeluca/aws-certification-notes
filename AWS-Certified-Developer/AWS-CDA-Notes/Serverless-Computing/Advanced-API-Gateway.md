# Advanced API Gateway
## Import APIs
You can use the **API Gateway Import** API feature to import an API from an external definition file into API Gateway. Currently, the Import API feature supports **Swaggerv2.0** definition files.

With the Import API, you can either create a new API by submitting a POST request that includes a Swagger definition in the payload and endpoint configuration, or you can update an existing API by using a PUT request that contains a Swagger definition in the payload. You can update an API by overwriting it with a new definition, or merge a definition with an existing API. You specify the options using a mode query parameter in the request URL.









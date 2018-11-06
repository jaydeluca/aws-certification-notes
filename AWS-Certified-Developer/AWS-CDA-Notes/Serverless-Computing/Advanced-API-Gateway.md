# Advanced API Gateway
## Import APIs
You can use the **API Gateway Import** API feature to import an API from an external definition file into API Gateway. Currently, the Import API feature supports **Swaggerv2.0** definition files.

With the Import API, you can either create a new API by submitting a POST request that includes a Swagger definition in the payload and endpoint configuration, or you can update an existing API by using a PUT request that contains a Swagger definition in the payload. You can update an API by overwriting it with a new definition, or merge a definition with an existing API. You specify the options using a mode query parameter in the request URL.

## API Throttling
By default, API Gateway limits the steady-state request rate to **10,000 requests per second (rps)

The maximum concurrent requests is 5000 requests across all APIs within AWS account

If you go over 10,000 request per second or 5000 concurrent requests you will receive a 429 Too Many Request error response

Examples:
- If a caller submits 10,000 requests in a one second period evenly (for example, 10 requests every millisecond), API Gateway processes all requests without dropping any.
- If the caller sends 10,000 requests in the first millisecond, API Gateway serves 5,000 of those requests and throttles the rest in the one-second period.
- If the caller submits 5,000 requests through the remaining 999 millisecond and then evenly spreads another 5,000 requests through the remaining 999 milliseconds (for example, about 5 requests every millisecond), API Gateway processes all 10,000 requests in the one-second period without returning 429 Too Many Requests error responses.

## SOAP Webservice Passthrough
- You can configure API Gateway as a SOAP web services passthrough

## Advanced API Gateway - Exam Tips
- Import API's using Swagger v2.0 definition files
- API Gateway can be throttled
    - Default limits are 10,000 RPS or 5000 concurrently
- You can configure API Gateway as a SOAP Webservice passthrough



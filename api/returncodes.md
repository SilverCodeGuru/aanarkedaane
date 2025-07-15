# return codes

## DELETE
- **204** - success with no content in response
- **200** - useful when you want to send a message that deletion is successful.
- **202** - accepted for deletion. Asynchronous processing.
- **500** - Internal server error
- **404** - Not Found
- **401** - unauthorized
- **400** - bad request - missing headers?
- **403** - no access
- **415** - unsuppoprted media type application/xml
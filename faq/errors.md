# Errors

This section describes possible application errors in detail:

### Clipboard is empty

Most likely, you forgot to copy the data before attempting to import it into the application.

### The subscription URL is not valid

The provided address contains errors or invalid characters. Check the link for correctness by reviewing the clipboard contents.

### Configuration {config type} is not valid

The configuration you tried to add (vless, vmess, trojan, etc.) contains errors or invalid characters. Verify the link’s correctness by reviewing the clipboard contents.

### JSON (or array) configuration is not valid

The provided JSON contains errors or invalid characters. Check the JSON by reviewing the clipboard contents.

### Invalid deeplink URL

The specified DeepLink is not recognized by the application and has been ignored.

### Unknown content type

The provided data could not be recognized because it contains errors or invalid characters. Verify the correctness of the provided data.

### Wrong data for import routing profile

The routing profile contains errors or invalid parameters.

### **Timeout while adding a subscription**

When adding or updating a subscription, the application sends a request to the subscription server.\
If no response is received within 9 seconds, this error will be displayed.

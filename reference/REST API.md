# REST API

The Amply API is organized around REST. Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. JSON is returned by all API responses, including errors.

To make the API as explorable as possible, accounts have test mode and live mode API keys. There is no "switch" for changing between modes, just use the appropriate key to perform a live or test request. Requests made with test mode credentials will never incur fees or actually send email — they are for testing that your application can properly handle our responses and validate the parameters and structure of your requests.


The REST API has some advantages over SMTP:

- If your ISP or hosting provider blocks traffic on mail ports.
- If you do not control your hosting environment and cannot install/configure an SMTP library.

You can look at the full API documentation here.

Teamgo API
==========

This is official API for Teamgo. Teamgo is a visitor management system for enterprises.

Teamgo implements RESTful API. 

Security
--------

The Teamgo API is served over HTTPS to ensure data security and privacy.  HTTP is not supported.

Base URL
--------

Base URL are dependent on the end point. Please take note of the API URLs, as they maybe different.

Authentication
--------------

The Teamgo API uses HTTP Basic authentication. This is secure as all requests are via SSL.

Each Teamgo user will have their own API Key(s), this is used for authentication.  The API Key will have the same permissions as the user it is from.

Errors
------

Conventional HTTP response codes are used to indicate API errors.

General code rules apply:
* 2xx range indicate success.
* 4xx range indicate an error resulting from the provided information (eg. missing a required parameter)
* 5xx range indicate an error with our Teamgo servers


Data Responses
--------------

We only support JSON for serialization of data.

Dates and Times
---------------

All dates and times are expected to be in UTC.

API Resources
-----------------

* [Hosts](https://github.com/teamgovms/api/blob/hosts.md)
* [Webhook](https://github.com/teamgovms/api/blob/hosts.md)

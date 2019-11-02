Getting Started
===============


The Client API is organized around REST. Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP verbs, which are understood by off-the-shelf HTTP clients. We support cross-origin resource sharing, allowing you to interact securely with our API from a client-side web application (though you should never expose your secret credentials in any public website's client-side code). JSON is returned by all API responses, including errors, although our API libraries convert responses to appropriate language-specific objects.

**Example HTTP Request**

.. code-block:: console

  GET /client/v1 HTTP/1.1
  X-Client-ID: your-client-id
  X-Client-Secret: your-client-secret

**Response**

.. code-block:: JSON

    {
        "code": 200,
        "message": "Server is Reachable."
    }

**Response**

.. code-block:: JSON

    {
        "code": 401,
        "type": "authentication_error",
        "message": "Incorrect X-Client-ID or X-Client-Secret"
    }



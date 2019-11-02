Password Policy
===============

Endpoint: ``/client/v1/password-policy``

Method: ``GET``


**Example HTTP Request**

.. code-block:: console

  GET /client/v1/password-policy HTTP/1.1
  X-Client-ID: your-client-id
  X-Client-Secret: your-client-secret

**Response**

.. code-block:: JSON

    {
        "code": 200,
        "message": "Success",
        "policy": {
            "min_length": 6,
            "uppercase": true,
            "lowercase": true,
            "digit": true,
            "wildcard": true
        }
    }



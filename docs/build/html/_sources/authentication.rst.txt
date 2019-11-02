Authentication
=====================

All api endpoints are subject to client application authentication. Client application authentication to the API is performed via headers

.. code-block:: console

  X-Client-ID: your-client-id
  X-Client-Secret: your-client-secret

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without client authentication will also fail.

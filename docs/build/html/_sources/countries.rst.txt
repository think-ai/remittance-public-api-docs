Countries
=========

Get All Countries
-----------------

Get list of all countries in the system.

Endpoint: ``/client/v1/countries``

Method: ``GET``


**Example HTTP Request**

.. code-block:: console

  GET /client/v1/countries HTTP/1.1
  X-Client-ID: your-client-id
  X-Client-Secret: your-client-secret

**Response**

.. code-block:: JSON

    {
        "code": 200,
        "message": "Success",
        "countries": [
            {
                "known_name": "United Kingdom",
                "official_name": "United Kingdom of Great Britain and Northern Ireland",
                "endonym": "United Kingdom",
                "demonym": "British",
                "isd_code": 44,
                "iso_code_alpha2": "GB",
                "iso_code_alpha3": "GBR",
                "fips_code": "UK",
                "slug": "united-kingdom"
            },
            {
                "known_name": "United States",
                "official_name": "United States of America",
                "endonym": "United States",
                "demonym": "American",
                "isd_code": 1,
                "iso_code_alpha2": "US",
                "iso_code_alpha3": "USA",
                "fips_code": "US",
                "slug": "united-states"
            }
        ]
    }


Get Source Countries
--------------------

.. NOTE::
   Customers can register or send money from these countries only.

Endpoint: ``/client/v1/sources``

Method: ``GET``


**Example HTTP Request**

.. code-block:: console

  GET /client/v1/countries/sources HTTP/1.1
  X-Client-ID: your-client-id
  X-Client-Secret: your-client-secret

**Response**

.. code-block:: JSON

    {
        "code": 200,
        "message": "Success",
        "countries": [
            {
                "known_name": "Austria",
                "official_name": "Austria",
                "endonym": "Österreich",
                "demonym": "Austrian",
                "isd_code": 43,
                "iso_code_alpha2": "AT",
                "iso_code_alpha3": "AUT",
                "fips_code": "AU",
                "slug": "austria"
            },
            {
                "known_name": "Belgium",
                "official_name": "Belgium",
                "endonym": "België",
                "demonym": "Belgian",
                "isd_code": 32,
                "iso_code_alpha2": "BE",
                "iso_code_alpha3": "BEL",
                "fips_code": "BE",
                "slug": "belgium"
            },
            {
                "known_name": "United Kingdom",
                "official_name": "United Kingdom of Great Britain and Northern Ireland",
                "endonym": "United Kingdom",
                "demonym": "British",
                "isd_code": 44,
                "iso_code_alpha2": "GB",
                "iso_code_alpha3": "GBR",
                "fips_code": "UK",
                "slug": "united-kingdom"
            }
        ]
    }

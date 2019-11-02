Settings
========

Endpoint: ``/client/v1/settings``

Method: ``GET``


**Example HTTP Request**

.. code-block:: console

  GET /client/v1/settings HTTP/1.1
  X-Client-ID: your-client-id
  X-Client-Secret: your-client-secret

**Response**

.. code-block:: JSON

    {
        "code": 200,
        "message": "Success",
        "settings": {
            "trading_name": "ABC Money Transfer",
            "company_name": "ABC Limited",
            "tag_line": "Sending Money with Care",
            "license": "ABC Money Transfer is the trading name of ABC Limited. Registered company No. 07952651. We are registered as a Money Service Business and supervised by HM Revenue & Customs (HMRC) under Money Laundering Regulations (MLR) No.XXXXXXX.We are Authorised and Regulated by the Financial Conduct Authority (FCA) as a payment institution with reference number XXXXXX",
            "cs_number": "+44 10 1234 5678",
            "cs_email": "support@abcmoneytransfer.com",
            "hq_address": "Headquarter Street",
            "hq_city": "City",
            "hq_region": "",
            "hq_postcode": "Post Code",
            "hq_country": "United Kingdom",
            "locales": [
                {
                    "id": "en_GB",
                    "label": "English (UK)"
                }
            ],
            "timezones": [
                {
                    "id": "Africa/Abidjan",
                    "offset": "+00:00",
                    "nice": "Abidjan"
                },
                {
                    "id": "Africa/Accra",
                    "offset": "+00:00",
                    "nice": "Accra"
                },
                {
                    "id": "Africa/Addis_Ababa",
                    "offset": "+03:00",
                    "nice": "Addis Ababa"
                }
            ]
        }
    }



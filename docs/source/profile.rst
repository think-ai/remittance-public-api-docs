.. raw:: html

    <style> .red {color:red} .green{color:green}</style>

.. role:: red
.. role:: green

Save Profile
=====================

Create Profile
-----------------

The API returns :green:`200` status code on successful updates, :red:`400` for blank credentials.

Endpoint: ``/client/v1/customers/update/40136741....``

Method: ``POST``

**Additional Headers**

+--------------------------+-------------------------------------------------------------------------+
| Parameter                | Description                                                             |
+==========================+=========================================================================+
| X-Client-IP              | IP Address of the customer.                                             |
+--------------------------+-------------------------------------------------------------------------+
| X-Client-UA              | | User Agent of client application. For mobile apps this should be      |
|                          | | Application Version                                                   |
+--------------------------+-------------------------------------------------------------------------+
| X-Client-Fingerprint     | The unique identifier for device (Device ID).                           |
+--------------------------+-------------------------------------------------------------------------+
| X-User-Token             | The unique identifier change every time when user login.                |
+--------------------------+-------------------------------------------------------------------------+

**Parameters**

+--------------------------+-------------------------------------------------------------------------+
| Parameter                | Description                                                             |
+==========================+=========================================================================+
| honorific_id             | User Title.                                                             |
+--------------------------+-------------------------------------------------------------------------+
| gender                   | User Gender.                                                            |
+--------------------------+-------------------------------------------------------------------------+
| first_name               | User First Name.                                                        |
+--------------------------+-------------------------------------------------------------------------+
| last_name                | User Last Name.                                                         |
+--------------------------+-------------------------------------------------------------------------+
| date_of_birth            | User Birth Date.                                                        |
+--------------------------+-------------------------------------------------------------------------+
| nationality_id           | User Nationality.                                                       |
+--------------------------+-------------------------------------------------------------------------+
| is_pep                   | Is User politically exposed person(Y/N).                                |
+--------------------------+-------------------------------------------------------------------------+
| is_fm_pep                | Anyone of users family is politically exposed(Y/N).                        |
+--------------------------+-------------------------------------------------------------------------+
| is_linked_pep            | Anyone politically exposed person linked with user(Y/N).                |
+--------------------------+-------------------------------------------------------------------------+
| birth_city               | City of Birth.                                                          |
+--------------------------+-------------------------------------------------------------------------+
| birth_country_id         | Country of Birth.                                                       |
+--------------------------+-------------------------------------------------------------------------+

**Example HTTP Request**

.. code-block:: console

  POST client/v1/customers/update/40136741... HTTP/1.1
  X-Client-ID: your-client-id
  X-Client-Secret: your-client-secret
  X-Client-IP: user-ip-address
  X-Client-UA: user-agent
  X-Client-Fingerprint: unique-device-fingerprint
  X-User-Token: currently-loged_in-user-id
  Content-Type: application/x-www-form-urlencoded

  honorific_id:
  gender:M
  first_name:Abc
  last_name:Xyz
  date_of_birth:1990-01-01
  nationality_id:5a6f1d7a...
  is_pep:0
  is_fm_pep:0
  is_linked_pep:0
  birth_city:Kolkata
  birth_country_id:5a6f1d7a...

**Response**

.. code-block:: JSON

    {
    "code": 200,
    "message": "Success",
    "profile": {
        "id": "58d0818a...",
        "country_id": "a776c158...",
        "cin": 69..,
        "full_name": "John Doe",
        "first_name": "John",
        "last_name": "Doe",
        "email": "test@gmail.com",
        "email_unmasked": "test@gmail.com",
        "is_verified_email": false,
        "two_factor_enabled": false,
        "password_modified": null,
        "referral_code": "VXH...",
        "is_profile_completed": false,
        "timezone": "UTC",
        "timezone_nice": "GMT +00:00",
        "locale": "en_GB",
        "created": "2021-01-09T10:40:27+00:00",
        "modified": "2021-01-11T07:00:03+00:00",
        "country": {
            "id": "a776c158..."
        }
    }

**Example Failed Response**

.. code-block:: JSON

    {
    "code": 400,
    "type": "invalid_request_error",
    "message": "Invalid request",
    "errors": {
            "param": "first_name",
            "code": "_empty",
            "message": "This field cannot be left empty"
           }
    }

Change Password
-------------------

The API returns :green:`200` status code on successful updates, :red:`401` for invalid user_token, :red:`400` for Incorrect current password, New password and confirm password do not match.

Endpoint: ``/client/v1/change-password``

Method: ``POST``

**Additional Headers**

+--------------------------+-------------------------------------------------------------------------+
| Parameter                | Description                                                             |
+==========================+=========================================================================+
| X-Client-IP              | IP Address of the customer.                                             |
+--------------------------+-------------------------------------------------------------------------+
| X-Client-UA              | | User Agent of client application. For mobile apps this should be      |
|                          | | Application Version                                                   |
+--------------------------+-------------------------------------------------------------------------+
| X-Client-Fingerprint     | The unique identifier for device (Device ID).                           |
+--------------------------+-------------------------------------------------------------------------+
| X-User-Token             | The unique identifier change every time when user login.                |
+--------------------------+-------------------------------------------------------------------------+

**Parameters**

+--------------------------+-------------------------------------------------------------------------+
| Parameter                | Description                                                             |
+==========================+=========================================================================+
| current_password         | Password currently have in your account.                                |
+--------------------------+-------------------------------------------------------------------------+
| password                 | New Password you want to set.                                           |
+--------------------------+-------------------------------------------------------------------------+
| confirm_password         | Password conformation                                                   |
+--------------------------+-------------------------------------------------------------------------+

**Example HTTP Request**

.. code-block:: console

  POST /client/v1/change-password HTTP/1.1
  X-Client-ID: your-client-id
  X-Client-Secret: your-client-secret
  X-Client-IP: user-ip-address
  X-Client-UA: user-agent
  X-Client-Fingerprint: unique-device-fingerprint
  X-User-Token: currently-loged_in-user-id
  Content-Type: application/x-www-form-urlencoded

  current_password:654321
  password:123456
  confirm_password:123456

**Response**

.. code-block:: JSON

    {
    "code": 200,
    "message": "Success"
    }


**Example Failed Response**

.. code-block:: JSON

    {
    "code": 401,
    "type": "authentication_error",
    "message": "Authentication token has been expired"
   }

    {
    "code": 400,
    "type": "invalid_request_error",
    "message": "Invalid request",
    "errors": [
        {
            "param": "current_password",
            "code": "_invalidCurrentPassword",
            "message": "Incorrect current password."
            }
        ]
    }

    {
    "code": 400,
    "type": "invalid_request_error",
    "message": "Invalid request",
    "errors": [
        {
            "param": "confirm_password",
            "code": "equalToField",
            "message": "New password and confirm password do not match."
           }
        ]
    }

Update Preferences
--------------------

The API returns :green:`200` status code on successful updates.

Endpoint: ``/client/v1/update-preferences``

Method: ``POST``

**Additional Headers**

+--------------------------+-------------------------------------------------------------------------+
| Parameter                | Description                                                             |
+==========================+=========================================================================+
| X-Client-IP              | IP Address of the customer.                                             |
+--------------------------+-------------------------------------------------------------------------+
| X-Client-UA              | | User Agent of client application. For mobile apps this should be      |
|                          | | Application Version                                                   |
+--------------------------+-------------------------------------------------------------------------+
| X-Client-Fingerprint     | The unique identifier for device (Device ID).                           |
+--------------------------+-------------------------------------------------------------------------+
| X-User-Token             | The unique identifier change every time when user login.                |
+--------------------------+-------------------------------------------------------------------------+

**Parameters**

+--------------------------+-------------------------------------------------------------------------+
| Parameter                | Description                                                             |
+==========================+=========================================================================+
| timezone                 | UTC                                                                     |
+--------------------------+-------------------------------------------------------------------------+
| locale                   | en_GB                                                                   |
+--------------------------+-------------------------------------------------------------------------+

**Example HTTP Request**

.. code-block:: console

  POST client/v1/update-preferences HTTP/1.1
  X-Client-ID: your-client-id
  X-Client-Secret: your-client-secret
  X-Client-IP: user-ip-address
  X-Client-UA: user-agent
  X-Client-Fingerprint: unique-device-fingerprint
  X-User-Token: currently-loged_in-user-id
  Content-Type: application/x-www-form-urlencoded

  timezone:UTC
  locale:en_GB

**Response**

.. code-block:: JSON

    {
    "code": 200,
    "message": "Success"
    }




Update Email
-----------------

The API returns :green:`200` status code on successful updates, :red:`400` for Incorrect Email.

Endpoint: ``/client/v1/update-email``

Method: ``POST``

**Additional Headers**

+--------------------------+-------------------------------------------------------------------------+
| Parameter                | Description                                                             |
+==========================+=========================================================================+
| X-Client-IP              | IP Address of the customer.                                             |
+--------------------------+-------------------------------------------------------------------------+
| X-Client-UA              | | User Agent of client application. For mobile apps this should be      |
|                          | | Application Version                                                   |
+--------------------------+-------------------------------------------------------------------------+
| X-Client-Fingerprint     | The unique identifier for device (Device ID).                           |
+--------------------------+-------------------------------------------------------------------------+
| X-User-Token             | The unique identifier change every time when user login.                |
+--------------------------+-------------------------------------------------------------------------+

**Parameters**

+--------------------------+-------------------------------------------------------------------------+
| Parameter                | Description                                                             |
+==========================+=========================================================================+
| email                    | Email you want to update.                                               |
+--------------------------+-------------------------------------------------------------------------+
| confirmation_url         | Confirmation Url                                                        |
+--------------------------+-------------------------------------------------------------------------+

**Example HTTP Request**

.. code-block:: console

  POST /client/v1/update-email HTTP/1.1
  X-Client-ID: your-client-id
  X-Client-Secret: your-client-secret
  X-Client-IP: user-ip-address
  X-Client-UA: user-agent
  X-Client-Fingerprint: unique-device-fingerprint
  X-User-Token: currently-loged_in-user-id
  Content-Type: application/x-www-form-urlencoded

  email:test1@gmail.com
  confirmation_url:confirmation_url

**Response**

.. code-block:: JSON

    {
    "code": 200,
    "message": "Success"
    }


**Example Failed Response**

.. code-block:: JSON

    {
    "code": 400,
    "type": "invalid_request_error",
    "message": "Invalid request",
    "errors": [
        {
            "param": "email",
            "code": "email",
            "message": "Email address is not a valid email."
         }
        ]
    }
:original_name: gaussdb_04_0009.html

.. _gaussdb_04_0009:

Querying a Parameter Template
=============================

Function
--------

This API is used to obtain a parameter template list, including all databases' default and custom parameter templates.

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` this API before using it.
-  Before calling this API, obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   GET https://{*Endpoint*}/mysql/v3/{*project_id*}/configurations

-  Example

   GET https://{*Endpoint*}/mysql/v3/0483b6b16e954cb88930a360d2c4e663/configurations

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                |
      +=======================+=======================+============================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                        |
      |                       |                       |                                                                            |
      |                       |                       | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+

Request
-------

None.

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                            |
      +=======================+=======================+========================================================================+
      | configurations        | Array of objects      | Parameter template list.                                               |
      |                       |                       |                                                                        |
      |                       |                       | For details, see :ref:`Table 3 <gaussdb_04_0009__table1324110018258>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------+
      | total_count           | Integer               | Total number of parameter templates.                                   |
      +-----------------------+-----------------------+------------------------------------------------------------------------+

   .. _gaussdb_04_0009__table1324110018258:

   .. table:: **Table 3** configurations field data structure description

      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Name                   | Type                  | Description                                                                                                        |
      +========================+=======================+====================================================================================================================+
      | id                     | String                | Parameter template ID.                                                                                             |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | name                   | String                | Parameter template name.                                                                                           |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | description            | String                | Parameter template description.                                                                                    |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_version_name | String                | DB version name.                                                                                                   |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_name         | String                | DB name.                                                                                                           |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | created                | String                | Creation time in the "yyyy-MM-ddTHH:mm:ssZ" format.                                                                |
      |                        |                       |                                                                                                                    |
      |                        |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | updated                | String                | Update time in the "yyyy-MM-ddTHH:mm:ssZ" format.                                                                  |
      |                        |                       |                                                                                                                    |
      |                        |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | user_defined           | Boolean               | Whether the parameter template is a custom template.                                                               |
      |                        |                       |                                                                                                                    |
      |                        |                       | -  **false**: The parameter template is a default template.                                                        |
      |                        |                       | -  **true**: The parameter template is a custom template.                                                          |
      +------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "configurations":[
              {
                  "id":"1ad028f5f6b8482483948860feb33339pr07",
                  "name":"DBS_GaussDB_ParameterTemple_Apply_001",
                  "description":"GaussDB-Test",
                  "datastore_version_name":"8.0",
                  "datastore_name":"gaussdb-mysql",
                  "created":"2020-04-08 07:12:17",
                  "updated":"2020-04-08 07:12:17",
                  "user_defined":true,
              }
      ]
      }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.

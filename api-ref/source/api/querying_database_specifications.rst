:original_name: gaussdb_04_0002.html

.. _gaussdb_04_0002:

Querying Database Specifications
================================

Function
--------

This API is used to query the database specifications of a specified DB engine version.

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` this API before using it.
-  Before calling this API, obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   GET https://{*Endpoint*}/mysql/v3/{project_id}/flavors/{database}?version_name={version_name}&spec_code={spec_code}

-  Example

   GET https://{*Endpoint*}/mysql/v3/0483b6b16e954cb88930a360d2c4e663/flavors/gaussdb-mysql?version_name=8.0&spec_code=gaussdb.mysql.xlarge.x86.4

-  Parameter description

   .. table:: **Table 1** Parameter description

      +------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | Name                   | Mandatory       | Type            | Description                                                                                                           |
      +========================+=================+=================+=======================================================================================================================+
      | project_id             | Yes             | String          | Project ID of a tenant in a region.                                                                                   |
      |                        |                 |                 |                                                                                                                       |
      |                        |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`.                                            |
      +------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | database               | Yes             | String          | DB engine. Its value can be any of the following and is case-insensitive:                                             |
      |                        |                 |                 |                                                                                                                       |
      |                        |                 |                 | -  gaussdb-mysql                                                                                                      |
      +------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | version_name           | No              | String          | DB version number. To obtain this value, see :ref:`Querying Version Information About a DB Engine <gaussdb_04_0001>`. |
      |                        |                 |                 |                                                                                                                       |
      |                        |                 |                 | Currently, only MySQL 8.0 is supported.                                                                               |
      +------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | availability_zone_mode | Yes             | String          | AZ type of the specification. The value can be **single** or **multi**.                                               |
      +------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | spec_code              | No              | String          | Specification code.                                                                                                   |
      +------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+

Request
-------

None.

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                       |
      +=======================+=======================+===================================================================+
      | flavors               | Array of objects      | DB instance specification list.                                   |
      |                       |                       |                                                                   |
      |                       |                       | For details, see :ref:`Table 3 <gaussdb_04_0002__table66531170>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------+

   .. _gaussdb_04_0002__table66531170:

   .. table:: **Table 3** flavors field data structure description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                              |
      +=======================+=======================+==========================================================================================+
      | vcpus                 | String                | Number of vCPUs. For example, the value **1** indicates 1 vCPU.                          |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
      | ram                   | Integer               | Memory size in gigabyte (GB).                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
      | type                  | String                | Specification type. The value can be **arm** or **x86**.                                 |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
      | id                    | String                | Specification ID. The value must be unique.                                              |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
      | spec_code             | String                | Resource specification code. For example: gaussdb.mysql.xlarge.x86.4.                    |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
      | version_name          | String                | DB version number.                                                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
      | instance_mode         | String                | DB instance type. Currently, only the cluster type is supported.                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
      | az_status             | Map<String, String>   | Status of the AZ where the specification belongs. Its value can be any of the following: |
      |                       |                       |                                                                                          |
      |                       |                       | -  **normal**: on sale.                                                                  |
      |                       |                       | -  **unsupported**: not supported.                                                       |
      |                       |                       | -  **sellout**: sold out.                                                                |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "flavors":[
              {
                  "vcpus":"1",
                  "ram":"4",
                  "type":"x86"
      "id":"3169caaf-6c2f-41d5-aadd-c8fc3d83597e",
                  "spec_code":"gaussdb.xlarge.x86.4",
                  "instance_mode":"Cluster",
                  "version_name": "8.0",
                  "az_status":{
                      "az1":"normal",
                      "az2":"normal"
                  }
              },
              {
                  "vcpus":"2",
                  "ram":"4",
                  "type":"arm"
                  "id":"cefb8fab-c9f7-482f-a97c-e8a0c8abe35b",
                  "spec_code":"gaussdb.mysql.xlarge.x86.2",
                  "instance_mode":"Cluster",
      "version_name": "8.0",
                  "az_status":{
                      "az1":"normal",
                      "az2":"normal"
                  }
              }
          ]
      }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.

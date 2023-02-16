:original_name: gaussdb_04_0001.html

.. _gaussdb_04_0001:

Querying Version Information About a DB Engine
==============================================

Function
--------

This API is used to query the DB version information of a specified DB engine.

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` this API before using it.
-  Before calling this API, obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   GET https://{*Endpoint*}/mysql/v3/{project_id}/datastores/{database_name}

-  Example

   GET https://{*Endpoint*}/mysql/v3/619d3e78f61b4be68bc5aa0b59edcf7b/datastores/gaussdb-mysql

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                       |
      +=======================+=======================+===================================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                               |
      |                       |                       |                                                                                   |
      |                       |                       | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`.        |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------+
      | database_name         | Yes                   | DB engine. The following DB engine is supported (case-insensitive): gaussdb-mysql |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------+

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
      | datastores            | Array of objects      | DB version list.                                                  |
      |                       |                       |                                                                   |
      |                       |                       | For details, see :ref:`Table 3 <gaussdb_04_0001__table66531170>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------+

   .. _gaussdb_04_0001__table66531170:

   .. table:: **Table 3** datastores field data structure description

      +------+--------+-------------------------------------------------------------------------------+
      | Name | Type   | Description                                                                   |
      +======+========+===============================================================================+
      | id   | String | DB version ID. Its value is unique.                                           |
      +------+--------+-------------------------------------------------------------------------------+
      | name | String | DB version number. Only the major version number with two digits is returned. |
      +------+--------+-------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
               "datastores": [{
                         "id": "87620726-6802-46c0-9028-a8785e1f1921",
                         "name": "8.0"
               }]
      }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.

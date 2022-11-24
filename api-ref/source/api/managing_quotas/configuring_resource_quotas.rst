:original_name: gaussdb_04_0012.html

.. _gaussdb_04_0012:

Configuring Resource Quotas
===========================

Function
--------

This API is used to set resource quotas for a specified enterprise project.

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` this API before using it.
-  Before calling this API, obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   POST https://{*Endpoint*}/mysql/v3/{project_id}/quotas

-  Example

   POST https://{*Endpoint*}/mysql/v3/0483b6b16e954cb88930a360d2c4e663/quotas

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                |
      +=======================+=======================+============================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                        |
      |                       |                       |                                                                            |
      |                       |                       | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | quota_list            | Yes                   | Quota details. A maximum of 10 quota records can be configured at a time.  |
      |                       |                       |                                                                            |
      |                       |                       | For details, see :ref:`Table 2 <gaussdb_04_0012__table1453814912427>`.     |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. _gaussdb_04_0012__table1453814912427:

   .. table:: **Table 2** quota_list field data structure description

      +-----------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type    | Description                                                                                                                                                                                      |
      +=======================+=========+==================================================================================================================================================================================================+
      | enterprise_project_id | String  | Enterprise project ID.                                                                                                                                                                           |
      +-----------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_quota        | Integer | DB instance quantity quota. The value ranges from **0** to **1000**. (If there are already DB instances created, this parameter value must be greater than the number of existing DB instances.) |
      +-----------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vcpus_quota           | Integer | vCPUs quota. The value ranges from **0** to **3600000**. (If there are already DB instances created, this parameter value must be greater than the number of used vCPUs.)                        |
      +-----------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ram_quota             | Integer | Memory quota in GB. The value ranges from **0** to **19200000**. (If there are already DB instances created, this parameter value must be greater than the used memory size.)                    |
      +-----------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
        "quota_list": [
          {
            "enterprise_project_id": "0",
            "instance_quota": 1,
            "vcpus_quota": 4,
            "ram_quota": 8
          }
        ]
      }

Response
--------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                       |
      +=======================+=======================+===================================================================+
      | quota_list            | Array of objects      | Configured quota information.                                     |
      |                       |                       |                                                                   |
      |                       |                       | For details, see :ref:`Table 4 <gaussdb_04_0012__table66531170>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------+

   .. _gaussdb_04_0012__table66531170:

   .. table:: **Table 4** quota_list data structure description

      ===================== ======= ==================================
      Name                  Type    Description
      ===================== ======= ==================================
      enterprise_project_id String  Enterprise project ID.
      instance_quota        Integer Quota of the DB instance quantity.
      vcpus_quota           Integer Quota of vCPUs.
      ram_quota             Integer Memory quota in GB.
      ===================== ======= ==================================

-  Example response

   .. code-block:: text

      {
        "quota_list": [
          {
            "enterprise_project_id": "0",
            "instance_quota": 1,
            "vcpus_quota": 4,
            "ram_quota": 8
          }
        ]
      }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.

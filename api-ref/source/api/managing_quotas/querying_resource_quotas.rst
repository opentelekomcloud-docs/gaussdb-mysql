:original_name: gaussdb_04_0011.html

.. _gaussdb_04_0011:

Querying Resource Quotas
========================

Function
--------

This API is used to obtain the resource quota of a specified enterprise project.

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` this API before using it.
-  Before calling this API, obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   GET https://{*Endpoint*}/mysql/v3/{project_id}/quotas

-  Example

   GET https://{*Endpoint*}/mysql/v3/619d3e78f61b4be68bc5aa0b59edcf7b/quotas

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                                                                             |
      +=======================+=======================+=========================================================================================================================================================================================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                                                         |
      |                       |                       | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`.                                                                                                                                                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset                | No                    | Index position. If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit                 | No                    | Number of records to be queried. The default value is **10**. The value cannot be a negative number. The minimum value is **1** and the maximum value is **100**.                                                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                       |
      +=======================+=======================+===================================================================+
      | quota_list            | Array of objects      | Quota information list.                                           |
      |                       |                       |                                                                   |
      |                       |                       | For details, see :ref:`Table 3 <gaussdb_04_0011__table66531170>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------+
      | total_count           | Integer               | Number of quota records.                                          |
      +-----------------------+-----------------------+-------------------------------------------------------------------+

   .. _gaussdb_04_0011__table66531170:

   .. table:: **Table 3** quota_list field data structure description

      =========================== ======= ==================================
      Name                        Type    Description
      =========================== ======= ==================================
      enterprise_project_id       String  Enterprise project ID.
      instance_quota              Integer Quota of the DB instance quantity.
      vcpus_quota                 Integer Quota of vCPUs.
      ram_quota                   Integer Memory quota in GB.
      availability_instance_quota Integer Remaining quota of DB instances.
      availability_vcpus_quota    Integer Remaining quota of vCPU.
      availability_ram_quota      Integer Remaining memory quota.
      =========================== ======= ==================================

-  Example response

   .. code-block:: text

      "quota_list": [
        {
          "enterprise_project_id": "0",
          "instance_quota": 20,
          "vcpus_quota": 20,
          "ram_quota": 40,
          "availability_instance_quota": 1,
          "availability_vcpus_quota ": 4,
          "availability_ram_quota": 8
        },
        {
          "enterprise_project_id": "d72ebb42-9110-464c-a8e2-f9b9f349f80f",
          "instance_quota": 0,
          "vcpus_quota": 0,
          "ram_quota": 0,
          "availability_instance_quota ": 1,
          "availability_vcpus_quota ": 4,
          "availability_ram_quota ": 8
        }
      ],
      "total_count": 2
      }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.

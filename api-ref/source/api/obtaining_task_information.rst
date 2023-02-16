:original_name: gaussdb_04_0014.html

.. _gaussdb_04_0014:

Obtaining Task Information
==========================

Function
--------

This API is used to obtain task information from the task center.

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` this API before using it.
-  Before calling this API, obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   GET https://{*Endpoint*}/mysql/v3/{project_id}/jobs?id={id}

-  Example

   GET https://{*Endpoint*}/mysql/v3/0483b6b16e954cb88930a360d2c4e663/jobs?id=a9767ede-fe0f-4888-9003-e843a4c90514

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                |
      +=======================+=======================+============================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                        |
      |                       |                       |                                                                            |
      |                       |                       | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | id                    | Yes                   | Task ID.                                                                   |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+

Request
-------

None.

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +------+--------+-------------------------------------------------------------------------------------------+
      | Name | Type   | Description                                                                               |
      +======+========+===========================================================================================+
      | job  | Object | Task information. For details, see :ref:`Table 3 <gaussdb_04_0014__table54571314103317>`. |
      +------+--------+-------------------------------------------------------------------------------------------+

   .. _gaussdb_04_0014__table54571314103317:

   .. table:: **Table 3** job field data structure description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                        |
      +=======================+=======================+====================================================================================================================+
      | id                    | String                | Task ID.                                                                                                           |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Task name.                                                                                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Task execution status.                                                                                             |
      |                       |                       |                                                                                                                    |
      |                       |                       | Valid value:                                                                                                       |
      |                       |                       |                                                                                                                    |
      |                       |                       | -  **Running**: The task is being executed.                                                                        |
      |                       |                       | -  **Completed**: The task is successfully executed.                                                               |
      |                       |                       | -  **Failed**: The task fails to be executed.                                                                      |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | created               | String                | Creation time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | process               | String                | Task execution progress.                                                                                           |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | instance              | Object                | DB instance on which the task is executed.                                                                         |
      |                       |                       |                                                                                                                    |
      |                       |                       | For details, see :ref:`Table 4 <gaussdb_04_0014__table4062895917262>`.                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | entities              | Object                | Displayed information varies depending on tasks.                                                                   |
      |                       |                       |                                                                                                                    |
      |                       |                       | For details, see :ref:`Table 5 <gaussdb_04_0014__table1014617554138>`.                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | fail_reason           | String                | Task failure information.                                                                                          |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

   .. _gaussdb_04_0014__table4062895917262:

   .. table:: **Table 4** instances field data structure description

      ==== ====== =================
      Name Type   Description
      ==== ====== =================
      id   String DB instance ID.
      name String DB instance name.
      ==== ====== =================

   .. _gaussdb_04_0014__table1014617554138:

   .. table:: **Table 5** entities field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                           |
      +=======================+=======================+=======================================================================+
      | instance              | Object                | DB instance queried in the task.                                      |
      |                       |                       |                                                                       |
      |                       |                       | For details, see :ref:`Table 6 <gaussdb_04_0014__table975183423611>`. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | resource_ids          | List<String>          | Resource ID involved in a task.                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+

   .. _gaussdb_04_0014__table975183423611:

   .. table:: **Table 6** entities.instance field data structure description

      +-----------+--------+---------------------------------------------------------------------------------------+
      | Name      | Type   | Description                                                                           |
      +===========+========+=======================================================================================+
      | endpoint  | String | DB instance connection address.                                                       |
      +-----------+--------+---------------------------------------------------------------------------------------+
      | type      | String | DB instance type.                                                                     |
      +-----------+--------+---------------------------------------------------------------------------------------+
      | datastore | Object | DB information. For details, see :ref:`Table 7 <gaussdb_04_0014__table173094268581>`. |
      +-----------+--------+---------------------------------------------------------------------------------------+

   .. _gaussdb_04_0014__table173094268581:

   .. table:: **Table 7** datastore field data structure description

      ======= ====== ===========
      Name    Type   Description
      ======= ====== ===========
      type    String DB engine.
      version String DB version.
      ======= ====== ===========

   .. table:: **Table 8** entities field data structure description (binding or unbinding an EIP)

      ========= ====== =====================
      Name      Type   Description
      ========= ====== =====================
      public_ip String EIP used in the task.
      ========= ====== =====================

   .. note::

      In the response example, some tasks in the task center are used as examples.

-  Example normal response

   .. code-block:: text

      {
        "job": {
          "id": "31b8ae23-c687-4d80-b7b4-42a66c9bb886",
          "name": " RestartGaussDBInstance",
          "status": "Completed",
          "created": "2018-08-06T10:41:14+0000",
          "ended": "2018-08-06T16:41:14+0000",
          "process": "",
          "instance": {
            "id": "a48e43ff268f4c0e879652d65e63d0fbin01",
            "name": "DO-NOT-TOUCH-mgr2-gaussdb"
          },
          "entities": {}
          }
        }
      }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.

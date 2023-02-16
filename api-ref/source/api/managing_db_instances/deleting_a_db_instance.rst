:original_name: gaussdb_04_0007.html

.. _gaussdb_04_0007:

Deleting a DB Instance
======================

Function
--------

This API is used to delete a DB instance.

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` this API before using it.
-  Before calling this API, obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   DELETE https://{*Endpoint*}/mysql/v3/{project_id}/instances/{instance_id}

-  Example

   DELETE https://{*Endpoint*}/mysql/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                |
      +=======================+=======================+============================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                        |
      |                       |                       |                                                                            |
      |                       |                       | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+
      | instance_id           | Yes                   | DB instance ID, which is compliant with the UUID format.                   |
      +-----------------------+-----------------------+----------------------------------------------------------------------------+

Request
-------

None.

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      ====== ====== ====================================
      Name   Type   Description
      ====== ====== ====================================
      job_id String ID of the DB instance deletion task.
      ====== ====== ====================================

-  Example normal response

   .. code-block:: text

      {
          "job_id": "dff1d289-4d03-4942-8b9f-463ea07c000d"
      }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.

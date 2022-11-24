:original_name: gaussdb_04_0006.html

.. _gaussdb_04_0006:

Querying Details of a DB Instance
=================================

Function
--------

This API is used to query the details of a specified DB instance.

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` this API before using it.
-  Before calling this API, obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   GET https://{*Endpoint*}/mysql/v3/{project_id}/instances/{instance_id}

-  Example

   GET https://{*Endpoint*}/mysql/v3/97b026aa9cc4417888c14c84a1ad9860/instances/436aaafb689c4250a9a5bb33cb271e8cin07

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
      | Name            | Type            | Mandatory       | Description                                                                |
      +=================+=================+=================+============================================================================+
      | project_id      | String          | Yes             | Project ID of a tenant in a region.                                        |
      |                 |                 |                 |                                                                            |
      |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+
      | instance_id     | String          | Yes             | DB instance ID.                                                            |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------+

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
      | instance              | Object                | DB instance information.                                               |
      |                       |                       |                                                                        |
      |                       |                       | For details, see :ref:`Table 3 <gaussdb_04_0006__table2058713718267>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------+

   .. _gaussdb_04_0006__table2058713718267:

   .. table:: **Table 3** instance field data structure description

      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | Name                  | Type             | Description                                                                                 |
      +=======================+==================+=============================================================================================+
      | id                    | String           | DB instance ID.                                                                             |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | name                  | String           | DB instance name.                                                                           |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | project_id            | String           | Project ID of a tenant in a region.                                                         |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | status                | String           | DB instance status.                                                                         |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | enterprise_project_id | String           | Enterprise project ID.                                                                      |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | type                  | String           | DB instance type. Currently, only the cluster type is supported.                            |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | node_count            | Integer          | Number of nodes.                                                                            |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | datastore             | Object           | Database information. For details, see :ref:`Table 4 <gaussdb_04_0006__table187591675262>`. |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | backup_used_space     | Integer          | Used backup space, in GB.                                                                   |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | created               | String           | DB instance creation time.                                                                  |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | updated               | String           | DB instance update time.                                                                    |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | public_ips            | String           | Public IP address of the DB instance.                                                       |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | private_write_ips     | Array of List    | Private IP address for write.                                                               |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | db_user_name          | String           | Default username.                                                                           |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | port                  | String           | Database port number.                                                                       |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | vpc_id                | String           | VPC ID.                                                                                     |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | subnet_id             | String           | Subnet ID.                                                                                  |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | security_group_id     | String           | Security group ID.                                                                          |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | volume                | Object           | Disk information. For details, see :ref:`Table 8 <gaussdb_04_0006__table14771167122611>`.   |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | backup_strategy       | Object           | Backup policy. For details, see :ref:`Table 6 <gaussdb_04_0006__table37991653839>`.         |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | nodes                 | Arrays of object | Node information. For details, see :ref:`Table 7 <gaussdb_04_0006__table5182635134511>`.    |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | time_zone             | String           | Time zone.                                                                                  |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | az_mode               | String           | AZ.                                                                                         |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+
      | master_az_code        | String           | Primary AZ.                                                                                 |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------+

   .. _gaussdb_04_0006__table187591675262:

   .. table:: **Table 4** datastore field data structure description

      ======= ====== ===========
      Name    Type   Description
      ======= ====== ===========
      type    String DB engine.
      version String DB version.
      ======= ====== ===========

   .. table:: **Table 5** configurations field data structure description

      ==== ====== ========================
      Name Type   Description
      ==== ====== ========================
      id   String Parameter template ID.
      name String Parameter template name.
      ==== ====== ========================

   .. _gaussdb_04_0006__table37991653839:

   .. table:: **Table 6** backup_strategy field data structure description

      +------------+---------+----------------------------------------------------------------------------------------+
      | Name       | Type    | Description                                                                            |
      +============+=========+========================================================================================+
      | start_time | String  | Backup time window. Automated backups will be triggered during the backup time window. |
      +------------+---------+----------------------------------------------------------------------------------------+
      | keep_days  | Integer | Backup retention days.                                                                 |
      +------------+---------+----------------------------------------------------------------------------------------+

   .. _gaussdb_04_0006__table5182635134511:

   .. table:: **Table 7** nodes field data structure description

      +------------------+-----------------+-------------------------------------------------------------------------+
      | Name             | Type            | Description                                                             |
      +==================+=================+=========================================================================+
      | id               | String          | Node ID.                                                                |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | name             | Array of object | Node name.                                                              |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | type             | String          | Node type, which can be **master** or **slave**.                        |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | status           | String          | Node status.                                                            |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | port             | Integer         | Database port number.                                                   |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | private_read_ips | Array of String | Private IP address for read.                                            |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | volume           | Object          | Disk information.                                                       |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | az_code          | String          | AZ.                                                                     |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | region_code      | String          | Region where the DB instance is deployed.                               |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | created          | String          | DB instance creation time.                                              |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | updated          | String          | Update time.                                                            |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | flavor_ref       | String          | Specification code.                                                     |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | max_connections  | String          | Maximum number of connections.                                          |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | vcpus            | String          | Number of vCPUs.                                                        |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | ram              | String          | Memory size in GB.                                                      |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | need_restart     | Boolean         | Whether to reboot the DB instance for the modifications to take effect. |
      +------------------+-----------------+-------------------------------------------------------------------------+
      | priority         | String          | Failover priority.                                                      |
      +------------------+-----------------+-------------------------------------------------------------------------+

   .. _gaussdb_04_0006__table14771167122611:

   .. table:: **Table 8** volume field data structure description

      ==== ====== ================================================
      Name Type   Description
      ==== ====== ================================================
      type String Storage type. Currently, only POOL is supported.
      used String Used storage size, in GB.
      ==== ====== ================================================

   .. note::

      The values of **region_code** and **az_code** are used as examples.

-  Example normal response

   .. code-block:: text

      {
        "instance": {
          "id": "d2cda7b97a39488e8b30e3cea4066204in07",
          "name": "gauss-d616-lb07",
          "status": "FAILED",
          "project_id": "053f533ead80d5102f0cc012e8d468a4",
          "enterprise_project_id": "0",
          "type": "Cluster",
          "charge_info": {
            "charge_mode": "postPaid",
            "order_id": ""
          },
          "node_count": 2,
          "datastore": {
            "type": "GaussDB(for MySQL)",
            "version": "8.0"
          },
          "created": "2020-07-21T09:13:56+0800",
          "updated": "2020-07-21T09:27:54+0800",
          "public_ips": "",
          "private_write_ips": [
            "192.168.0.235"
          ],
          "db_user_name": "root",
          "port": "3306",
          "vpc_id": "f7ee62e2-9705-4523-ba49-a85ea1a1fa87",
          "subnet_id": "140af7bf-a9da-4dcf-8837-34199fd6d186",
          "security_group_id": "c7f69884-fe2b-4630-8114-70a11499d902",
          "backup_strategy": {
            "start_time": "00:00-00:00",
            "keep_days": "0"
          },
          "nodes": [
            {
              "id": "799a0f2fa49a4151bf9f7063c1fbba36no07",
              "name": "gauss-d616-lb07_node01",
              "type": "master",
              "status": "FAILED",
              "port": 3306,
              "private_read_ips": [
                "192.168.0.163"
              ],
              "volume": {
                "type": "POOL",
                "used": "0.0"
              },
              "az_code": "az1xahz",
              "region_code": "cn-xianhz-1",
              "flavor_id": "3169caaf-6c2f-41d5-aadd-c8fc3d83597e",
              "flavor_ref": "taurus.large.4",
              "max_connections": null,
              "vcpus": "1",
              "ram": "4",
              "need_restart": false,
              "priority": 1
            },
            {
              "id": "816459d771c444db9fa4c1d5c173cb1cno07",
              "name": "gauss-d616-lb07_node02",
              "type": "slave",
              "status": "FAILED",
              "port": 3306,
              "private_read_ips": [
                "192.168.0.160"
              ],
              "volume": {
                "type": "POOL",
                "used": "0.0"
              },
              "az_code": "az1xahz",
              "region_code": "cn-xianhz-1",
              "flavor_id": "3169caaf-6c2f-41d5-aadd-c8fc3d83597e",
              "flavor_ref": "taurus.large.4",
              "max_connections": null,
              "vcpus": "1",
              "ram": "4",
              "need_restart": false,
              "priority": 1
            }
          ],
          "time_zone": "UTC+08:00",
          "backup_used_space": 0,
          "az_mode": "single",
          "master_az_code": "az1xahz"
        }
      }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.

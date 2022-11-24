:original_name: gaussdb_04_0005.html

.. _gaussdb_04_0005:

Querying a DB Instance List
===========================

Function
--------

This API is used to query a DB instance list according to search criteria.

-  Learn how to :ref:`authorize and authenticate <gaussdb_03_0001>` this API before using it.
-  Before calling this API, obtain the required :ref:`region and endpoint <gaussdb_00_0003>`.

URI
---

-  URI format

   GET https://{*Endpoint*}/mysql/v3/{project_id}/instances?id={id}&name={name}&type={type}&datastore_type={datastore_type}&vpc_id={vpc_id}&subnet_id={subnet_id}&offset={offset}&limit={limit}

-  Example

   GET https://{*Endpoint*}/mysql/v3/97b026aa9cc4417888c14c84a1ad9860/instances?id=ed7cc6166ec24360a5ed5c5c9c2ed726in01&name=hy&type=Cluster&datastore_type=gaussdb-mysql&vpc_id=19e5d45d-70fd-4a91-87e9-b27e71c9891f&subnet_id=bd51fb45-2dcb-4296-8783-8623bfe89bb7&offset=0&limit=10

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Type            | Mandatory       | Description                                                                                                                                                                                                                             |
      +=================+=================+=================+=========================================================================================================================================================================================================================================+
      | project_id      | String          | Yes             | Project ID of a tenant in a region.                                                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                         |
      |                 |                 |                 | To obtain this value, see :ref:`Obtaining a Project ID <gaussdb_10_0004>`.                                                                                                                                                              |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id              | String          | No              | DB instance ID.                                                                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                                         |
      |                 |                 |                 | The asterisk (``*``) is reserved for the system. If the instance ID starts with an asterisk (*), the value following asterisk (*) is used for fuzzy matching. Otherwise, the instance ID is used for exact matching.                    |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name            | String          | No              | DB instance name.                                                                                                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                                                                         |
      |                 |                 |                 | The asterisk (``*``) is reserved for the system. If the instance name starts with an asterisk (*), the value following asterisk (*) is used for fuzzy matching. Otherwise, the instance name is used for exact matching.                |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type            | String          | No              | DB instance type to be queried. Currently, only the cluster type is supported.                                                                                                                                                          |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore_type  | String          | No              | Database type.                                                                                                                                                                                                                          |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id          | String          | No              | VPC ID.                                                                                                                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                                                         |
      |                 |                 |                 | -  Method 1: Log in to VPC console and view the VPC ID in the VPC details.                                                                                                                                                              |
      |                 |                 |                 | -  Method 2: See the "Querying VPCs" section in the *Virtual Private Cloud API Reference*.                                                                                                                                              |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id       | String          | No              | Network ID of the subnet.                                                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                         |
      |                 |                 |                 | -  Method 1: Log in to VPC console and click the target subnet on the **Subnets** page. You can view the network ID on the displayed page.                                                                                              |
      |                 |                 |                 | -  Method 2: See the "Querying Subnets" section under "APIs" or the "Querying Networks" section under "OpenStack Neutron APIs" in the *Virtual Private Cloud API Reference*.                                                            |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset          | Integer         | No              | Index position. If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit           | Integer         | No              | Number of records to be queried. The default value is **100**. The value cannot be a negative number. The minimum value is **1** and the maximum value is **100**.                                                                      |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
      | instances             | Array of objects      | DB instance information.                                               |
      |                       |                       |                                                                        |
      |                       |                       | For details, see :ref:`Table 3 <gaussdb_04_0005__table2058713718267>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------+
      | total_count           | Integer               | Total number of records.                                               |
      +-----------------------+-----------------------+------------------------------------------------------------------------+

   .. _gaussdb_04_0005__table2058713718267:

   .. table:: **Table 3** instances field data structure description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                        |
      +=======================+=======================+====================================================================================================================+
      | id                    | String                | DB instance ID.                                                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | DB instance name.                                                                                                  |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | status                | String                | DB instance status.                                                                                                |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | private_ips           | List<String>          | Private IP address for write. It is a blank string until an ECS is created.                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | public_ips            | List<String>          | Public IP address list.                                                                                            |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | port                  | Integer               | Database port number.                                                                                              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | type                  | String                | DB instance type. The value is **Cluster**.                                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | region                | String                | Region where the DB instance is deployed.                                                                          |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore             | Object                | Database information.                                                                                              |
      |                       |                       |                                                                                                                    |
      |                       |                       | For details, see :ref:`Table 4 <gaussdb_04_0005__table187591675262>`.                                              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | created               | String                | Creation time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      |                       |                       |                                                                                                                    |
      |                       |                       | The value is empty unless the DB instance creation is complete.                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | updated               | String                | Update time. The format is the same as that of the **created** field.                                              |
      |                       |                       |                                                                                                                    |
      |                       |                       | The value is empty unless the DB instance creation is complete.                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | db_user_name          | String                | Default username.                                                                                                  |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | vpc_id                | String                | VPC ID.                                                                                                            |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | subnet_id             | String                | Network ID of the subnet.                                                                                          |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | security_group_id     | String                | Security group ID.                                                                                                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | flavor_ref            | String                | Specification code.                                                                                                |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | flavor_info           | Object                | Specification description.                                                                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | volume                | Object                | Volume information.                                                                                                |
      |                       |                       |                                                                                                                    |
      |                       |                       | For details, see :ref:`Table 5 <gaussdb_04_0005__table14771167122611>`.                                            |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | backup_strategy       | Object                | Backup policy.                                                                                                     |
      |                       |                       |                                                                                                                    |
      |                       |                       | For details, see :ref:`Table 7 <gaussdb_04_0005__table578797132615>`.                                              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | time_zone             | String                | Time zone.                                                                                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

   .. _gaussdb_04_0005__table187591675262:

   .. table:: **Table 4** datastore field data structure description

      ======= ====== ===========
      Name    Type   Description
      ======= ====== ===========
      type    String DB engine.
      version String DB version.
      ======= ====== ===========

   .. _gaussdb_04_0005__table14771167122611:

   .. table:: **Table 5** volume field data structure description

      ==== ====== ===============
      Name Type   Description
      ==== ====== ===============
      type String Disk type.
      size String Used disk size.
      ==== ====== ===============

   .. table:: **Table 6** flavor_ref field data structure description

      ===== ====== ==================
      Name  Type   Description
      ===== ====== ==================
      vcpus String Number of vCPUs.
      ram   String Memory size in GB.
      ===== ====== ==================

   .. _gaussdb_04_0005__table578797132615:

   .. table:: **Table 7** backup_strategy field data structure description

      +------------+--------+----------------------------------------------------------------------------------------+
      | Name       | Type   | Description                                                                            |
      +============+========+========================================================================================+
      | start_time | String | Backup time window. Automated backups will be triggered during the backup time window. |
      +------------+--------+----------------------------------------------------------------------------------------+
      | keep_days  | String | Backup retention days.                                                                 |
      +------------+--------+----------------------------------------------------------------------------------------+

   .. note::

      The value of **region** is used as an example in the following response.

-  Example normal response

   .. code-block:: text

      {
          "total_count":6,
          "instances":[
              {
                  "id":"d738399de028480fabb2b8120d4e01a4in07",
                  "status":"ACTIVE",
                                  "name":"oMoS_001",
                                  "port":3306,
                                  "type":"Cluster",
                                  "private_ips": ["192.168.0.142"],
                                  "public_ips": ["10.154.219.187"],
                                  "db_user_name": "root",
                                  "region": "aaa",
                                  "datastore": {"type": "gaussdb-mysql", "version":"8.0"},
                                  "created": "2018-08-20T02:33:49+0800",
                                  "updated": "2018-08-20T02:33:50+0800",
                  "volume": {
                          "type": "POOL",
                          "used_size": 100
                  },
                                  "vpc_id": "f7ee62e2-9705-4523-ba49-a85ea1a1fa87",
                                  "subnet_id": "140af7bf-a9da-4dcf-8837-34199fd6d186",
                                  "security_group_id":"c7f69884-fe2b-4630-8114-70a11499d902",
                                  "flavor_ref":"gaussdb.mysql.c3.small.4",
                  "backup_strategy": {"start_time": "19:00-20:00", "keep_days": 7}
                  "charge_info": {
                      "charge_mode": "postPaid"
                  },
                  "enterprise_project_id": "0",
                       "time_zone": "",
              }
          ]
      }

Status Code
-----------

For details, see :ref:`Status Codes <gaussdb_10_0002>`.

Error Code
----------

For details, see :ref:`Error Codes <gaussdb_10_0003>`.

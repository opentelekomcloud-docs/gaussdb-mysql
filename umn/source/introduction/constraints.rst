:original_name: gaussdb_01_0008.html

.. _gaussdb_01_0008:

Constraints
===========

:ref:`Table 1 <gaussdb_01_0008__en-us_topic_0171122409_table60364850123535>` shows the constraints designed to ensure the stability and security of GaussDB(for MySQL).

.. _gaussdb_01_0008__en-us_topic_0171122409_table60364850123535:

.. table:: **Table 1** Function constraints

   +------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Function                           | Constraint                                                                                                                                                                                   |
   +====================================+==============================================================================================================================================================================================+
   | GaussDB(for MySQL) access          | -  If GaussDB(for MySQL) instances are not bound with EIPs, the instances must be in the same VPC subnet as the ECSs associated with these instances.                                        |
   |                                    |                                                                                                                                                                                              |
   |                                    | -  Security group rules must be added to allow ECSs to access GaussDB(for MySQL) instances.                                                                                                  |
   |                                    |                                                                                                                                                                                              |
   |                                    |    By default, a GaussDB(for MySQL) instance cannot be accessed by an ECS in a different security group. To allow it, you must add an inbound rule to the GaussDB(for MySQL) security group. |
   |                                    |                                                                                                                                                                                              |
   |                                    | -  The default GaussDB(for MySQL) instance port is **3306**. You can change it if you want to access GaussDB(for MySQL) through another port.                                                |
   +------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deployment                         | ECSs in which GaussDB(for MySQL) instances are deployed are not visible to users. You can access GaussDB(for MySQL) instances only over an IP address and a port.                            |
   +------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Administrator root permission      | Only the **root** user permissions are available on the instance creation page.                                                                                                              |
   +------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database parameter modification    | Most parameters can be modified on the GaussDB(for MySQL) console.                                                                                                                           |
   +------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data migration                     | The mysqldump tool is used to migrate data to GaussDB(for MySQL).                                                                                                                            |
   +------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | GaussDB(for MySQL) instance reboot | GaussDB(for MySQL) instances cannot be rebooted through commands. They must be rebooted on the GaussDB(for MySQL) console.                                                                   |
   +------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | GaussDB(for MySQL) backup files    | GaussDB(for MySQL) backup files are stored in OBS buckets and are not visible to users.                                                                                                      |
   +------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

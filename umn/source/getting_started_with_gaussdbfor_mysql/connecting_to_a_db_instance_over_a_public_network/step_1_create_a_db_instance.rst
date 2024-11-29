:original_name: gaussdb_02_0012.html

.. _gaussdb_02_0012:

Step 1: Create a DB Instance
============================

Scenarios
---------

This section describes how to create a DB instance on the management console.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Databases**, click **GaussDB(for MySQL)**.
#. On the **Instances** page, click **Create DB Instance**.
#. On the displayed page, configure parameters about the DB instance specifications. Then, click **Create Now**.

   .. table:: **Table 1** Basic information

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================================================================+
      | Region                            | A region where the tenant is located. You can change it on the creation page, or go back to the **Instances** page and change it in the upper left corner.                                                                                         |
      |                                   |                                                                                                                                                                                                                                                    |
      |                                   | .. important::                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                    |
      |                                   |    NOTICE:                                                                                                                                                                                                                                         |
      |                                   |    Products in different regions cannot communicate with each other over a private network and you cannot change the region of a DB instance after creating the instance.                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Instance Name                  | A name starts with a letter and consists of 4 to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Engine                         | GaussDB(for MySQL)                                                                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Engine Version                 | MySQL 8.0                                                                                                                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ Type                           | An AZ is a physical region where resources use independent power supply and networks. AZs are physically isolated but interconnected through an internal network.                                                                                  |
      |                                   |                                                                                                                                                                                                                                                    |
      |                                   | -  **Single AZ**: The primary node and read replicas are deployed in the same AZ.                                                                                                                                                                  |
      |                                   | -  **Multi-AZ**: The primary node and read replicas are deployed in different AZs to ensure high reliability.                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Time Zone                         | You need to select a time zone for your DB instances based on the longitude and latitude of the region hosting your DB instance. The time zone can be selected during DB instance creation and cannot be changed after the DB instance is created. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 2** Specifications and storage

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================+
      | Instance Specifications           | Refers to the CPU and memory of a DB instance. Different instance specifications support different numbers of database connections and maximum IOPS.                    |
      |                                   |                                                                                                                                                                         |
      |                                   | After a DB instance is created, you can change its CPU and memory. For details, see :ref:`Changing vCPUs and Memory of an Instance <gaussdb_03_0092>`.                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Nodes                             | GaussDB(for MySQL) supports one primary node and up to 15 read replicas. When you are creating a DB instance, a maximum of nine read replicas can be created at a time. |
      |                                   |                                                                                                                                                                         |
      |                                   | After the DB instance is created, you can also create read replicas based on service requirements by referring to :ref:`Creating a Read Replica <gaussdb_03_0111>`.     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage                           | Contains the system overhead required for inode, reserved block, and database operation. You do not need to specify storage space when creating a DB instance.          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 3** Network

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================================================================================================================================================================================================================================+
      | VPC                               | A dedicated virtual network in which your DB instances are located. It isolates networks for different services. You can select an existing VPC or create a VPC. For details on how to create a VPC, see "Creating a VPC" in the *Virtual Private Cloud User Guide*.                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                   |
      |                                   | If no VPC is available, GaussDB(for MySQL) allocates a VPC to you by default.                                                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subnet                            | Improves network security by providing dedicated network resources that are logically isolated from other networks. Subnets are only valid for a given AZ. The Dynamic Host Configuration Protocol (DHCP) function must be enabled by default for subnets in which you plan to create DB instances. It cannot be disabled. You can select or search for a desired subnet from the drop-down list. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                   |
      |                                   | A private IP address is automatically assigned when you create an instance. You can also enter a free private IP address in the subnet CIDR block.                                                                                                                                                                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Security Group                    | Enhances security by controlling access to GaussDB(for MySQL) from other services. You need to add rules to a security group that enable you to connect to your DB instance.                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                   |
      |                                   | If no security group is available or has been created, GaussDB(for MySQL) allocates a security group to you by default.                                                                                                                                                                                                                                                                           |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 4** Database configuration

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================================+
      | Administrator                     | The default login name for the database is **root**.                                                                                                                                                                                                                                                   |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Administrator Password            | Must consist of 8 to 32 characters and contain at least three of the following: uppercase letters, lowercase letters, digits, and special characters ``~!@#%^*-_=+?``. Enter a strong password and periodically change it to improve security, preventing security risks such as brute force cracking. |
      |                                   |                                                                                                                                                                                                                                                                                                        |
      |                                   | Keep this password secure. The system cannot retrieve it.                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                        |
      |                                   | After a DB instance is created, you can reset this password. For details, see :ref:`Resetting the Administrator Password <gaussdb_03_0051>`.                                                                                                                                                           |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Confirm Password                  | Must be the same as **Administrator Password**.                                                                                                                                                                                                                                                        |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 5** Parameter template

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                |
      +===================================+============================================================================================================================================================================+
      | Parameter Template                | Contains engine configuration values that can be applied to one or more DB instances. You can modify the instance parameters as required after the DB instance is created. |
      |                                   |                                                                                                                                                                            |
      |                                   | For details, see :ref:`Parameter Template Management <gaussdb_08_0011>`.                                                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 6** Batch instance creation

      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                           |
      +===========+=======================================================================================================================================================================================================================================================================================================================================================================================================+
      | Quantity  | You can create instances in batches. The default value is **1**. The value ranges from **1** to **10**. If you create multiple instances at a time, a hyphen (-) followed by a number with four digits will be appended to the instance name, starting with -0001. For example, if you enter **instance**, the first instance will be named as instance-0001, the second as instance-0002, and so on. |
      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Confirm your specifications.

   -  If you need to modify your settings, click **Previous**.
   -  If you do not need to modify your settings, click **Submit**.

#. To view and manage DB instances, go to the **Instances** page.

   -  During the creation process, the DB instance status is **Creating**. When the status of the created instance is **Available**, the DB instance can be used.

   -  An automated backup policy is enabled by default. After the DB instance is created, you can modify this policy as required. An automated full backup is immediately triggered after a DB instance is created.

   -  The default database port is **3306**. After a DB instance is created, you can change its port.

      For details, see :ref:`Changing a Database Port <gaussdb_03_0012>`.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png

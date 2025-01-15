:original_name: gaussdb_03_0007.html

.. _gaussdb_03_0007:

Migrating Data to GaussDB(for MySQL) Using mysqldump
====================================================

Preparing for Data Migration
----------------------------

GaussDB(for MySQL) supports public accessibility. You can access GaussDB(for MySQL) through an ECS or EIP.

#. Prepare an ECS in the same VPC subnet as GaussDB(for MySQL) or prepare a device for accessing GaussDB(for MySQL) over a public network.

   -  To connect to a DB instance through an ECS, you must first create an ECS.

      For details on how to create and log in to an ECS, see descriptions about creating an ECS and logging in an ECS in the *Elastic Cloud Server User Guide*.

   -  To connect to a DB instance through an EIP, you must:

      a. Bind the EIP to the DB instance. For details, see :ref:`Binding an EIP <gaussdb_03_0011__en-us_topic_0171122283_section3199593620428>`.
      b. Ensure that the local device can access the EIP that has been bound to the DB instance.

#. Install the MySQL client on the prepared ECS or device.

   For details, see :ref:`How Can I Install the MySQL Client? <gaussdb_faq_0011>`

   .. note::

      The version of the GaussDB(for MySQL) client must be the same as or later than that of the GaussDB(for MySQL) server. The MySQL database or client provides the mysqldump and mysql tools by default.

Exporting Data
--------------

Before migrating data to GaussDB(for MySQL), you need to export data first.

.. important::

   -  The export tool must match the DB engine version.
   -  Database migration is performed offline. Before the migration, you must stop any applications using the source database.

#. Log in to the prepared ECS or device that can access GaussDB(for MySQL) DB instances.

#. .. _gaussdb_03_0007__en-us_topic_0171122750_li16251172911136:

   Use the mysqldump tool to export metadata into an SQL file.

   .. important::

      MySQL databases are required for GaussDB(for MySQL) management. When exporting metadata, do not specify **--all-database**. Otherwise, the databases will be unavailable.

   **mysqldump** **--databases** <*DB_NAME*> **--single-transaction --order-by-primary --hex-blob --no-data --routines --events --set-gtid-purged=OFF** -u <*DB_USER*> **-p -h** <*DB_ADDRESS*> **-P** <*DB_PORT*> **\|sed -e 's/DEFINER[ ]*=[ ]*[^*]*\\*/\\*/' -e 's/DEFINER[ ]*=.*FUNCTION/FUNCTION/' -e 's/DEFINER[ ]*=.*PROCEDURE/PROCEDURE/' -e 's/DEFINER[ ]*=.*TRIGGER/TRIGGER/' -e 's/DEFINER[ ]*=.*EVENT/EVENT/' >** *<BACKUP_FILE>*

   -  **DB_NAME** indicates the name of the database to be migrated.
   -  **DB_USER** indicates the database username.
   -  **DB_ADDRESS** indicates the database address.
   -  **DB_PORT** indicates the database port.
   -  **BACKUP_FILE** indicates the name of the file to which the data will be exported.

   Enter the database password as prompted.

   Example:

   **mysqldump --databases gaussdb --single-transaction --order-by-primary --hex-blob --no-data --routines --events --set-gtid-purged=OFF -u root -p -h 192.168.151.18 -P 3306 \|sed -e 's/DEFINER[ ]*=[ ]*[^*]*\\*/\\*/' -e 's/DEFINER[ ]*=.*FUNCTION/FUNCTION/' -e 's/DEFINER[ ]*=.*PROCEDURE/PROCEDURE/' -e 's/DEFINER[ ]*=.*TRIGGER/TRIGGER/' -e 's/DEFINER[ ]*=.*EVENT/EVENT/' > dump-defs.sql**

   **Enter password:**

   After this command is executed, the **dump-defs.sql** file will be generated.

#. Use the mysqldump tool to export data into an SQL file.

   .. important::

      MySQL databases are required for GaussDB(for MySQL) management. When exporting metadata, do not specify **--all-database**. Otherwise, the databases will be unavailable.

   **mysqldump --databases** <*DB_NAME*> **--single-transaction --hex-blob --set-gtid-purged=OFF --no-create-info --skip-triggers** **-u** <*DB_USER*> **-p** **-h** <*DB_ADDRESS*> **-P** <*DB_PORT*> **-r** <*BACKUP_FILE*>

   For details on the parameters in the preceding command, see :ref:`2 <gaussdb_03_0007__en-us_topic_0171122750_li16251172911136>`.

   Enter the database password as prompted.

   Example:

   **mysqldump --databases gaussdb --single-transaction --hex-blob --set-gtid-purged=OFF --no-create-info --skip-triggers -u root -p -h 192.168.151.18 -P 3306 -r dump-data.sql**

   After this command is executed, the **dump-data.sql** file will be generated.

Importing Data
--------------

You can use a client to connect to a GaussDB(for MySQL) DB instance through an ECS or a device and then import the exported SQL file into that DB instance.

.. important::

   If the source database contains triggers, storage processes, functions, or event invocation, you must set **log_bin_trust_function_creators** to **ON** for the destination database before importing data.

#. Import metadata into GaussDB(for MySQL).

   Use the MySQL tool to connect to the GaussDB(for MySQL) DB instance, enter the password, and run the following command to import metadata:

   **mysql -f -h** *<DB_ADDRESS>* **-P** <*DB_PORT*> **-u** root **-p <** *<BACKUP_DIR>*\ **/dump-defs.sql**

   -  **DB_ADDRESS** indicates the IP address of the GaussDB(for MySQL) DB instance.
   -  **DB_PORT** indicates the GaussDB(for MySQL) DB instance port.
   -  **BACKUP_DIR** indicates the directory where **dump-defs.sql** is stored.

   Example:

   **mysql -f -h 172.16.66.198 -P 3306 -u root -p < dump-defs.sql**

   **Enter password:**

#. Import data into GaussDB(for MySQL).

   **mysql -f -h** *<DB_ADDRESS>* **-P** <*DB_PORT*> **-u** root **-p** **<** *<BACKUP_DIR>*\ **/dump-data.sql**

   -  **DB_ADDRESS** indicates the IP address of the GaussDB(for MySQL) DB instance.
   -  **DB_PORT** indicates the GaussDB(for MySQL) DB instance port.
   -  **BACKUP_DIR** indicates the directory where **dump-data.sql** is stored.

   Example:

   **mysql -f -h 172.16.66.198 -P 3306 -u root -p < dump-data.sql**

   **Enter password:**

#. View the import result.

   **mysql> show databases;**

   In this example, the database named **my_db** has been imported.

   .. code-block::

      mysql> show databases;
      +--------------------+
      | Database           |
      +--------------------+
      | information_schema |
      | my_db              |
      | mysql              |
      | performance_schema |
      +--------------------+
      4 rows in set (0.00 sec)

:original_name: gaussdb_03_0114.html

.. _gaussdb_03_0114:

Deleting a Read Replica
=======================

Scenarios
---------

You can manually delete read replicas on the **Instance Management** page.

.. important::

   Deleted read replicas cannot be restored. Exercise caution when performing this operation.

Constraints
-----------

-  You can delete read replicas only when the DB instance has two or more than two read replicas. A GaussDB(for MySQL) DB instance must have at least one read replica.
-  DB instances cannot be deleted when operations are being performed on them. They can be deleted only after the operations are completed.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **GaussDB**.

#. On the **Instance Management** page, click the target DB instance.

#. At the bottom of the **Basic Information** page, locate the read replicas to be deleted and choose **More** > **Delete** in the **Operation** column.

   For high availability reasons, the system reserves an available read replica. The read replica cannot be deleted until the associated DB instance is deleted.

#. In the displayed dialog box, click **Yes**. Refresh the **Instance Management** page later to check that the deletion is successful.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png

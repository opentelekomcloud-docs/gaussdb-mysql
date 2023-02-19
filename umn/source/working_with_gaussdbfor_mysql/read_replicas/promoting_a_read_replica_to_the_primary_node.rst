:original_name: gaussdb_03_0113.html

.. _gaussdb_03_0113:

Promoting a Read Replica to the Primary Node
============================================

A GaussDB(for MySQL) DB instance consists of a primary node and multiple read replicas. In addition to :ref:`automatic failover <gaussdb_03_0113__section1762033653214>` scenarios, you can perform a :ref:`manual switchover <gaussdb_03_0113__section133052410322>` to promote a read replica to the new primary node.

.. _gaussdb_03_0113__section133052410322:

Manual Switchover
-----------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **GaussDB**.
#. On the **Instance Management** page, click the target DB instance.
#. At the bottom of the **Basic Information** page, locate the read replica to be promoted and click **Promote to Primary** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.

   -  During the manual switchover, an intermittent disconnection may occur for about 30 seconds. Ensure that your applications support automatic reconnection.
   -  During the manual switchover, the instance status is **Promoting to primary** and this process takes several seconds or minutes.
   -  After the switchover is complete, the node running status changes to **Available**. The node types of the original primary node and read replica have been exchanged.

      .. important::

         Services may be intermittently interrupted for several seconds or minutes when the read replica is promoted to the primary node.

.. _gaussdb_03_0113__section1762033653214:

Automatic Failover
------------------

GaussDB(for MySQL) uses an active-active high availability architecture and can automatically fail over to a new primary node that is automatically selected by the system.

Each read replica has a failover priority that determines the order in which it is promoted when recovering from a primary node failure.

-  Priorities range from 1 for the first priority to 16 for the last priority.
-  If two or more read replicas share the same priority, they have a same probability of being promoted to the new primary node.

GaussDB(for MySQL) selects a read replica and promotes it to the new primary node as follows:

#. Find all read replicas that are available for a promotion.
#. Fine one or more read replicas with the highest priority.
#. Promote an arbitrary read replica with the highest priority. If the promotion fails due to network faults or abnormal replication status, GaussDB(for MySQL) attempts to promote another read replica by priority until the promotion is successful.

.. |image1| image:: /_static/images/en-us_image_0000001400783488.png

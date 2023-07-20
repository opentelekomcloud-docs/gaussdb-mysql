:original_name: gaussdb_11_0031.html

.. _gaussdb_11_0031:

Changing the Read/Write Splitting Address
=========================================

Scenarios
---------

After read/write splitting is enabled, you can change the read/write splitting address.

Precautions
-----------

Changing the read/write splitting address will interrupt database connections and services. Therefore, change the read/write splitting address during off-peak hours or when services are stopped.

Constraints
-----------

The new IP address is not in use and must be in the same subnet as the GaussDB(for MySQL) instance.

Procedure
---------

You can change the read/write splitting address for instances with read/write splitting enabled.

#. Log in to the console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Under **Database**, click **GaussDB**. In the navigation pane on the left, click **GaussDB(for MySQL)**.

#. On the **Instances** page, click the instance name to go to the **Basic Information** page.

#. In the navigation pane on the left, click **Database Proxy**.

   Click the desired proxy instance name. In the **DB Instance Information** area, click **Change** next to the **Read/Write Splitting Address** field.

#. In the displayed dialog box, enter a new IP address and click **OK**.

   In-use IP addresses cannot be used.

.. |image1| image:: /_static/images/en-us_image_0000001400391461.png

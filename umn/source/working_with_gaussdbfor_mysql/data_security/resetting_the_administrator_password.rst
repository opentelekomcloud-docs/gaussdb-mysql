:original_name: gaussdb_03_0051.html

.. _gaussdb_03_0051:

Resetting the Administrator Password
====================================

Scenarios
---------

You can reset the administrator password of a DB instance.

You can also reset the password of your database account when using GaussDB(for MySQL).

You cannot reset the administrator password under the following circumstances:

-  The database port is being changed.
-  The instance status is **Creating**, **Restoring**, **Rebooting**, **Changing port**, **Changing instance class**, **Promoting to primary**, or **Abnormal**.

Precautions
-----------

-  If you change the administrator password of a DB instance, the passwords of the read replicas associated with the DB instance are also changed accordingly.
-  The length of time it takes for the new password to take effect depends on the amount of service data currently being processed by the primary node.
-  To prevent brute force cracking and ensure system security, change your password periodically, such as every three or six months.

Method 1
--------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **GaussDB**.

#. On the **Instances** page, locate the target DB instance and choose **More** > **Reset Password** in the **Operation** column.

#. Enter a new password and confirm the password.

   .. important::

      Keep this password secure. The system cannot retrieve it.

   The new password must consist of 8 to 32 characters and contain at least three of the following: uppercase letters, lowercase letters, digits, and special characters (``~!@#%^*-_=+?``). Enter a strong password and periodically change it to improve security, preventing security risks such as brute force cracking.

   -  To submit the new password, click **OK**.
   -  To cancel the reset, click **Cancel**.

Method 2
--------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **GaussDB**.

#. On the **Instances** page, click the target DB instance. The **Basic Information** page is displayed.

#. In the **DB Instance Information** area, click **Reset Password** in the **Administrator** field. In the displayed dialog box, enter a new password and confirm the password.

   .. important::

      Keep this password secure. The system cannot retrieve it.

   The new password must consist of 8 to 32 characters and contain at least three of the following: uppercase letters, lowercase letters, digits, and special characters (``~!@#%^*-_=+?``). Enter a strong password and periodically change it to improve security, preventing security risks such as brute force cracking.

   -  To submit the new password, click **OK**.
   -  To cancel the reset, click **Cancel**.

.. |image1| image:: /_static/images/en-us_image_0000001352219100.png
.. |image2| image:: /_static/images/en-us_image_0000001352219100.png

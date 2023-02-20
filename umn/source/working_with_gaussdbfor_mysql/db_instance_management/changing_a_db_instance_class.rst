:original_name: gaussdb_03_0092.html

.. _gaussdb_03_0092:

Changing a DB Instance Class
============================

Scenarios
---------

You can change the CPU or memory (instance class) of a DB instance as required. If the status of a DB instance changes from **Changing instance class** to **Available**, the change is successful.

-  A DB instance cannot be deleted while its instance class is being changed.
-  The instance class can be changed only at the DB instance level. The instance class of the primary node or read replicas cannot be changed separately for a GaussDB(for MySQL) DB instance.

.. important::

   -  Changing the DB instance class will cause the instance to reboot. To prevent service interruptions, change the instance class during off-peak hours.
   -  To prevent traffic congestion during peak hours, you are advised to reboot the DB instance during off-peak hours.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **GaussDB**.

#. You can change the instance class in either of the following ways:

   -  On the **Instance Management** page, locate the target DB instance and choose **More** > **Change Instance Class** in the **Operation** column.
   -  Click the target DB instance to go to the **Basic Information** page. In the **DB Instance Information** area, click **Change** in the **Instance Class** field.

#. On the displayed page, specify the new instance class and scheduled time, and click **Next**.

   Choose either of the following scheduled time:

   -  **Upon submission**: The instance class will be changed upon the task submission.
   -  **In maintenance window**: The instance class will be changed in your specified maintenance window.

#. On the displayed page, confirm the instance class.

   -  If you need to modify your settings, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit**.

#. View the DB instance class change result.

   Changing the instance class takes 5-15 minutes. During this period, the status of the DB instance on the **Instance Management** page is **Changing instance class**. After a few minutes, click the instance and view the instance class on the displayed **Basic Information** page to check that the change is successful.

   .. important::

      After the DB instance class is changed, the system will change the values of the following parameters accordingly: **innodb_buffer_pool_size**, **innodb_log_buffer_size**, **max_connections**, **innodb_buffer_pool_instances**, **innodb_page_cleaners**, **innodb_parallel_read_threads**, **innodb_read_io_threads**, **innodb_write_io_threads**, **threadpool_size** and **query_cache_size**.

.. |image1| image:: /_static/images/en-us_image_0000001400783488.png
